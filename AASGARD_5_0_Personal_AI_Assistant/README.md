# AASGARD 5.0 - Personal AI Assistant

This n8n workflow acts as a personal AI assistant, integrating with Telegram to receive commands and then routing them to various services like email, calendar, CRM, document management, and web research. It uses AI to analyze commands and determine the appropriate action.

## Features

*   **Telegram Integration**: Receives commands and sends confirmations via Telegram.
*   **AI Command Analysis**: Uses AI to interpret user commands and identify the intended action (e.g., send email, create meeting, add contact).
*   **Multi-Service Integration**: Connects with:
    *   Gmail (to send emails)
    *   Google Calendar (to create meetings)
    *   Google Sheets (to add/update contacts)
    *   Google Drive (to manage documents)
    *   Tavily API (for web research)
*   **Dynamic Action Routing**: Routes commands to the correct service based on AI analysis.
*   **Confirmation System**: Sends confirmation messages back to the user via Telegram.

## How it Works

1.  **Telegram Trigger**: The workflow starts when a message is received via Telegram.
2.  **Prepare AI Input**: Formats the incoming message for AI processing.
3.  **AI Command Analyzer**: An AI model analyzes the Telegram message to understand the user's intent and extract relevant details (e.g., recipient, subject, date, query).
4.  **Parse AI Response**: Extracts structured data from the AI's analysis.
5.  **Route by Action**: A switch node directs the workflow to the appropriate service based on the AI's identified action.
    *   **Send Email**: If the intent is to send an email, it uses Gmail.
    *   **Create Meeting**: If the intent is to create a meeting, it uses Google Calendar.
    *   **Generate Invoice/Quote**: If the intent is to generate an invoice/quote, it uses a code node and then converts it to PDF via HTTP Request and sends it via Gmail.
    *   **Add/Update Contact**: If the intent is to manage contacts, it uses Google Sheets.
    *   **Manage Documents**: If the intent is to manage documents, it uses Google Drive.
    *   **Web Research**: If the intent is to perform web research, it uses the Tavily API.
6.  **Format Confirmation**: Prepares a confirmation message.
7.  **Send Confirmation**: Sends the confirmation message back to the user via Telegram.

## Setup Instructions

1.  **n8n Instance**: Ensure you have a running n8n instance.
2.  **Credentials**: Configure credentials for:
    *   Telegram API
    *   OpenAI API (for AI Command Analyzer)
    *   Gmail API
    *   Google Calendar API
    *   Google Sheets API
    *   Google Drive API
    *   Tavily API
    *   html2PdfApi (for invoice/quote generation)
3.  **Workflow Import**: Import the provided `.json` workflow file into your n8n instance.
4.  **Configuration**: Adjust webhook IDs, API keys, and any specific parameters within the nodes as needed.

## Workflow File

[AASGARD_5_0_Personal_AI_Assistant.json](AASGARD_5_0_Personal_AI_Assistant.json)

