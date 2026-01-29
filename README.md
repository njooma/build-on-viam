# Build on Viam

**Get every Viam engineer building on Viam**
 
## Program Goals

### 1. Team Enablement

Equip every engineering team with the knowledge, tools, and confidence to build effectively on the Viam platform.

**Success looks like:**
- Every engineer has completed at least one project on the platform
- Teams can independently start and complete projects without external support
- Engineers can articulate Viam's core value propositions

### 2. Individual & Team Ownership

Foster a culture where engineers feel personal ownership over the platform's success and quality.

**Success looks like:**
- Engineers proactively identify and report platform issues
- Engineers contribute fixes and improvements beyond their assigned tasks
- Increased participation in platform discussions and design reviews

### 3. Platform Quality

Improve platform quality through direct, hands-on experience building real applications.

**Success looks like:**
- Decrease in customer-reported bugs
- Increase in internally-discovered issues before release
- Documentation improvements driven by real usage

---

## Program Structure

### 1. Application Development

6-8 well-defined robotics applications to be developed (from scratch or continued from existing projects):

- Each application will be highly visible
- Together they will demonstrate the depth and breadth of Viam's capabilities
- Initial applications defined up front as prominent examples
- Additional projects solicited via submission template and established guidelines
- Each application has a defined backlog tracked in Jira
- Some backlog items will be documentation

**Requirement:** Every engineer must join an application team.

### 2. Hackathon Kickoff

- **Date:** February 2026
- **Duration:** 3-day hackathon
- **Culmination:** Demos and awards

### 3. Ongoing Ownership & Accountability

- **Bi-weekly demos** with kudos and backlog burndown celebrations
- **Designated triage sessions** where app teams present their top blockers
- Focus on creating a remarkably positive experience with the platform

### 4. Quarterly Retrospective

- What did our internal building experiences teach us?
- What did we fix because of them?
- What do we need to do to make Viam an exciting and powerful product experience?

### 5. Education

Ad hoc tutorial enablement sessions on:
- Robotics fundamentals
- Use of AI
- Viam platform capabilities
- Emerging best practices

---

## Scorecard Metrics

### Prior to Kickoff (Feb 10)
- Progress reports on rollout prep
- Defining project backlogs
- Completing builds
- Hackathon logistics prep

### Mar 1 Target
- 70% of individuals have continued their hackathon project

### Ongoing (After Kickoff)
- Team & individual activity in the prior 14 days
- Application backlog items delivered
- Jira issues opened/closed on platform bugs & enhancements emerging from builds

---

## Documentation

### For Engineers Building Projects

| Document | Description |
|----------|-------------|
| [Team Development Guide](docs/team-development-guide.md) | **Start here.** Two-layer configuration architecture (hardware fragment + application layer), CLI development pattern for rapid iteration, project structure, multi-developer workflow, and best practices for building on Viam. Based on the [viam-chess](https://github.com/erh/viam-chess) reference implementation. |
| [Submission Guidelines](docs/submission-guidelines.md) | How to propose a new project for the program. Includes deadline (Feb 13), evaluation criteria summary, requirements, and tips for strong proposals. |
| [Project Template](templates/project-template.md) | Template for defining new projects. Includes sections for MVP options, hardware requirements, backlog items organized by feature category, and success criteria. |

### For Program Leads & Evaluators

| Document | Description |
|----------|-------------|
| [Project Planning Guide](docs/project-planning-guide.md) | Strategic guide for project selection and portfolio management. Covers Viam capability coverage analysis, feature gap methodology, configuration architecture rationale, and the full assessment criteria with scoring rubrics (1-5 scale across 6 dimensions). Use this when evaluating proposals or assessing portfolio balance. |

### Projects

| Document | Description |
|----------|-------------|
| [Projects Overview](projects/) | Index of all active projects with capability matrix showing which Viam features each project demonstrates. Includes comparison scores and next steps checklist. |
| Individual project files | Each project (Vino, Chess, Greenhouse, Box-bot, Dishwasher, Cleaning Cart, Barista) has its own file with description, MVP options, hardware requirements, backlog, and success criteria. |

---

## Quick Links

**I want to...**

| Goal | Go to |
|------|-------|
| Join a project team | [Projects Overview](projects/) |
| Propose a new project | [Submission Guidelines](docs/submission-guidelines.md) → [Project Template](templates/project-template.md) |
| Learn how to build on shared hardware | [Team Development Guide](docs/team-development-guide.md) |
| Evaluate a project proposal | [Project Planning Guide](docs/project-planning-guide.md#project-assessment-criteria) |
| Understand which Viam features we're demonstrating | [Project Planning Guide](docs/project-planning-guide.md#current-feature-coverage) |

---

## Open Questions

1. Should consumer/home-automation applications be part of our strategy?
   - How do we incorporate remote engineers?
   - How do we address Viam's scale-to-fleet, fleet maintenance, and batteries-included capabilities?
2. Should we require all engineers to participate in user tests as part of this initiative?

---

## Directory Structure

```
build-on-viam/
├── README.md                 # This file - program overview and navigation
├── docs/
│   ├── team-development-guide.md    # How to build (architecture, workflow, best practices)
│   ├── project-planning-guide.md    # Strategic planning (feature gaps, assessment criteria)
│   └── submission-guidelines.md     # How to propose projects
├── projects/
│   ├── README.md             # Project index and capability matrix
│   ├── barista.md            # Robotic coffee station
│   ├── box-bot.md            # Cardboard box flattener
│   ├── chess.md              # Chess-playing robot
│   ├── cleaning-cart.md      # Mobile dish collection
│   ├── dishwasher.md         # Dishwasher unloading robot
│   ├── greenhouse.md         # Automated growing environment
│   └── vino.md               # Wine service robot
├── templates/
│   └── project-template.md   # Template for new project proposals
└── archive/                  # Historical working documents
```
