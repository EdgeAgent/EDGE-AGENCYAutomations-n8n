# Complete SDR Lead Capture & Qualification Agent

This n8n workflow provides a comprehensive solution for capturing, qualifying, and routing sales leads from multiple channels. It uses AI to instantly qualify leads, categorizing them as hot, warm, or cold, and then automates appropriate follow-up actions, including booking calls, sending nurture emails, and notifying sales teams.

## Features

*   **Multi-Channel Lead Capture**: Receives leads from various sources (website forms, WhatsApp, email, LinkedIn, chat widgets) via a single webhook.
*   **Instant Lead Response**: Provides an immediate automated response to new leads.
*   **Airtable CRM Integration**: Stores and updates lead information in an Airtable CRM.
*   **AI Lead Qualification**: Utilizes an AI agent (e.g., GPT-4) to analyze lead quality, urgency, and fit, assigning a qualification score and determining the next best action.
*   **Dynamic Lead Routing**: Routes leads based on their qualification score:
    *   **Hot Leads**: Automatically books a discovery call via Cal.com, sends a confirmation email, and notifies the sales team via Slack.
    *   **Warm Leads**: Initiates a nurture email sequence and notifies the sales team.
    *   **Cold Leads**: Archives the lead for long-term nurturing.
*   **Automated Follow-up**: Manages email and Slack notifications for different lead stages.

## How it Works

1.  **Multi-Channel Lead Webhook**: The workflow is triggered when a new lead is received via a webhook.
2.  **Instant Response to Lead**: An immediate text response is sent back to the lead.
3.  **Store Lead in Airtable CRM**: The new lead's information is stored in Airtable.
4.  **AI Lead Qualification Agent**: An AI model analyzes the lead's details to determine its quality, urgency, and fit, providing a qualification score and a recommended next action.
5.  **Parse AI Analysis**: Extracts structured data from the AI's response.
6.  **Update Lead with AI Insights**: The Airtable lead record is updated with the AI's qualification insights.
7.  **Route by Qualification Score**: A switch node directs the workflow based on the lead's qualification score (Hot, Warm, Cold).
    *   **Hot Lead Path**: Books a discovery call, updates the lead status, sends a confirmation email, and notifies the sales team via Slack.
    *   **Warm Lead Path**: Initiates an email nurture sequence, updates the lead status, and notifies the sales team.
    *   **Cold Lead Path**: Archives the lead for long-term nurturing.

## Setup Instructions

1.  **n8n Instance**: Ensure you have a running n8n instance.
2.  **Credentials**: Configure credentials for:
    *   Airtable API
    *   OpenAI API (for AI Lead Qualification Agent)
    *   Cal.com API (for booking calls)
    *   Email Sending Service (e.g., SendGrid)
    *   Slack API
3.  **Airtable Base**: Set up an Airtable base with a 

Leads table, including fields for name, email, phone, company, message, source, AI-generated tier, urgency, score, next action, and reasoning.
4.  **Workflow Import**: Import the provided `.json` workflow file into your n8n instance.
5.  **Configuration**: Adjust webhook URLs, Airtable base/table IDs, Cal.com event IDs, email templates, and Slack channel IDs as needed. Ensure the AI prompt in the `AI Lead Qualification Agent` node is tailored to your specific qualification criteria.

## Workflow File

[Complete_SDR_Lead_Capture_Qualification_Agent.json](Complete_SDR_Lead_Capture_Qualification_Agent.json)

