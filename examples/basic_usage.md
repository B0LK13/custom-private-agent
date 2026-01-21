# Example: Basic Agent Usage

> **Note**: This is a placeholder example. It will be updated once the core functionality is implemented.

## Simple Task Execution

```python
# Example of how the agent might be used (Python)
from custom_agent import Agent

# Initialize the agent
agent = Agent(config_file="config.yaml")

# Execute a simple task
result = agent.execute_task(
    task_type="automation",
    parameters={
        "action": "send_notification",
        "message": "Hello from custom-private-agent!"
    }
)

print(f"Task result: {result}")
```

## Using Plugins

```python
# Example of using a plugin
from custom_agent import Agent
from custom_agent.plugins import WeatherPlugin

# Initialize agent with plugins
agent = Agent()
agent.register_plugin(WeatherPlugin(api_key="your_api_key"))

# Use the plugin
weather = agent.execute_task(
    task_type="weather",
    parameters={
        "location": "San Francisco"
    }
)

print(f"Current weather: {weather}")
```

## Scheduled Tasks

```python
# Example of scheduling tasks
from custom_agent import Agent, Scheduler

agent = Agent()
scheduler = Scheduler(agent)

# Schedule a daily task
scheduler.add_task(
    name="daily_backup",
    task_type="backup",
    schedule="daily",
    time="02:00",
    parameters={
        "source": "/data",
        "destination": "/backups"
    }
)

# Start the scheduler
scheduler.start()
```

## CLI Usage

```bash
# Example CLI commands (hypothetical)

# Initialize configuration
custom-agent init

# Run a task
custom-agent run --task automation --param action=test

# List available plugins
custom-agent plugins list

# Install a plugin
custom-agent plugins install weather-plugin

# Start in daemon mode
custom-agent daemon start

# Check status
custom-agent status
```

## Configuration Example

```yaml
# config.yaml
agent:
  name: "My Personal Agent"
  log_level: "INFO"
  
plugins:
  - name: "weather"
    enabled: true
    config:
      api_key: "${WEATHER_API_KEY}"
      
  - name: "email"
    enabled: true
    config:
      smtp_host: "smtp.example.com"
      smtp_port: 587
      
tasks:
  - name: "morning_briefing"
    schedule: "0 8 * * *"  # Daily at 8 AM
    actions:
      - type: "weather"
        params:
          location: "home"
      - type: "email"
        params:
          subject: "Daily Briefing"
```

## Advanced Example: Custom Workflow

```python
# Example of creating a custom workflow
from custom_agent import Agent, Workflow

agent = Agent()

# Define a workflow
workflow = Workflow("data_processing")

# Add workflow steps
workflow.add_step(
    name="fetch_data",
    task_type="api_call",
    parameters={"endpoint": "https://api.example.com/data"}
)

workflow.add_step(
    name="process_data",
    task_type="transform",
    parameters={"format": "json"}
)

workflow.add_step(
    name="store_data",
    task_type="database",
    parameters={"table": "processed_data"}
)

# Execute workflow
result = agent.execute_workflow(workflow)

print(f"Workflow completed: {result}")
```

## Error Handling Example

```python
# Example of error handling
from custom_agent import Agent, AgentException

agent = Agent()

try:
    result = agent.execute_task(
        task_type="risky_operation",
        parameters={"data": "sensitive"}
    )
except AgentException as e:
    print(f"Agent error: {e}")
    # Handle error appropriately
except Exception as e:
    print(f"Unexpected error: {e}")
    # Log and report
```

---

**Note**: These examples are illustrative and will be updated as the actual implementation progresses. The API design may change based on development decisions.
