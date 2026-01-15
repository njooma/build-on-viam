# Project Assessment Criteria

This document defines the criteria for evaluating projects proposed for the Build on Viam program. Criteria are derived from Viam's platform capabilities, the robotics application lifecycle, and the program's goals.

## Program Goals (for reference)

1. **Team enablement** - Engineers gain hands-on platform expertise
2. **Individual & team ownership** - Engineers feel ownership over platform quality
3. **Platform quality** - Surface and fix issues through real usage

## Assessment Framework

Projects are evaluated across six dimensions, each scored 1-5.

---

## 1. Platform Capability Coverage

**Question:** Does this project demonstrate capabilities that differentiate Viam?

### Tier 1: Core Differentiators (High Value)

Projects should exercise at least 2-3 of these:

| Capability | What It Proves |
|------------|----------------|
| **Remote Development** | Code on laptop, run on device over network (no SSH, no deploy step) |
| **Hardware Abstraction** | Same code works across different hardware vendors |
| **Data Capture & Sync** | Edge-to-cloud data pipeline with offline buffering |
| **Fragments** | Reusable configuration blocks that enable 1→many scaling |
| **Fleet Management** | Provisioning, monitoring, OTA updates across multiple machines |
| **Module Registry** | Extend platform with custom components, share via registry |

### Tier 2: Platform Capabilities (Medium Value)

| Capability | What It Proves |
|------------|----------------|
| Motion planning | Path planning, inverse kinematics, collision avoidance |
| ML inference | Deploy and run models (TensorFlow, PyTorch, ONNX) |
| SLAM / Navigation | Mapping, localization, autonomous navigation |
| Computer vision | Detection, classification, segmentation |
| Sensor fusion | Combine data from multiple sensors |
| Services (vision, motion, etc.) | Use built-in higher-level services |

### Tier 3: Basic Usage (Lower Value)

| Capability | Notes |
|------------|-------|
| Single component control | Motors, servos, sensors - necessary but not differentiating |
| Basic camera streaming | Table stakes |
| Simple sensor reading | Minimal platform exercise |

**Scoring:**
- 5: Exercises 3+ Tier 1 capabilities
- 4: Exercises 2 Tier 1 capabilities
- 3: Exercises 1 Tier 1 + multiple Tier 2
- 2: Exercises Tier 2 only
- 1: Exercises Tier 3 only

---

## 2. Lifecycle Stage Coverage

**Question:** Does this project expose engineers to challenges beyond prototyping?

Viam's value compounds across the robotics application lifecycle:

| Stage | Timeline | Problems | Viam Value |
|-------|----------|----------|------------|
| **1. Prototype** | Weeks | Get hardware working, write control logic | Hardware drivers, remote dev |
| **2. First Deployment** | 1-3 months | Real-world validation, field config, connectivity | Remote access, calibration |
| **3. Multiple Units** | 3-6 months | Configuration variance, per-machine differences | Fragments, config management |
| **4. Fleet at Scale** | 6+ months | Monitoring, updates, rollback | OTA, fleet dashboards |
| **5. Maintenance** | Ongoing | Debugging, logs, model updates | Remote diagnostics, data pipelines |

**Ideal projects:**
- MVP demonstrates Stage 1-2
- Backlog items push into Stage 3-4
- Stretch goals touch Stage 5

**Scoring:**
- 5: Backlog explicitly addresses Stages 3-5 (fleet, scale, maintenance)
- 4: MVP reaches Stage 2, backlog addresses Stage 3
- 3: MVP reaches Stage 2 (real deployment scenario)
- 2: MVP is Stage 1 only, but backlog extends further
- 1: Stays entirely in Stage 1 (bench prototype only)

---

## 3. Problem-Platform Fit

**Question:** Does this project address problems Viam is designed to solve?

### Problems Viam Solves Well (Prioritize These)

**Hardware & Integration:**
- Connecting diverse hardware (cameras, motors, sensors, arms)
- Abstracting vendor differences
- Adding new hardware types via modules

**Development Experience:**
- Remote access to robots (NAT traversal, firewalls)
- Live sensor feeds during development
- Configuration-driven setup (vs. code changes)

**Data & ML:**
- Capturing sensor data at the edge
- Syncing data to cloud with offline resilience
- Deploying ML models to edge devices

**Scale & Operations:**
- Managing configuration across multiple robots
- Pushing updates without physical access
- Monitoring fleet health

### Problems Viam Partially Solves (Acceptable)

- Complex motion planning (supported but not all scenarios)
- Real-time control (WebRTC adds latency)
- Simulation (emerging, not fully integrated)

### Problems Viam Doesn't Solve (Avoid as Primary Focus)

- Low-level motor control algorithms
- Custom RTOS or real-time guarantees
- Hardware design or manufacturing
- Domain-specific business logic (Viam is infrastructure)

**Scoring:**
- 5: Primary problems are all in "solves well" category
- 4: Primary problems mostly in "solves well", some "partial"
- 3: Mix of "solves well" and "partial"
- 2: Primarily "partial" problems
- 1: Problems outside Viam's scope

---

## 4. Feasibility & Scope

**Question:** Can this project achieve meaningful results within program constraints?

### Hackathon MVP (3 days)

Must be achievable:
- Working demo that shows core functionality
- Uses available hardware or simulation
- Team of 2-4 engineers can complete it

### Hardware Considerations

| Factor | Preferred | Acceptable | Problematic |
|--------|-----------|------------|-------------|
| Availability | In-office stock | Orderable, <$500 | Custom, long lead time |
| Setup complexity | Plug and play | Some assembly | Significant integration |
| Remote access | Simulation available | Can be shared | Physical presence required |

### Technical Complexity

| Factor | Preferred | Acceptable | Problematic |
|--------|-----------|------------|-------------|
| Dependencies | Viam SDK + standard libs | Common ML frameworks | Obscure libraries |
| Domain knowledge | General robotics | Some specialization | Deep expertise required |
| Integration points | Viam components | Well-documented APIs | Reverse engineering |

**Scoring:**
- 5: MVP clearly achievable, hardware available, well-understood domain
- 4: MVP achievable with some risk, hardware obtainable
- 3: MVP achievable but tight, some hardware or complexity concerns
- 2: MVP at risk, significant unknowns
- 1: MVP unlikely in timeframe, major blockers

---

## 5. Learning & Quality Impact

**Question:** Will this project achieve program goals?

### Engineer Learning

Does the project teach engineers about:
- [ ] Viam's architecture and component model
- [ ] Configuration and fragments
- [ ] SDK usage patterns (Python, Go, TypeScript)
- [ ] Data management and ML deployment
- [ ] Fleet operations and monitoring
- [ ] Module development and registry

### Platform Quality

Will building this project likely:
- [ ] Surface bugs in core platform
- [ ] Identify documentation gaps
- [ ] Reveal UX friction points
- [ ] Test edge cases in components/services
- [ ] Exercise less-used platform features

### Visibility & Engagement

- [ ] Makes a compelling demo
- [ ] Engineers will want to work on it
- [ ] Can be shown to customers/community
- [ ] Tells a story about Viam's value

**Scoring:**
- 5: High learning value + likely to surface issues + high visibility
- 4: Strong in 2 of 3 areas
- 3: Moderate across all areas
- 2: Strong in 1 area only
- 1: Limited learning, quality, or visibility value

---

## 6. Cool Factor & Practical Utility

**Question:** Is this project genuinely exciting or solving a real problem people care about?

Technical merit alone isn't enough. The best projects make people say "that's really cool" or "I actually need that." This criterion captures the intangible qualities that generate enthusiasm and engagement.

### Cool Factor

Does this project have "wow" appeal?

- **Visceral impact** - Does it make people stop and watch? Does it do something visually impressive or unexpected?
- **Story potential** - Can you explain it to a non-engineer and see their eyes light up?
- **Demo magnetism** - Will people gather around to see it in action?
- **Shareability** - Would engineers post a video of this on social media?
- **Pride of ownership** - Will the team brag about building this?

Examples of cool:
- A robot that plays chess against you
- An arm that sorts candy by color
- A rover that maps your office autonomously
- A system that recognizes and greets people by name

### Practical Utility

Does this project solve a real problem?

- **Genuine usefulness** - Would someone actually use this beyond the demo?
- **Pain point addressed** - Does it solve an annoying or tedious problem?
- **Internal value** - Could this be used at Viam (office, warehouse, events)?
- **Customer relevance** - Does it mirror something customers actually want to build?
- **Template potential** - Could this become a reference implementation others copy?

Examples of useful:
- Automated inventory tracking for the hardware lab
- Meeting room occupancy monitoring
- Package delivery notification system
- Automated plant watering based on soil sensors

### The "Why Should I Care?" Test

Ask yourself:
- If I showed this to my non-technical friends, would they think it's cool?
- If I showed this to a customer, would they see how it applies to their problems?
- If I showed this at a conference, would people want to learn more?
- Would I be excited to work on this for the next 3 months?

**Scoring:**
- 5: Genuinely exciting AND practically useful - people will talk about this
- 4: Either very cool OR very useful, with some of the other
- 3: Moderately interesting, would make a decent demo
- 2: Technically sound but uninspiring - "so what?"
- 1: Neither cool nor useful - a solution looking for a problem

---

## Summary Scorecard

| Criterion | Weight | Score (1-5) | Weighted |
|-----------|--------|-------------|----------|
| Platform Capability Coverage | 20% | | |
| Lifecycle Stage Coverage | 15% | | |
| Problem-Platform Fit | 15% | | |
| Feasibility & Scope | 20% | | |
| Learning & Quality Impact | 10% | | |
| Cool Factor & Practical Utility | 20% | | |
| **Total** | 100% | | |

### Thresholds

- **4.0+**: Strong candidate, approve
- **3.0-3.9**: Conditional approval, address concerns
- **2.0-2.9**: Needs revision before approval
- **<2.0**: Does not fit program goals

---

## Quick Checklist

Before detailed scoring, projects must pass these gates:

- [ ] **Exercises real Viam capabilities** (not just using Viam as a thin wrapper)
- [ ] **Has a 3-day MVP** (something to demo at hackathon end)
- [ ] **Hardware is available or simulatable** (remote engineers can participate)
- [ ] **Engineers will learn something** (not just doing what they already know)
- [ ] **Potential to surface platform issues** (serves quality goal)

Projects failing any gate should be revised before full assessment.

---

## Examples

### Strong Project (Score ~4.5)

**Autonomous inventory scanner**
- Platform coverage: Remote dev, data capture, ML inference, navigation (4 Tier 1) → 5
- Lifecycle: MVP is Stage 2 (deployed in real space), backlog includes multi-robot → 4
- Problem fit: All problems Viam solves well → 5
- Feasibility: Uses available mobile base, known ML models → 4
- Learning/Quality: Exercises many subsystems, great demo → 5
- Cool/Useful: Solves real hardware lab problem, autonomous robot roaming is inherently cool → 5

### Weak Project (Score ~2.0)

**LED blink patterns**
- Platform coverage: Single GPIO control (Tier 3 only) → 1
- Lifecycle: Stage 1 only, no deployment scenario → 1
- Problem fit: Viam adds no value over direct hardware control → 1
- Feasibility: Trivially easy → 5
- Learning/Quality: Minimal learning, no quality impact → 1
- Cool/Useful: Not interesting, no practical value → 1

### Medium Project - Cool but Limited Platform Use (Score ~3.2)

**Robot that plays tic-tac-toe**
- Platform coverage: Basic arm control, simple vision (Tier 2/3) → 2
- Lifecycle: Stage 1 bench demo only → 1
- Problem fit: Viam works but isn't differentiated here → 2
- Feasibility: Achievable, uses available arm → 4
- Learning/Quality: Moderate learning, limited quality impact → 3
- Cool/Useful: Very cool demo, people will gather to watch → 5

*This project scores well on cool factor but lacks platform depth. Consider expanding scope to include remote play, multi-game tracking, or fleet deployment to game stations.*
