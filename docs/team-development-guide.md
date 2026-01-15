# Team Development Guide: Working Together on Shared Robots

This guide explains how teams can develop independently on shared hardware without stepping on each other's configurations.

## The Core Problem

Multiple engineers working on the same robot will create configuration conflicts if everyone edits the same machine config directly. Viam's **fragments** solve this.

## What Are Fragments?

Fragments are reusable configuration blocks. Instead of one monolithic config per robot, you compose a machine from multiple fragments:

```
Machine: research-robot-001
├── Fragment: base-drivetrain (motors, wheels, encoders)
├── Fragment: vision-pipeline (camera, detector, classifier)
├── Fragment: arm-control (arm, gripper, motion service)
└── Machine-specific overwrites (USB ports, calibration values)
```

Each team owns their fragment. No conflicts.

## How Teams Avoid Conflicts

### Strategy 1: Fragment Ownership

Each team owns specific fragments:

| Team | Fragment | Contains |
|------|----------|----------|
| Navigation | `nav-system-v1` | SLAM service, motion planning, obstacle detection |
| Vision | `vision-pipeline-v1` | Camera, ML models, vision service |
| Manipulation | `arm-control-v1` | Arm, gripper, poses |
| Data | `data-capture-v1` | Data management, sync config |

Teams edit only their fragments. When applied to a machine, all fragments combine.

### Strategy 2: Prefixes for Namespace Isolation

When multiple fragments are on the same machine, use prefixes to avoid naming collisions:

```json
{
  "fragments": [
    {
      "id": "vision-pipeline-fragment-id",
      "prefix": "vision"
    },
    {
      "id": "arm-control-fragment-id",
      "prefix": "arm"
    }
  ]
}
```

Result:
- Vision team's `camera` becomes `vision-camera`
- Arm team's `camera` (if they have one) becomes `arm-camera`
- No collision

**Rule:** Always use prefixes when combining fragments from different teams.

### Strategy 3: Overwrites for Machine-Specific Differences

Don't modify a shared fragment for one machine's quirks. Use **overwrites** instead:

```json
{
  "fragment_mods": [
    {
      "fragment_id": "base-drivetrain-id",
      "mods": [
        {
          "$set": {
            "components.left_motor.attributes.pins.a": 15,
            "components.right_motor.attributes.max_rpm": 1500
          }
        }
      ]
    }
  ]
}
```

Benefits:
- Fragment stays clean for all machines
- Machine-specific tweaks don't affect others
- When fragment updates, overwrites persist

### Strategy 4: Variables for Common Variations

Use template variables for things that vary predictably (USB paths, IP addresses):

In fragment definition:
```json
{
  "name": "main-camera",
  "attributes": {
    "video_path": {
      "$variable": { "name": "camera_usb_path" }
    }
  }
}
```

When adding to machine:
```json
{
  "camera_usb_path": "/dev/video0"
}
```

Different machine:
```json
{
  "camera_usb_path": "/dev/video2"
}
```

Same fragment, different configs. No overwrites needed.

## Recommended Team Structure

### Fragment Organization

```
Organization: Build on Viam

Fragments (owned centrally):
├── base-hardware-v1        # Common board, power config
├── camera-standard-v1      # Standard camera setup
└── data-capture-standard-v1  # Common data sync config

Project-Specific Fragments:
├── chess-vision-v1         # Chess piece detection
├── chess-arm-v1            # Chess arm movements
├── vino-pour-v1            # Wine pouring logic
├── greenhouse-sensors-v1   # Environmental sensors
└── cleaning-nav-v1         # Office navigation
```

### Machine Organization

```
Locations:
├── Chess Project
│   ├── chess-dev     (development - latest fragments)
│   ├── chess-qa      (testing - beta tag)
│   └── chess-prod    (demo - stable tag)
├── Vino Project
│   ├── vino-dev
│   └── vino-prod
└── Shared Hardware
    └── dev-arm-station  (shared across projects)
```

### Role Assignments

| Role | Can Do | Assign To |
|------|--------|-----------|
| Org Owner | Create/edit fragments | Project leads |
| Location Owner | Apply fragments, create overwrites | Team members |
| Machine Operator | Control robots, view logs | Everyone |

## Development Workflow

### Daily Development

1. **Work on your team's fragment** - Edit freely, changes auto-version
2. **Test on dev machine** - Dev machines use `latest` version
3. **Don't touch other teams' fragments** - Use overwrites if you need to adjust their resources temporarily

### Releasing Updates

```
1. Make changes to fragment (new version created automatically)
2. Test on dev machine (uses latest)
3. Tag as "beta" when ready for broader testing
4. Test on QA machines (pinned to beta)
5. Tag as "stable" when validated
6. Update production machines to stable tag
```

### Handling Shared Hardware

When multiple teams need the same robot:

**Option A: Time-based sharing**
- Team A uses robot 9am-12pm
- Team B uses robot 1pm-5pm
- Each team has their own machine config pointing to same hardware

**Option B: Fragment composition**
- Both teams add their fragments to same machine
- Use prefixes to avoid collisions
- Coordinate on shared resources (e.g., one camera)

**Option C: Separate machines for separate concerns**
- Team A configures `robot-vision-dev` (only their components)
- Team B configures `robot-arm-dev` (only their components)
- Integration testing uses `robot-full-dev` (all fragments)

## Rules for Build on Viam Projects

### Do

- Create fragments for your project's subsystems
- Use prefixes when adding fragments to shared machines
- Use overwrites for machine-specific adjustments
- Use variables for USB paths, IP addresses, credentials
- Test on dev machines before tagging stable
- Document what your fragment configures

### Don't

- Edit another team's fragment without asking
- Hardcode machine-specific values in fragments
- Skip the dev → beta → stable progression
- Apply fragments without prefixes on shared hardware
- Modify machine configs directly when a fragment should change

## Example: Two Teams on One Robot

**Scenario:** Vision team and Arm team both need `research-robot-001`

**Vision team creates:** `vision-pipeline-v1`
```json
{
  "components": [
    { "name": "camera", "type": "camera", ... },
    { "name": "detector", "type": "vision", ... }
  ]
}
```

**Arm team creates:** `arm-control-v1`
```json
{
  "components": [
    { "name": "arm", "type": "arm", ... },
    { "name": "gripper", "type": "gripper", ... }
  ]
}
```

**Machine config for `research-robot-001`:**
```json
{
  "fragments": [
    { "id": "vision-pipeline-v1-id", "prefix": "vis" },
    { "id": "arm-control-v1-id", "prefix": "manip" }
  ]
}
```

**Result on machine:**
- `vis-camera`
- `vis-detector`
- `manip-arm`
- `manip-gripper`

Both teams work independently. No conflicts.

## Quick Reference

| I want to... | Use... |
|--------------|--------|
| Share config across machines | Fragment |
| Avoid naming collisions | Prefix |
| Adjust one machine differently | Overwrite (`fragment_mods`) |
| Handle varying USB paths/IPs | Variables (`$variable`) |
| Control who edits what | Locations + RBAC |
| Safely roll out updates | Version tags (dev → beta → stable) |

## Troubleshooting

**"Component name already exists"**
- Add a prefix to your fragment

**"My changes aren't showing up"**
- Check if machine is pinned to old version
- Check if overwrites are reverting your changes

**"Fragment update broke other machines"**
- Roll back to previous version tag
- Test on dev machine first next time

**"I need to change another team's fragment"**
- Talk to them first
- Use overwrites for temporary/machine-specific changes
- Request they add a variable if it's a common need
