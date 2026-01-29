# Project Planning Guide

This guide captures the strategic thinking behind Build on Viam project selection and design. Use it when proposing new projects or evaluating how well our portfolio demonstrates Viam's capabilities.

## Goals

Build on Viam projects should collectively:

1. **Demonstrate all major Viam capabilities** - Every significant platform feature should be showcased by at least one project
2. **Provide reference implementations** - Projects serve as examples for customers and internal teams
3. **Exercise the full lifecycle** - From prototype to fleet deployment and maintenance
4. **Be compelling demos** - Visitors, customers, and executives should be impressed

## Viam Platform Capabilities

These are the capabilities we want to demonstrate across our project portfolio:

### Core Capabilities (must be covered)

| Capability | Description |
|------------|-------------|
| **Hardware Integration** | Consistent APIs across cameras, arms, motors, sensors |
| **Motion Planning** | Arm movement, obstacle avoidance, frame system |
| **Vision / ML Inference** | Object detection, classification, custom models |
| **Data Capture & Sync** | Edge-to-cloud data pipelines with offline resilience |
| **Remote Operation** | Control and monitor robots through firewalls |
| **Module Development** | Custom components and services via Registry |

### Scale & Fleet Capabilities

| Capability | Description |
|------------|-------------|
| **Fragments** | Reusable configuration blocks for fleet management |
| **Fleet Management** | Managing multiple machines with shared configs |
| **OTA Updates** | Deploying module and model updates to fleet |
| **Provisioning** | Automatic setup of new machines |

### Operational Capabilities

| Capability | Description |
|------------|-------------|
| **Event-Driven Automation** | Event-driven automation (sensor thresholds, detections) |
| **Scheduled Tasks** | Periodic operations without custom schedulers |
| **Monitoring & Alerting** | Fleet health visibility and notifications |
| **Data Pipeline (ML Training)** | Capture → Label → Train → Deploy workflow |

### Customer-Facing Capabilities

| Capability | Description |
|------------|-------------|
| **Customer Delivery** | White-label auth, TypeScript/Flutter SDKs, billing |
| **Web/Mobile Apps** | Customer-facing interfaces using Viam SDKs |

## Current Feature Coverage

As of the current project portfolio, here's how capabilities are covered:

**Active Projects:** Vino, Chess, Salad Maker, Greenhouse, Barista, Inventory Tracker, Retro Roomba, Smart Lighting

**Future Projects:** Cleaning Cart, Dishwasher, Box Bot

| Capability | Primary Project | Secondary |
|------------|-----------------|-----------|
| Hardware Integration | All projects | - |
| Motion Planning | Chess, Vino, Salad Maker, Barista | - |
| Vision / ML | Chess, Inventory Tracker, Greenhouse | Salad Maker, Barista |
| Data Capture & Sync | Greenhouse, Retro Roomba | All projects |
| Remote Operation | All projects | - |
| Module Development | **Retro Roomba**, **Smart Lighting** | Inventory Tracker |
| Fragments | Greenhouse, Retro Roomba | Smart Lighting |
| Fleet Management | **Greenhouse**, **Smart Lighting** | Barista, Inventory Tracker |
| OTA Updates | Retro Roomba (stretch) | - |
| Provisioning | Retro Roomba (stretch) | - |
| Event-Driven Automation | **Inventory Tracker**, **Smart Lighting** | Greenhouse, Vino, Chess, Barista, Salad Maker |
| Scheduled Tasks | **Smart Lighting**, **Inventory Tracker** | Greenhouse, Barista, Vino |
| Monitoring & Alerting | **Greenhouse**, Barista | Inventory Tracker |
| Data Pipeline (ML) | **Chess**, **Greenhouse** | Inventory Tracker, Salad Maker, Barista |
| Customer Delivery | **Inventory Tracker**, **Vino** | Salad Maker, Barista |
| Web/Mobile Apps | Inventory Tracker, Barista | Vino, Salad Maker |

**Bold** = Primary responsibility for demonstrating this capability.


## Proposing New Projects

When proposing a new project, consider:

### 1. Feature Coverage

- Does this project demonstrate capabilities not well-covered elsewhere?
- Which "gap features" could this project address?
- Would this be the PRIMARY demo for any capability?

### 2. Natural Fit

- Do the gap features fit naturally, or are they forced?
- Example: Fleet management fits Greenhouse naturally (multiple sensor stations) but not Chess (single board)
- Example: Customer delivery fits Vino naturally (guest-facing) but not Box-bot (internal utility)

### 3. Demo Appeal

- Is this compelling to watch?
- Would visitors/customers be impressed?
- Does it have a clear "wow" moment?

### 4. Feasibility

- Can this be built with available hardware?
- Is the MVP achievable in hackathon timeframe?
- Are the stretch goals realistic?

### 5. Lifecycle Coverage

- Does this project exercise multiple lifecycle stages?
- Prototype → Deploy → Scale → Fleet → Maintain
- Greenhouse scores highly because it naturally progresses through all stages

### 6. Maintenance

- Can this project be maintained long-term?
- Is the hardware reliable?
- Will someone own it after the hackathon?


# Project Assessment Criteria

This section defines how projects proposed for the Build on Viam program are evaluated.

## Assessment Framework

Projects are evaluated across six dimensions, each scored 1-5.

### 1. Platform Capability Coverage

**Question:** Does this project demonstrate capabilities that differentiate Viam?

#### Tier 1: Core Differentiators (High Value)

Projects should exercise at least 2-3 of these:

| Capability | What It Proves |
|------------|----------------|
| **Remote Development** | Code on laptop, run on device over network (no SSH, no deploy step) |
| **Hardware Abstraction** | Same code works across different hardware vendors |
| **Data Capture & Sync** | Edge-to-cloud data pipeline with offline buffering |
| **Fragments** | Reusable configuration blocks that enable 1→many scaling |
| **Fleet Management** | Provisioning, monitoring, OTA updates across multiple machines |
| **Module Registry** | Extend platform with custom components, share via registry |

#### Tier 2: Platform Capabilities (Medium Value)

| Capability | What It Proves |
|------------|----------------|
| Motion planning | Path planning, inverse kinematics, collision avoidance |
| ML inference | Deploy and run models (TensorFlow, PyTorch, ONNX) |
| SLAM / Navigation | Mapping, localization, autonomous navigation |
| Computer vision | Detection, classification, segmentation |
| Sensor fusion | Combine data from multiple sensors |
| Services (vision, motion, etc.) | Use built-in higher-level services |

#### Tier 3: Basic Usage (Lower Value)

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

### 2. Lifecycle Stage Coverage

**Question:** Does this project expose engineers to challenges beyond prototyping?

| Stage | Timeline | Problems | Viam Value |
|-------|----------|----------|------------|
| **1. Prototype** | Weeks | Get hardware working, write control logic | Hardware drivers, remote dev |
| **2. First Deployment** | 1-3 months | Real-world validation, field config, connectivity | Remote access, calibration |
| **3. Multiple Units** | 3-6 months | Configuration variance, per-machine differences | Fragments, config management |
| **4. Fleet at Scale** | 6+ months | Monitoring, updates, rollback | OTA, fleet dashboards |
| **5. Maintenance** | Ongoing | Debugging, logs, model updates | Remote diagnostics, data pipelines |

**Scoring:**
- 5: Backlog explicitly addresses Stages 3-5 (fleet, scale, maintenance)
- 4: MVP reaches Stage 2, backlog addresses Stage 3
- 3: MVP reaches Stage 2 (real deployment scenario)
- 2: MVP is Stage 1 only, but backlog extends further
- 1: Stays entirely in Stage 1 (bench prototype only)

### 3. Problem-Platform Fit

**Question:** Does this project address problems Viam is designed to solve?

**Problems Viam Solves Well (Prioritize These):**
- Connecting diverse hardware (cameras, motors, sensors, arms)
- Abstracting vendor differences
- Remote access to robots (NAT traversal, firewalls)
- Capturing sensor data at the edge with cloud sync
- Managing configuration across multiple robots
- Deploying ML models to edge devices

**Problems Viam Partially Solves (Acceptable):**
- Complex motion planning (supported but not all scenarios)
- Real-time control (WebRTC adds latency)
- Simulation (emerging, not fully integrated)

**Problems Viam Doesn't Solve (Avoid as Primary Focus):**
- Low-level motor control algorithms
- Custom RTOS or real-time guarantees
- Hardware design or manufacturing

**Scoring:**
- 5: Primary problems are all in "solves well" category
- 4: Primary problems mostly in "solves well", some "partial"
- 3: Mix of "solves well" and "partial"
- 2: Primarily "partial" problems
- 1: Problems outside Viam's scope

### 4. Feasibility & Scope

**Question:** Can this project achieve meaningful results within program constraints?

**Hackathon MVP (3 days)** must be achievable:
- Working demo that shows core functionality
- Uses available hardware or simulation
- Team of 2-4 engineers can complete it

| Factor | Preferred | Acceptable | Problematic |
|--------|-----------|------------|-------------|
| Hardware availability | In-office stock | Orderable, <$500 | Custom, long lead time |
| Setup complexity | Plug and play | Some assembly | Significant integration |
| Technical dependencies | Viam SDK + standard libs | Common ML frameworks | Obscure libraries |

**Scoring:**
- 5: MVP clearly achievable, hardware available, well-understood domain
- 4: MVP achievable with some risk, hardware obtainable
- 3: MVP achievable but tight, some hardware or complexity concerns
- 2: MVP at risk, significant unknowns
- 1: MVP unlikely in timeframe, major blockers

### 5. Learning & Quality Impact

**Question:** Will this project achieve program goals?

**Engineer Learning** - Does the project teach about:
- Viam's architecture and component model
- Configuration and fragments
- SDK usage patterns (Python, Go, TypeScript)
- Data management and ML deployment
- Fleet operations and monitoring

**Platform Quality** - Will building this project likely:
- Surface bugs in core platform
- Identify documentation gaps
- Reveal UX friction points
- Exercise less-used platform features

**Scoring:**
- 5: High learning value + likely to surface issues + high visibility
- 4: Strong in 2 of 3 areas
- 3: Moderate across all areas
- 2: Strong in 1 area only
- 1: Limited learning, quality, or visibility value

### 6. Cool Factor & Practical Utility

**Question:** Is this project genuinely exciting or solving a real problem?

**Cool Factor** - Does this project have "wow" appeal?
- Visceral impact - Does it make people stop and watch?
- Story potential - Can you explain it to a non-engineer and see their eyes light up?
- Demo magnetism - Will people gather around to see it in action?

**Practical Utility** - Does this project solve a real problem?
- Genuine usefulness - Would someone actually use this beyond the demo?
- Pain point addressed - Does it solve an annoying or tedious problem?
- Customer relevance - Does it mirror something customers want to build?

**Scoring:**
- 5: Genuinely exciting AND practically useful
- 4: Either very cool OR very useful, with some of the other
- 3: Moderately interesting, would make a decent demo
- 2: Technically sound but uninspiring
- 1: Neither cool nor useful

## Summary Scorecard

| Criterion | Weight | Score (1-5) |
|-----------|--------|-------------|
| Platform Capability Coverage | 20% | |
| Lifecycle Stage Coverage | 15% | |
| Problem-Platform Fit | 15% | |
| Feasibility & Scope | 20% | |
| Learning & Quality Impact | 10% | |
| Cool Factor & Practical Utility | 20% | |
| **Total** | 100% | |

### Thresholds

- **4.0+**: Strong candidate, approve
- **3.0-3.9**: Conditional approval, address concerns
- **2.0-2.9**: Needs revision before approval
- **<2.0**: Does not fit program goals

## Quick Checklist

Before detailed scoring, projects must pass these gates:

- [ ] **Exercises real Viam capabilities** (not just using Viam as a thin wrapper)
- [ ] **Has a 3-day MVP** (something to demo at hackathon end)
- [ ] **Hardware is available or simulatable** (remote engineers can participate)
- [ ] **Engineers will learn something** (not just doing what they already know)
- [ ] **Potential to surface platform issues** (serves quality goal)

## Assessment Examples

### Strong Project (Score ~4.5)

**Autonomous inventory scanner**
- Platform coverage: Remote dev, data capture, ML inference, navigation (4 Tier 1) → 5
- Lifecycle: MVP is Stage 2 (deployed in real space), backlog includes multi-robot → 4
- Problem fit: All problems Viam solves well → 5
- Feasibility: Uses available mobile base, known ML models → 4
- Learning/Quality: Exercises many subsystems, great demo → 5
- Cool/Useful: Solves real hardware lab problem → 5

### Medium Project (Score ~3.2)

**Robot that plays tic-tac-toe**
- Platform coverage: Basic arm control, simple vision (Tier 2/3) → 2
- Lifecycle: Stage 1 bench demo only → 1
- Problem fit: Viam works but isn't differentiated here → 2
- Feasibility: Achievable, uses available arm → 4
- Learning/Quality: Moderate learning, limited quality impact → 3
- Cool/Useful: Very cool demo, people will gather to watch → 5

*This project scores well on cool factor but lacks platform depth. Consider expanding scope to include remote play, multi-game tracking, or fleet deployment.*
