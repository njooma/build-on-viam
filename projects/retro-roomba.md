# Project: Retro Roomba Revival

## Overview

**One-line description:** Bring a Roomba 650/655 into the Viam ecosystem with a custom driver module

**Project Lead:** TBD
**Team Members:** TBD
**Status:** New

## Description

Retro Roomba Revival takes a Roomba 650/655 and integrates it with Viam by building a custom driver module. Engineers implement the Roomba Open Interface protocol and handle serial communication. The project deliberately avoids computer vision to focus on core module development and hardware integration fundamentals.

## Viam Capabilities Demonstrated

| Capability | Coverage | Notes |
|------------|----------|-------|
| Custom Module Development | Primary | Build driver from scratch |
| Hardware Abstraction | Primary | Implement base, sensor, power_sensor, movement_sensor APIs |
| Protocol Implementation | Primary | Roomba Open Interface serial protocol |
| Data Capture & Sync | Strong | Sensor logs, battery cycles, patrol data |
| Triggers | Strong | Low battery, dock needed, bump detected |
| Remote Operation | Strong | Control through app and SDKs |
| Fleet Management | Stretch | Multiple Roombas |
| Fragments | Strong | Hardware fragment for Roomba setup |
| Module Registry | Strong | Publish and version the driver |
| SDK Development | Strong | Python, Go, TypeScript clients |
| Customer Delivery | Stretch | Guest control interface |

---

## Hardware Requirements

| Component | Description | Options |
|-----------|-------------|---------|
| Roomba | 600 series base | Roomba 650 or 655 |
| Compute | Main controller | Raspberry Pi 5 |
| Serial Adapter | Connect Pi to Roomba | Mini-DIN cable + logic level converter |

**Estimated Hardware Cost:** ~$150 (Roomba + Pi + wiring)

**Remote-Friendly:** Partially - protocol/module development remote, physical testing requires hardware

---

## MVP Options

Select one for hackathon scope:

### Option A: Basic Drive Control (Recommended)
Drive Roomba from Viam app, read sensors.
- **Complexity:** Medium
- **Demo Appeal:** Medium
- **Scope:** Serial protocol, base API, basic sensors

### Option B: Full Sensor Suite
All Roomba sensors exposed through Viam.
- **Complexity:** Medium-High
- **Demo Appeal:** Medium
- **Scope:** Complete sensor implementation

**Selected MVP:** _______________

---

## Feature Backlog: Organized by Learning Objective

### Phase 1: Module Development Fundamentals

**Learning Goal:** Understand how Viam modules work, how to implement component APIs, and how the resource lifecycle operates.

#### 1.1 Basic Module Structure
- [ ] **Create module scaffold** - main.go, meta.json, resource registration
  - *Teaches:* Module entry points, resource registration pattern
- [ ] **Implement base.Base interface** - SetVelocity, SetPower, Stop, IsMoving
  - *Teaches:* Component API contracts, how Viam abstracts hardware
- [ ] **Handle serial port configuration** - Configurable port, baud rate via attributes
  - *Teaches:* Component configuration, Validate() pattern
- [ ] **Implement Reconfigure()** - Handle config changes without restart
  - *Teaches:* Dynamic reconfiguration, resource lifecycle
- [ ] **Implement Close()** - Clean shutdown, release serial port
  - *Teaches:* Resource cleanup, graceful shutdown

#### 1.2 Multiple Component Types
- [ ] **Implement sensor.Sensor** - Bump sensors as generic sensor
  - *Teaches:* Sensor API, Readings() return format
- [ ] **Implement power_sensor.PowerSensor** - Battery voltage, current, charge level
  - *Teaches:* PowerSensor API, voltage/current/power readings
- [ ] **Implement movement_sensor.MovementSensor** - Wheel encoders for odometry
  - *Teaches:* MovementSensor API, position/orientation tracking
- [ ] **Create composite component** - Single config creates all Roomba resources
  - *Teaches:* Resource dependencies, module organization patterns

#### 1.3 Protocol Implementation
- [ ] **Roomba OI initialization** - Start, Safe, Full mode commands
  - *Teaches:* Serial communication, state machines
- [ ] **Sensor packet parsing** - Decode binary sensor data
  - *Teaches:* Binary protocols, byte manipulation in Go
- [ ] **Command serialization** - Encode drive commands
  - *Teaches:* Protocol encoding, endianness
- [ ] **Error handling** - Serial timeouts, reconnection logic
  - *Teaches:* Robust hardware communication, error recovery

#### 1.4 Testing Your Module
- [ ] **Unit tests for protocol** - Test packet encoding/decoding
  - *Teaches:* Testing hardware code without hardware
- [ ] **Mock serial port** - Test module logic with fake Roomba
  - *Teaches:* Dependency injection, testable design
- [ ] **Integration test script** - Python SDK script to verify module
  - *Teaches:* SDK usage, end-to-end testing

---

### Phase 2: Configuration & Fragments

**Learning Goal:** Understand Viam's configuration architecture, how fragments enable reuse, and the two-layer config pattern.

#### 2.1 Machine Configuration
- [ ] **Create basic machine config** - Roomba module + components
  - *Teaches:* Machine configuration structure, component dependencies
- [ ] **Use attributes for hardware specifics** - Serial port, sensor polling rate
  - *Teaches:* Attribute schema design, configuration flexibility
- [ ] **Configure frame system** - Define Roomba's coordinate frame
  - *Teaches:* Frame system, spatial relationships

#### 2.2 Fragment Creation
- [ ] **Extract hardware fragment** - Roomba base + sensors as reusable fragment
  - *Teaches:* Fragment structure, what belongs in a fragment
- [ ] **Add fragment variables** - Serial port, device name as variables
  - *Teaches:* Fragment parameterization, machine-specific values
- [ ] **Version the fragment** - Tag stable versions, maintain dev version
  - *Teaches:* Fragment versioning strategy

#### 2.3 Multi-Machine Configuration
- [ ] **Deploy to second Roomba** - Same fragment, different variables
  - *Teaches:* Fragment reuse, configuration scaling
- [ ] **Use fragment mods** - Override specific settings per machine
  - *Teaches:* Fragment customization, inheritance pattern
- [ ] **Organize by location** - Different locations for different Roombas
  - *Teaches:* Location hierarchy, organizational structure

---

### Phase 3: Remote Development & SDKs

**Learning Goal:** Master Viam's development workflow and understand how to build applications using different SDKs.

#### 3.1 CLI Development Pattern
- [ ] **Run module locally against remote hardware** - Connect laptop to Pi-hosted Roomba
  - *Teaches:* WebRTC connection, remote development workflow
- [ ] **Iterate without deploy** - Edit code, rebuild, test immediately
  - *Teaches:* Development velocity, why this pattern matters
- [ ] **Debug with logs** - Use logger, view in app
  - *Teaches:* Logging best practices, remote debugging

#### 3.2 Python SDK
- [ ] **Basic control script** - Connect, drive forward, read sensors
  - *Teaches:* Python SDK patterns, async/await usage
- [ ] **Patrol script** - Drive a pattern, avoid obstacles
  - *Teaches:* Control loops, sensor-based decisions
- [ ] **Data collection script** - Capture sensor data to files
  - *Teaches:* SDK data access, offline analysis

#### 3.3 Go SDK
- [ ] **Control application in Go** - Same functionality as Python
  - *Teaches:* Go SDK patterns, context usage
- [ ] **Compare SDK ergonomics** - Document differences from Python
  - *Teaches:* SDK design tradeoffs, language-specific patterns

#### 3.4 TypeScript SDK
- [ ] **Web control interface** - Browser-based Roomba control
  - *Teaches:* TypeScript SDK, web application patterns
- [ ] **Real-time sensor display** - Live sensor values in browser
  - *Teaches:* Streaming data, WebSocket-like patterns
- [ ] **Mobile-responsive design** - Control from phone browser
  - *Teaches:* Practical UI considerations

---

### Phase 4: Data Management

**Learning Goal:** Understand Viam's data capture, sync, and query capabilities.

#### 4.1 Data Capture Configuration
- [ ] **Enable sensor data capture** - Configure capture for all sensors
  - *Teaches:* Data capture configuration, capture frequency tradeoffs
- [ ] **Configure sync rules** - When and how data syncs to cloud
  - *Teaches:* Sync configuration, bandwidth management

#### 4.2 Working with Captured Data
- [ ] **View data in app** - Browse captured sensor data
  - *Teaches:* Data visualization in Viam app
- [ ] **Query data via CLI** - Use viam data commands
  - *Teaches:* CLI data access, filtering and export
- [ ] **Query data via SDK** - Programmatic data access
  - *Teaches:* Data client SDK, building analytics

#### 4.3 Data Analysis
- [ ] **Battery degradation tracking** - Analyze charge cycles over time
  - *Teaches:* Time-series analysis, predictive insights
- [ ] **Patrol efficiency metrics** - Analyze coverage patterns
  - *Teaches:* Operational analytics, optimization
- [ ] **Error pattern analysis** - Correlate bumps, cliffs, stuck events
  - *Teaches:* Anomaly detection, reliability analysis

---

### Phase 5: Triggers & Automation

**Learning Goal:** Understand event-driven automation in Viam.

#### 5.1 Basic Triggers
- [ ] **Low battery trigger** - Alert when battery below threshold
  - *Teaches:* Trigger configuration, threshold-based events
- [ ] **Bump detected trigger** - Log and alert on collisions
  - *Teaches:* Event-based triggers, immediate response
- [ ] **Cliff detected trigger** - Emergency alert on cliff detection
  - *Teaches:* Safety-critical triggers

#### 5.2 Trigger Actions
- [ ] **Webhook notification** - Send to Slack/Discord on events
  - *Teaches:* Webhook integration, external notifications
- [ ] **Email alerts** - Send email on critical events
  - *Teaches:* Email action configuration
- [ ] **Data capture on trigger** - Capture extra data when event occurs
  - *Teaches:* Conditional data capture

#### 5.3 Complex Automation
- [ ] **Return to dock on low battery** - Trigger initiates dock sequence
  - *Teaches:* Trigger-initiated actions, state management
- [ ] **Scheduled patrol** - Clean at specific times
  - *Teaches:* Scheduled triggers, cron-like functionality
- [ ] **Conditional logic** - Only clean if motion not detected recently
  - *Teaches:* Complex trigger conditions

---

### Phase 6: Services

**Learning Goal:** Understand Viam's built-in services and when to use them.

#### 6.1 Motion Service
- [ ] **Configure motion service** - Even for base-only robot
  - *Teaches:* Motion service scope, when it applies
- [ ] **Understand frame system** - How motion service uses frames
  - *Teaches:* Frame relationships, transforms

---

### Phase 7: Module Publishing & Registry

**Learning Goal:** Understand how to share modules and manage versions.

#### 7.1 Prepare for Publishing
- [ ] **Write comprehensive README** - Installation, configuration, usage
  - *Teaches:* Documentation standards
- [ ] **Define meta.json completely** - All fields, entry point, models
  - *Teaches:* Module metadata requirements
- [ ] **Add example configurations** - Sample machine configs
  - *Teaches:* User onboarding, examples

#### 7.2 Publishing
- [ ] **Publish to registry (private)** - Internal use first
  - *Teaches:* Publishing workflow, visibility settings
- [ ] **Version management** - Semantic versioning, changelog
  - *Teaches:* Version strategy, breaking changes
- [ ] **Publish publicly** - Share with community
  - *Teaches:* Public module considerations

#### 7.3 Updates & Maintenance
- [ ] **Release update** - Fix bug, publish new version
  - *Teaches:* Update workflow
- [ ] **OTA update to fleet** - Update all Roombas to new version
  - *Teaches:* Fleet updates, rollout strategy
- [ ] **Rollback** - Revert to previous version if issues
  - *Teaches:* Rollback procedures, safety

---

### Phase 8: Fleet Management

**Learning Goal:** Understand how Viam scales to multiple machines.

#### 8.1 Multi-Robot Setup
- [ ] **Deploy second Roomba** - Same module, new machine
  - *Teaches:* Machine provisioning, fragment reuse
- [ ] **Unique naming** - Consistent naming across fleet
  - *Teaches:* Fleet organization, naming conventions
- [ ] **Location organization** - Group by physical location
  - *Teaches:* Location hierarchy

#### 8.2 Fleet Operations
- [ ] **Fleet dashboard** - View all Roombas in one place
  - *Teaches:* Fleet visibility, monitoring
- [ ] **Bulk configuration** - Update fragment, propagate to all
  - *Teaches:* Configuration at scale
- [ ] **Fleet-wide data query** - Aggregate data across robots
  - *Teaches:* Cross-machine analytics

#### 8.3 Provisioning
- [ ] **Provisioning flow** - Add new Roomba with minimal steps
  - *Teaches:* Provisioning workflow
- [ ] **Viam agent** - Auto-setup with agent
  - *Teaches:* Agent-based provisioning

---

### Phase 9: Customer-Facing Features

**Learning Goal:** Understand how to build end-user experiences with Viam.

#### 9.1 Custom Web Application
- [ ] **Build control app** - Custom web UI for Roomba control
  - *Teaches:* TypeScript SDK in production app
- [ ] **User authentication** - Login to control Roomba
  - *Teaches:* Auth integration, API keys
- [ ] **Permission scoping** - Limit what users can do
  - *Teaches:* Operator permissions, security

#### 9.2 Mobile Application
- [ ] **Flutter app skeleton** - Basic mobile app structure
  - *Teaches:* Flutter SDK usage
- [ ] **Control interface** - Drive Roomba from phone
  - *Teaches:* Mobile control patterns
- [ ] **Push notifications** - Alert when cleaning done
  - *Teaches:* Mobile notification integration

#### 9.3 Voice Control
- [ ] **Voice command integration** - "Roomba, clean the lab"
  - *Teaches:* Voice assistant integration patterns
- [ ] **Natural language mapping** - Map commands to actions
  - *Teaches:* Intent mapping, UX design

---

### Phase 10: Advanced Integration

**Learning Goal:** Complex multi-system integration.

#### 11.1 Integration with Other Projects
- [ ] **Smart Lighting integration** - Lights follow Roomba
  - *Teaches:* Cross-project integration, event coordination
- [ ] **Inventory Tracker integration** - Roomba reports floor items
  - *Teaches:* Data sharing between systems

#### 11.2 External System Integration
- [ ] **Home Assistant integration** - Expose Roomba to HA
  - *Teaches:* External API integration
- [ ] **Calendar integration** - Clean based on calendar events
  - *Teaches:* External data sources

#### 11.3 Multi-Robot Coordination
- [ ] **Zone assignment** - Multiple Roombas divide space
  - *Teaches:* Multi-robot coordination
- [ ] **Collision avoidance** - Roombas avoid each other
  - *Teaches:* Inter-robot communication

---

## Success Criteria

**MVP Complete When:**
- [ ] Roomba drives from Viam app (SetVelocity works)
- [ ] Battery level readable as sensor
- [ ] Bump sensors trigger stops
- [ ] Module published to registry (private)

**Phase 1 Complete When:**
- [ ] All Roomba sensors exposed through Viam
- [ ] Module has unit tests
- [ ] Documentation complete

**Phase 2 Complete When:**
- [ ] Hardware fragment created and versioned
- [ ] Second Roomba deployed using fragment

**Full Project Complete When:**
- [ ] Fleet of 2+ Roombas managed together
- [ ] Custom web or mobile control interface
- [ ] Triggers and automation configured
- [ ] Data capture and analysis pipeline working

---

## Documentation Deliverables

### For Users
- [ ] README with setup instructions
- [ ] Wiring diagram (Pi to Roomba)
- [ ] Configuration examples

### For Developers
- [ ] Roomba Open Interface command reference
- [ ] Module development tutorial
- [ ] Testing guide

### For Hardware Builders
- [ ] Wiring guide (Pi to Roomba serial)
- [ ] Parts list with purchase links

### For Viam Learners
- [ ] "What I Learned" blog post per phase
- [ ] Comparison: Viam vs. ROS for this project
- [ ] Tips for module development

---

## Links

- **Jira Epic:** [TBD]
- **GitHub Repo:** [TBD]
- **Viam Organization:** [TBD]
- **Hardware BOM:** [TBD]

---

## Technical Reference

### Roomba Open Interface

**Connection:**
- Mini-DIN connector on Roomba
- TXD, RXD, GND, battery power
- 5V logic (needs level shifter for 3.3V Pi)
- Default baud: 115200 (Roomba 650/655)

**Key commands:**

| Command | Opcode | Data | Description |
|---------|--------|------|-------------|
| Start | 128 | none | Initialize OI |
| Safe | 131 | none | Safe mode (cliff/bump protection) |
| Full | 132 | none | Full mode (no limits) |
| Drive | 137 | velocity (2), radius (2) | Drive wheels |
| Sensors | 142 | packet ID | Request sensor data |
| Dock | 143 | none | Seek dock |

**Sensor packets:**

| Packet | ID | Bytes | Description |
|--------|----|----|-------------|
| Bump/Wheeldrop | 7 | 1 | Bump and wheel drop flags |
| Cliff Left | 9 | 1 | Left cliff sensor |
| Battery Charge | 25 | 2 | Current charge (mAh) |
| Distance | 19 | 2 | Distance since last (mm) |
| Angle | 20 | 2 | Angle since last (degrees) |

### Viam Module Structure

```
roomba-legacy/
├── main.go              # Entry point, resource registration
├── roomba_base.go       # Implements base.Base
├── roomba_sensor.go     # Implements sensor.Sensor (bump)
├── roomba_power.go      # Implements powersensor.PowerSensor
├── roomba_movement.go   # Implements movementsensor.MovementSensor
├── protocol.go          # OI protocol implementation
├── protocol_test.go     # Protocol unit tests
├── meta.json            # Module metadata
└── README.md            # Documentation
```

## Cost Comparison

| Platform | Cost | Driver Work | Learning Depth |
|----------|------|-------------|----------------|
| Roomba 650/655 | ~$150 | Build from scratch | Very High |
| Create 3 | $299 | Configure ROS 2 bridge | Medium |
| TurtleBot 4 | $1,850 | Configure existing | Low |

---

## Notes

**Why this project is valuable:**
- Cheapest mobile base option ($30-50)
- Forces deep understanding of Viam abstractions
- No computer vision required - focuses on fundamentals
- Creates reusable module for community
- Covers core Viam capabilities without complex dependencies

**Skills developed:**
- Serial communication & binary protocols
- Viam module development (Go)
- Multiple component API implementation
- SDK usage (Python, Go, TypeScript)
- Data capture and analysis
- Fleet management

**References:**
- [Roomba Open Interface Specification](https://edu.irobot.com/what-we-offer/create3-resources)
- [iRobot Create 2 OI Spec (similar protocol)](https://www.irobot.com/about-irobot/stem/create-2)
