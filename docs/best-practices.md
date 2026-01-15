# Best Practices for Building on Viam

This guide captures best practices for teams participating in the Build on Viam program.

## Getting Started

### 1. Set Up Your Development Environment

- Install the Viam CLI: `brew install viam`
- Set up your Viam organization and create a machine
- Clone your project repository
- Verify connectivity to your hardware (if applicable)

### 2. Understand the Architecture

Before writing code:
- Review [Viam's architecture documentation](https://docs.viam.com/architecture/)
- Understand the relationship between machines, components, and services
- Familiarize yourself with the SDK you'll be using (Python, Go, TypeScript)

### 3. Start Simple

- Get a basic "hello world" working first
- Verify each component works individually before integrating
- Use the Viam app to test components before writing code

## Development Practices

### Use Configuration Over Code

Prefer configuring components in the Viam app over hardcoding in your application:

**Good:**
```json
// Configure in Viam app, reference by name in code
camera = robot.get_component("my-camera")
```

**Avoid:**
```python
# Hardcoding configuration in application code
camera = Camera(port="/dev/video0", resolution=(640, 480))
```

### Leverage Modular Resources

When existing components don't meet your needs:
- Check if a community module exists first
- Build a modular resource rather than forking core code
- Share your modules with the team

### Handle Disconnections Gracefully

Robots operate in the real world. Your code should handle:
- Network interruptions
- Hardware failures
- Sensor noise and invalid readings

```python
try:
    reading = await sensor.get_readings()
except Exception as e:
    logger.warning(f"Sensor read failed: {e}")
    # Implement fallback behavior
```

### Use Data Management

- Log sensor data to Viam's data management for debugging
- Use data capture for ML training datasets
- Review logs when debugging issues

## Team Collaboration

### Daily Standups

During the hackathon and ongoing:
- Share what you accomplished
- Identify blockers early
- Coordinate on shared resources (hardware, machines)

### Document As You Go

Don't leave documentation for the end:
- Update README as you make progress
- Record short demo videos of milestones
- Note any gotchas or non-obvious solutions

### Report Issues

When you hit platform issues:
1. Document the issue clearly (steps to reproduce, expected vs actual)
2. File a Jira ticket
3. Bring critical blockers to triage sessions

This is one of the program's primary value propositions - finding and fixing issues.

## Demo Best Practices

### Preparing for Demos

- Test your demo multiple times before presenting
- Have a backup plan if hardware fails
- Record a video backup of the demo working

### During the Demo

- Start with context: what problem does this solve?
- Show the working application, not just slides
- Highlight which Viam capabilities you used
- Be honest about challenges and learnings

### After the Demo

- Share your code and configuration
- Document lessons learned
- Update your project backlog based on feedback

## Common Pitfalls

### Pitfall 1: Scope Creep

**Problem:** Adding features before MVP is complete
**Solution:** Ruthlessly prioritize. Get something working first, then iterate.

### Pitfall 2: Hardware Tunnel Vision

**Problem:** Spending all time on hardware issues, not building the application
**Solution:** Use simulation or existing working hardware when possible. Ask for help early.

### Pitfall 3: Working in Isolation

**Problem:** Not sharing progress or blockers
**Solution:** Post updates in your team channel. Attend standups. Ask questions.

### Pitfall 4: Not Using Platform Features

**Problem:** Building custom solutions for things Viam already provides
**Solution:** Review documentation. Ask if there's a built-in way to do something.

## Resources

- [Viam Documentation](https://docs.viam.com/)
- [SDK References](https://docs.viam.com/sdks/)
- [Example Projects](https://docs.viam.com/tutorials/)
- Internal Slack: #build-on-viam
