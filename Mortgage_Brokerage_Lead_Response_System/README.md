# Mortgage Brokerage - Lead Response System

This n8n workflow provides a comprehensive lead response and nurturing system specifically designed for mortgage brokerages. It captures leads, qualifies them based on a lead score, and then initiates a multi-channel, multi-stage follow-up sequence including immediate SMS and email responses, AI-powered voice calls, CRM integration, and scheduled nurture campaigns.

## Features

*   **Lead Capture Webhook**: Receives incoming leads from various sources.
*   **Lead Scoring & Filtering**: Qualifies leads based on a lead score, routing them to different follow-up paths.
*   **Immediate Multi-Channel Response**: Sends instant SMS and email acknowledgments to high-scoring leads.
*   **AI Voice Call Integration**: Initiates an AI-powered voice call (via Vapi) to engage high-priority leads.
*   **CRM Integration**: Creates contacts and urgent tasks in HubSpot (or a similar CRM).
*   **Multi-Stage Nurture Campaigns**: Implements a series of timed follow-ups via SMS and email over several days.
*   **Appointment Booking Webhook**: Handles appointment booking confirmations and updates CRM.
*   **Appointment Reminders**: Sends 24-hour and 2-hour reminders for booked appointments.

## How it Works

1.  **Webhook - Lead Capture**: The workflow is triggered by an incoming lead via a webhook.
2.  **Lead Score Filter**: Leads are filtered based on a predefined lead score (e.g., >70).
3.  **Immediate Response (SMS & Email)**: High-scoring leads receive immediate SMS and email acknowledgments.
4.  **Wait 2 Minutes**: A short delay before initiating the AI voice call.
5.  **AI Voice Call (Vapi)**: An AI voice agent calls the lead to further qualify and engage them.
6.  **CRM - Create Contact & Urgent Task**: A new contact is created in HubSpot, and an urgent task is assigned for manual follow-up if needed.
7.  **Wait 2 Hours / Check If Contacted**: The workflow waits and then checks if the lead has been contacted.
8.  **SMS - 2 Hour Follow-up**: If not contacted, a follow-up SMS is sent.
9.  **Wait 1 Day / Check If Contacted (Day 1)**: Another wait period, followed by a check.
10. **Email - Day 1 Nurture**: A nurture email is sent if the lead is still not contacted.
11. **Wait 2 Days / Check If Contacted (Day 3)**: Further waiting and checking.
12. **CRM - Day 3 Call Task**: A task is created in the CRM for a manual call on Day 3.
13. **Wait 4 Days (Total: 7) / Check If Contacted (Day 7)**: Final waiting period and check.
14. **CRM - Move to Long-term Nurture / SMS - Final Message**: If still not contacted, the lead is moved to a long-term nurture sequence, and a final SMS is sent.
15. **Low Score Lead Path**: Leads with a low score are routed to a newsletter subscription and CRM update.
16. **Webhook Response**: Sends a success response back to the lead capture system.
17. **Webhook - Appointment Booked**: A separate branch handles appointment booking confirmations, updating the CRM and sending SMS/email confirmations and reminders.

## Setup Instructions

1.  **n8n Instance**: Ensure you have a running n8n instance.
2.  **Credentials**: Configure credentials for:
    *   Twilio API (for SMS)
    *   SendGrid API (for email)
    *   Vapi API (for AI voice calls)
    *   HubSpot API (for CRM integration)
    *   Google Calendar API (for appointment scheduling)
3.  **CRM Setup**: Configure your HubSpot CRM with appropriate contact properties and task types.
4.  **Vapi Assistant**: Set up an AI assistant in Vapi with the desired script for lead engagement.
5.  **Workflow Import**: Import the provided `.json` workflow file into your n8n instance.
6.  **Configuration**: Adjust webhook URLs, API keys, lead scoring thresholds, email templates, and CRM field mappings as needed.

## Workflow File

[Mortgage_Brokerage_Lead_Response_System.json](Mortgage_Brokerage_Lead_Response_System.json)

