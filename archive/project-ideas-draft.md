# Project Ideas - Draft Assessment

Initial assessment of proposed Build on Viam projects against [assessment criteria](../docs/project-assessment-criteria.md).

---

## 1. Vino

**Status:** Existing project with backlog

**Description:** [To be filled from existing backlog]

**Assessment:** Needs backlog review to score against criteria.

**Action:** Review existing backlog and map to assessment criteria.

---

## 2. Chess

**Status:** Existing project with backlog

**Description:** [To be filled from existing backlog]

**Assessment:** Needs backlog review to score against criteria.

**Action:** Review existing backlog and map to assessment criteria.

---

## 3. Dishwasher Robot

**Description:** Robot that unloads dishwasher using arm(s) mounted on gantry. Extended scope includes loading dishwasher from sink.

### Initial Assessment

| Criterion | Score | Notes |
|-----------|-------|-------|
| Platform Capability Coverage | 4 | Motion planning, vision for dish detection, potentially data capture for dish types. Could add remote monitoring. |
| Lifecycle Stage Coverage | 3 | MVP is Stage 1-2. Could extend to "fleet" of kitchen robots with shared config. |
| Problem-Platform Fit | 4 | Arm control, vision, motion planning are solid Viam capabilities. |
| Feasibility & Scope | 3 | Gantry + arm is complex. MVP scope needs careful definition. |
| Learning & Quality Impact | 4 | Exercises motion planning, vision services, manipulation. |
| Cool Factor & Practical Utility | 5 | **Very cool and genuinely useful.** Everyone hates unloading the dishwasher. High demo appeal. |

**Estimated Score: 3.8**

### Strengths
- High cool factor - relatable problem everyone understands
- Practical utility in the office
- Good platform exercise (arm, vision, motion planning)

### Concerns
- Gantry adds mechanical complexity
- MVP scope may be ambitious for 3-day hackathon
- Dish handling requires careful gripper design

### Recommendations
- Define minimal MVP: pick up one dish type, place in cabinet
- Consider arm-only MVP (no gantry) to reduce complexity
- Gantry + sink loading as post-hackathon backlog

---

## 4. Box Bot

**Description:** Stationed robot that breaks down, stacks, and binds cardboard boxes for recycling. Also unloads boxes to restock kitchen stores. People drop boxes in front of it.

### Initial Assessment

| Criterion | Score | Notes |
|-----------|-------|-------|
| Platform Capability Coverage | 4 | Vision for box detection, arm manipulation, potentially data capture for recycling metrics. |
| Lifecycle Stage Coverage | 3 | Stationary deployment is Stage 2. Could track box volumes over time (Stage 5 data). |
| Problem-Platform Fit | 4 | Vision + manipulation is core Viam strength. |
| Feasibility & Scope | 4 | Stationary mount simplifies things. Box breakdown is well-defined task. |
| Learning & Quality Impact | 4 | Good manipulation challenge, vision detection of varying box sizes. |
| Cool Factor & Practical Utility | 5 | **Solves real office annoyance.** Visible location means high engagement. |

**Estimated Score: 4.0**

### Strengths
- Stationary mount reduces complexity vs. mobile solutions
- Clear, bounded problem (boxes in → flat cardboard out)
- High visibility location drives engagement
- Solves actual office problem (Andrea's suggestion adds validation)

### Concerns
- Box breakdown mechanics need design
- Variety of box sizes/types
- Binding mechanism adds complexity

### Recommendations
- MVP: Detect box, flatten it, stack it (no binding)
- Binding as post-hackathon enhancement
- Track metrics: boxes processed per day, sizes, etc.

---

## 5. Greenhouse

**Description:** Environmental sensing and control for greenhouse. Manages temperature, humidity, watering, light. Small arms on gantries harvest vegetables when ready. Alerting as needed.

### Initial Assessment

| Criterion | Score | Notes |
|-----------|-------|-------|
| Platform Capability Coverage | 5 | Data capture (sensors), remote monitoring, alerting, ML (ripeness detection), fleet potential (multiple grow stations). |
| Lifecycle Stage Coverage | 5 | Natural progression: single station → multiple stations → fleet management. Data pipelines for growth tracking. |
| Problem-Platform Fit | 5 | Sensor data, cloud sync, remote monitoring, ML inference - all Viam strengths. |
| Feasibility & Scope | 3 | Gantry arms for harvesting is complex. Environmental sensing alone is more achievable. |
| Learning & Quality Impact | 5 | Exercises data services, ML, alerting, potentially fleet management. |
| Cool Factor & Practical Utility | 5 | **Growing food with robots is inherently cool.** Fresh vegetables in office. Time-lapse potential. |

**Estimated Score: 4.6**

### Strengths
- Excellent platform coverage (sensors, data, ML, fleet)
- Natural multi-stage lifecycle progression
- High cool factor with tangible output (actual vegetables)
- Remote-friendly: sensors can be monitored from anywhere
- Time-lapse and growth data creates compelling content

### Concerns
- Harvesting arms add significant complexity
- Greenhouse infrastructure needed
- Plant growth timeline extends beyond hackathon

### Recommendations
- MVP: Environmental monitoring + automated watering + data dashboard
- Ripeness detection as post-hackathon ML project
- Harvesting arms as stretch goal
- Consider starting with herbs (faster growth cycle)

---

## 6. Cleaning Cart

**Description:** Mobile cart that drives around office collecting cups, glasses, dishes, and garbage from desks. Disposes of trash. Loads dishes into sink (handoff to dishwasher robot).

### Initial Assessment

| Criterion | Score | Notes |
|-----------|-------|-------|
| Platform Capability Coverage | 5 | Navigation, vision, manipulation, multi-robot coordination (handoff to dishwasher). |
| Lifecycle Stage Coverage | 4 | Mobile deployment is Stage 2. Multi-robot is Stage 3+. |
| Problem-Platform Fit | 4 | Navigation + vision + manipulation - all Viam capabilities. Real-time coordination is harder. |
| Feasibility & Scope | 2 | Mobile + manipulation + navigation + multi-robot is very ambitious. |
| Learning & Quality Impact | 5 | Exercises nearly every platform capability. |
| Cool Factor & Practical Utility | 5 | **Extremely cool.** Robot butler collecting dishes. Very useful if it works. |

**Estimated Score: 4.0 (but high risk)**

### Strengths
- Maximum cool factor - robot butler is universally appealing
- Exercises full platform capabilities
- Multi-robot handoff demonstrates fleet coordination
- Genuinely useful in office environment

### Concerns
- **Scope is very ambitious** for hackathon
- Mobile manipulation is challenging
- Navigation in cluttered office environment
- Multi-robot coordination adds complexity

### Recommendations
- Consider splitting into phases:
  - Phase 1 (Hackathon): Mobile patrol that identifies dishes but doesn't collect
  - Phase 2: Add collection capability
  - Phase 3: Add dishwasher handoff
- Or: Start with stationary collection point (people bring dishes to cart)

---

## 7. Home Automation

**Status:** TBD

**Notes:** This could address the open question about remote engineer participation and consumer/home applications. Needs definition.

### Potential Directions
- Smart home integration with Viam (lights, HVAC, security)
- Home robot assistant
- Pet feeder/monitor
- Package delivery notification

### Assessment
Cannot score until defined. Could be valuable for:
- Remote engineer participation (everyone has a home)
- Demonstrating Viam beyond industrial robotics
- Fleet concepts (multiple homes)

**Action:** Define specific project scope before assessment.

---

## Summary Comparison

| Project | Platform | Lifecycle | Fit | Feasibility | Learning | Cool/Useful | **Total** |
|---------|----------|-----------|-----|-------------|----------|-------------|-----------|
| Greenhouse | 5 | 5 | 5 | 3 | 5 | 5 | **4.6** |
| Box Bot | 4 | 3 | 4 | 4 | 4 | 5 | **4.0** |
| Cleaning Cart | 5 | 4 | 4 | 2 | 5 | 5 | **4.0** |
| Dishwasher | 4 | 3 | 4 | 3 | 4 | 5 | **3.8** |
| Vino | ? | ? | ? | ? | ? | ? | **TBD** |
| Chess | ? | ? | ? | ? | ? | ? | **TBD** |
| Home Automation | ? | ? | ? | ? | ? | ? | **TBD** |

### Top Recommendations

1. **Greenhouse** - Highest score, excellent platform coverage, manageable MVP, remote-friendly
2. **Box Bot** - Strong score, well-scoped, high visibility, solves real problem
3. **Cleaning Cart** - Very cool but needs scope reduction for feasibility
4. **Dishwasher** - Cool and useful, needs careful MVP scoping

### Next Steps

1. Review Vino and Chess backlogs for scoring
2. Define Home Automation scope
3. Refine MVP definitions for top projects
4. Assess hardware availability for each
