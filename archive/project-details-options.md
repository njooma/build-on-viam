# Project Details - Options for Consideration

For each project, choose from the options below to define MVP scope, backlog, and stretch goals.

---

## 1. Vino

**Concept:** Wine service robot - pouring, serving, or sommelier assistance.

### MVP Options (Pick One)

| Option | Description | Complexity | Demo Appeal |
|--------|-------------|------------|-------------|
| **A. Pour on demand** | Arm picks bottle from rack, pours measured amount into glass at fixed location | Medium | High |
| **B. Glass detection pour** | Vision detects glass placement, arm pours into detected glass | Medium-High | High |
| **C. Wine selector** | User selects wine via app/voice, arm retrieves correct bottle from rack | Medium | Medium |
| **D. Sommelier display** | Camera reads wine label, displays pairing suggestions and tasting notes | Low-Medium | Medium |

### Post-Hackathon Backlog Options

| Option | Description | Viam Capabilities |
|--------|-------------|-------------------|
| Multiple bottle types | Handle different bottle shapes/sizes | Vision, motion planning |
| Pour level detection | Camera monitors fill level, stops at right amount | Vision, ML |
| Temperature monitoring | Track wine storage temps, alert if out of range | Data capture, alerting |
| Inventory tracking | Track bottles consumed, sync to cloud | Data management |
| Voice commands | "Pour me a glass of the Pinot" | Integration (external) |
| Multi-station fleet | Multiple Vino units in different locations | Fleet management |
| Glass handoff | Robot hands glass to person or mobile robot | Manipulation, coordination |

### Stretch Goals

- [ ] Wine recommendation engine based on preferences/history
- [ ] Decanting with timed aeration
- [ ] Label scanning with vintage database lookup
- [ ] Party mode: queue up orders from multiple guests

### Hardware Options

| Component | Options |
|-----------|---------|
| Arm | xArm 6, xArm 5 Lite, UFactory Lite 6 |
| Gripper | Parallel jaw, soft gripper (for bottles) |
| Camera | Intel RealSense, standard USB camera |
| Rack | Custom wine rack with known positions, or vision-based detection |

### Viam Capabilities Exercised

- [ ] Arm control & motion planning
- [ ] Gripper manipulation
- [ ] Vision (glass/bottle detection)
- [ ] Data capture (pours, inventory)
- [ ] Remote operation
- [ ] ML inference (label reading, pour level)

---

## 2. Chess

**Concept:** Robot that plays chess against a human opponent, physically moving pieces.

### MVP Options (Pick One)

| Option | Description | Complexity | Demo Appeal |
|--------|-------------|------------|-------------|
| **A. Full game play** | Robot plays complete game, detects all pieces, makes legal moves | High | Very High |
| **B. Move execution only** | Human inputs moves via app, robot executes them physically | Medium | High |
| **C. Piece reset** | Robot resets board to starting position after game | Medium | Medium |
| **D. Teaching mode** | Robot demonstrates famous games move-by-move | Medium | High |

### Post-Hackathon Backlog Options

| Option | Description | Viam Capabilities |
|--------|-------------|-------------------|
| Difficulty levels | Adjustable AI difficulty | ML/logic |
| Game recording | Capture and replay games with data service | Data capture |
| Remote play | Play against robot from anywhere via app | Remote operation |
| Tournament mode | Track multiple games, maintain leaderboard | Data management |
| Voice commentary | Robot announces moves and commentary | Integration (TTS) |
| Captured piece handling | Sort captured pieces into trays | Motion planning |
| Multi-board fleet | Multiple chess stations, centralized tournaments | Fleet management |
| Opening book training | Learn from games played, improve openings | ML, data pipelines |

### Stretch Goals

- [ ] Play other games (checkers, Go with different board)
- [ ] Spectator mode with live streaming
- [ ] Integration with chess.com or Lichess for ratings
- [ ] Robot vs robot matches

### Hardware Options

| Component | Options |
|-----------|---------|
| Arm | xArm 6, xArm 5 Lite |
| Gripper | Small parallel jaw, magnetic gripper, vacuum |
| Camera | Overhead mounted, Intel RealSense |
| Board | Standard board with detectable pieces, custom pieces |

### Viam Capabilities Exercised

- [ ] Arm control & motion planning
- [ ] Vision (piece detection, board state)
- [ ] ML inference (piece classification)
- [ ] Remote operation
- [ ] Data capture (game history)
- [ ] Module development (chess service)

---

## 3. Greenhouse

**Concept:** Automated growing environment with sensing, control, and optional harvesting.

### MVP Options (Pick One)

| Option | Description | Complexity | Demo Appeal |
|--------|-------------|------------|-------------|
| **A. Monitor + dashboard** | Sensors track temp/humidity/soil moisture, display on web dashboard | Low | Medium |
| **B. Monitor + auto-water** | Above plus automated watering based on soil moisture thresholds | Low-Medium | Medium-High |
| **C. Monitor + water + lights** | Full environment control including grow lights on schedule | Medium | High |
| **D. Single plant pod** | Small self-contained unit (like AeroGarden) with full monitoring | Low-Medium | High |

### Post-Hackathon Backlog Options

| Option | Description | Viam Capabilities |
|--------|-------------|-------------------|
| Multi-zone control | Different settings for different plant types | Configuration, fragments |
| Ripeness detection | ML model detects when produce is ready to harvest | ML inference, vision |
| Growth time-lapse | Capture images on schedule, compile into video | Data capture, cloud sync |
| Alerting | Notify when conditions out of range or harvest ready | Alerting, data triggers |
| Historical analysis | Track growth rates, correlate with conditions | Data pipelines |
| Recipe management | Saved profiles for different crops | Fragments, configuration |
| Multi-station fleet | Multiple grow stations with centralized monitoring | Fleet management |
| Yield tracking | Track harvests over time, optimize for yield | Data management |

### Stretch Goals

- [ ] Harvesting arm on gantry (complex)
- [ ] Seed planting automation
- [ ] Pest detection via vision
- [ ] Integration with weather API for outdoor greenhouses
- [ ] Produce delivery handoff to mobile robot

### Hardware Options

| Component | Options |
|-----------|---------|
| Sensors | DHT22 (temp/humidity), soil moisture, light sensor, pH sensor |
| Actuators | Relay-controlled pump, solenoid valve, grow lights, fans |
| Camera | USB camera for time-lapse/monitoring, or RPi camera |
| Compute | Raspberry Pi 4, Jetson Nano (if ML needed) |
| Enclosure | IKEA greenhouse cabinet, custom build, commercial grow tent |

### Viam Capabilities Exercised

- [ ] Sensor data capture
- [ ] Cloud sync with offline buffering
- [ ] Remote monitoring
- [ ] Alerting/triggers
- [ ] ML inference (ripeness)
- [ ] Fleet management (multi-station)
- [ ] Fragments (environment recipes)
- [ ] Data visualization

---

## 4. Box Bot

**Concept:** Stationary robot that breaks down cardboard boxes for recycling.

### MVP Options (Pick One)

| Option | Description | Complexity | Demo Appeal |
|--------|-------------|------------|-------------|
| **A. Flatten only** | Detect box, grab it, flatten it, place in pile | Medium | High |
| **B. Flatten + stack** | Flatten boxes and stack neatly by size | Medium-High | High |
| **C. Flatten + bind** | Flatten, stack, and bundle with twine/tape | High | Very High |
| **D. Sort + flatten** | Detect box size/type, sort into categories, then flatten | Medium-High | High |

### Post-Hackathon Backlog Options

| Option | Description | Viam Capabilities |
|--------|-------------|-------------------|
| Box counting | Track boxes processed per day/week | Data capture |
| Size classification | ML model classifies box sizes | ML inference |
| Recycling metrics | Dashboard showing recycling impact | Data visualization |
| Jam detection | Detect and alert when mechanism jams | Vision, alerting |
| Multi-material sorting | Separate cardboard from other recyclables | Vision, ML |
| Scheduled operation | Run during off-hours to reduce noise | Scheduling |
| Remote monitoring | Check status and metrics from anywhere | Remote operation |
| Restock mode | Unpack boxes to restock kitchen supplies | Different workflow |

### Stretch Goals

- [ ] Automatic bin full detection and alerting
- [ ] Integration with recycling pickup schedule
- [ ] Compactor integration for volume reduction
- [ ] QR code scanning for supply tracking (restock mode)

### Hardware Options

| Component | Options |
|-----------|---------|
| Arm | xArm 6, or custom mechanism for flattening |
| Gripper | Wide parallel jaw, vacuum pads |
| Camera | Overhead for box detection |
| Mount | Wall-mounted, table-mounted, or freestanding station |
| Flattening mechanism | Arm pressure, dedicated roller, or hydraulic press |

### Viam Capabilities Exercised

- [ ] Vision (box detection)
- [ ] Arm control & motion planning
- [ ] ML inference (size classification)
- [ ] Data capture (metrics)
- [ ] Remote monitoring
- [ ] Alerting

---

## 5. Dishwasher Robot

**Concept:** Robot that unloads (and potentially loads) a dishwasher.

### MVP Options (Pick One)

| Option | Description | Complexity | Demo Appeal |
|--------|-------------|------------|-------------|
| **A. Single dish type** | Unload plates only, place in single cabinet location | Medium | High |
| **B. Multiple dish types** | Detect and handle plates, bowls, cups - different destinations | High | Very High |
| **C. Utensil sorting** | Focus on utensil basket - sort into drawer organizer | Medium | High |
| **D. Rack extraction** | Pull dishwasher rack out, enabling easier access for unloading | Low-Medium | Medium |

### Post-Hackathon Backlog Options

| Option | Description | Viam Capabilities |
|--------|-------------|-------------------|
| Dish classification | ML model identifies dish types | ML inference |
| Cabinet mapping | Learn cabinet locations for different items | Configuration |
| Dishwasher loading | Reverse workflow - load from sink | Motion planning |
| Sink handoff | Receive dishes from cleaning cart robot | Multi-robot coordination |
| Clean detection | Verify dishes are clean before unloading | Vision |
| Cycle completion trigger | Start unloading when dishwasher cycle ends | Integration, triggers |
| Breakage detection | Detect and alert on cracked/chipped dishes | Vision, ML |
| Inventory tracking | Track dish counts, alert on low supplies | Data management |

### Stretch Goals

- [ ] Full kitchen integration (sink → dishwasher → cabinet)
- [ ] Handle fragile items (wine glasses)
- [ ] Pot and pan handling (larger manipulation)
- [ ] Detergent level monitoring and reorder alerts

### Hardware Options

| Component | Options |
|-----------|---------|
| Arm | xArm 6, dual arms for efficiency |
| Gripper | Parallel jaw, soft gripper for fragile items |
| Gantry | Overhead rail for extended reach (post-MVP) |
| Camera | Overhead + side view for dish detection |
| Mounting | Counter-mounted, ceiling-mounted gantry |

### Viam Capabilities Exercised

- [ ] Arm control & motion planning
- [ ] Vision (dish detection, pose estimation)
- [ ] ML inference (dish classification)
- [ ] Configuration management (cabinet positions)
- [ ] Multi-robot coordination (if integrated with other robots)
- [ ] Triggers/scheduling

---

## 6. Cleaning Cart

**Concept:** Mobile robot that collects dishes, cups, and trash from around the office.

### MVP Options (Pick One)

| Option | Description | Complexity | Demo Appeal |
|--------|-------------|------------|-------------|
| **A. Patrol + detect** | Navigate office, detect and report dish/trash locations | Medium | High |
| **B. Patrol + alert** | Above plus alert humans to collect items | Medium | Medium-High |
| **C. Patrol + collect (simple)** | Navigate to known stations, wait for humans to load items | Medium | High |
| **D. Full collection** | Navigate, detect, pick up items autonomously | Very High | Very High |

### Post-Hackathon Backlog Options

| Option | Description | Viam Capabilities |
|--------|-------------|-------------------|
| Desk mapping | Learn office layout, desk locations | SLAM, navigation |
| Item classification | ML distinguishes cups vs plates vs trash | ML inference |
| Route optimization | Efficient patrol routes based on historical data | Data analysis |
| Trash disposal | Navigate to and deposit trash in bin | Navigation, manipulation |
| Dishwasher handoff | Coordinate with dishwasher robot for unloading | Multi-robot, fleet |
| Schedule patrols | Run collection routes at set times | Scheduling |
| Obstacle avoidance | Handle dynamic obstacles (people, chairs) | Navigation |
| Battery management | Return to charge station, resume patrol | Autonomous operation |

### Stretch Goals

- [ ] Voice interaction ("I have dishes for you")
- [ ] Elevator integration for multi-floor operation
- [ ] Spill detection and alerting
- [ ] Integration with calendar (collect after meetings)

### Hardware Options

| Component | Options |
|-----------|---------|
| Base | Create 3, Husarion ROSbot, custom wheeled base |
| Arm | Small arm for collection (xArm Lite), or tray-only |
| Gripper | Parallel jaw, tray carrier |
| Sensors | Lidar (RPLidar, Velodyne), depth camera |
| Camera | RealSense for item detection |
| Tray/bin | Mounted collection bins for dishes, trash |

### Viam Capabilities Exercised

- [ ] Navigation & SLAM
- [ ] Vision (item detection)
- [ ] ML inference (classification)
- [ ] Fleet management (coordination)
- [ ] Data capture (patrol logs)
- [ ] Remote monitoring
- [ ] Scheduling/triggers

---

## Summary: Recommended MVP Combinations

| Project | Recommended MVP | Rationale |
|---------|-----------------|-----------|
| Vino | A or B (Pour on demand / Glass detection) | Core demo value, achievable in 3 days |
| Chess | A (Full game play) if existing, else B | Build on existing work |
| Greenhouse | B (Monitor + auto-water) | Shows data + actuation, achievable scope |
| Box Bot | A (Flatten only) | Clear deliverable, complex enough to learn |
| Dishwasher | A (Single dish type) | Proves the concept, expandable |
| Cleaning Cart | A (Patrol + detect) | Navigation + vision without manipulation complexity |

---

## Decision Template

For each project, select:

**Vino:**
- MVP Option: ___
- Backlog items (pick 3-5): ___
- Hardware: ___

**Chess:**
- MVP Option: ___
- Backlog items (pick 3-5): ___
- Hardware: ___

**Greenhouse:**
- MVP Option: ___
- Backlog items (pick 3-5): ___
- Hardware: ___

**Box Bot:**
- MVP Option: ___
- Backlog items (pick 3-5): ___
- Hardware: ___

**Dishwasher:**
- MVP Option: ___
- Backlog items (pick 3-5): ___
- Hardware: ___

**Cleaning Cart:**
- MVP Option: ___
- Backlog items (pick 3-5): ___
- Hardware: ___
