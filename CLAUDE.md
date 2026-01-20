# Copilot Studio News Agent Lab

## Project Overview

A self-service lab teaching how to build an autonomous agent in Microsoft Copilot Studio that:
- Runs on a schedule (Recurring Copilot Trigger)
- Searches the web for news on specified topics
- Compiles results into an HTML newsletter
- Sends the report via email

## Image Inventory

| Image | Description | Used In |
|-------|-------------|---------|
| `agent-overview.png` | Completed agent showing all components: name (HR News Agent), model (GPT-5 Chat), trigger, instructions, web search enabled, email tool | Introduction/final state |
| `add-trigger-recurrence.png` | "Add trigger" dialog with trigger type options; Recurrence highlighted among options like "When an item is created", "When a file is created", etc. | Step 1 |
| `sign-in-trigger-recurrence.png` | Sign-in step for Recurring Copilot Trigger; shows Microsoft Copilot Studio connection with sign-in button | Step 1 |
| `create-trigger-recurrence.png` | Trigger configuration form with fields: Trigger name, Trigger frequency | Step 1 |
| `add-tool.png` | Tools page showing "Send an email (V2)" listed as a connector, available to HR News Agent, triggered by agent, with enabled toggle | Step 2 |
| `tool-definition-email-to.png` | Email tool input configuration for "To" field; shows "Dynamically fill with AI" option and description "send to myself" | Step 2 |
| `tool-definition-email-body.png` | Email tool input configuration for "Body" field; "Dynamically fill with AI" with description "An HTML formatted report of relevant news, including links. Design the report like a visually appealing newsletter" | Step 2 |
| `add-tools-to-instructions.png` | Instructions editor showing `/` tool picker dropdown with available tools and knowledge sources | Step 3 |
| `select-email-tool.png` | Tool picker with "Send an email (V2)" selected from the dropdown | Step 3 |
| `click-test-trigger.png` | Agent overview showing the Recurring Copilot Trigger in the Triggers section | Step 4 |
| `start-testing.png` | "Test your trigger" dialog with date/time schedule and "Start testing" button | Step 4 |
| `activity-map.png` | Activity map showing execution flow: multiple "Search sources" (Knowledge) steps followed by "Send an email (V2)"; right panel shows completed email with HTML body | Step 4 (testing) |
| `email-report.png` | Example email received: "Gaming News Report" with formatted HTML sections for AAA Games, Simulation Games, Farming Games with links | Step 4 (result) |

## Lab Structure (Simplified)

Single flow, no separate use cases. Steps:

1. **Configure the Recurring Copilot Trigger**
   - Add trigger → select Recurrence
   - Sign in to Microsoft Copilot Studio
   - Configure: name, frequency

2. **Add and Configure the Email Tool**
   - Add tool → Send an email (V2) connector
   - Configure "To" input: Dynamically fill with AI, description "send to myself"
   - Configure "Subject" input: Dynamically fill with AI
   - Configure "Body" input: Dynamically fill with AI, description for HTML newsletter format

3. **Write Agent Instructions**
   - Enable Web Search in Knowledge
   - Write instructions that:
     - Define the news topics to search
     - Reference the email tool for sending the report
   - Example: "When triggered, search the web for news on the following subjects: [topics]. Once you have the results, compile and send a report using Send an email (V2)"

4. **Test and Verify**
   - Use test panel to trigger the agent
   - Review activity map to see search → email flow
   - Verify email is sent with formatted newsletter

## Key Configurations Observed

### Agent Settings
- **Model**: GPT-5 Chat
- **Web Search**: Enabled

### Trigger Settings
- **Type**: Recurring Copilot Trigger

### Email Tool Inputs
- **To**: Dynamically filled, "send to myself"
- **Subject**: Dynamically filled
- **Body**: Dynamically filled, "An HTML formatted report of relevant news, including links. Design the report like a visually appealing newsletter"

### Sample Instructions
```
When triggered, search the web for news on the following subjects:
The role of HR in the age of Gen AI, how AI assistants impact the dev role, the frontier organization

Once you have the results, compile and send a report using Send an email (V2)
```

## Important Notes

- The Recurring Copilot Trigger requires signing in to Microsoft Copilot Studio
- Email tool inputs use "Dynamically fill with AI" so the agent decides the values based on instructions
- The activity map shows the agent's execution path: Knowledge searches → Email send
