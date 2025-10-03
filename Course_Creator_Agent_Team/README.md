# Course Creator Agent Team

This n8n workflow orchestrates a team of AI agents to assist in the creation of online courses. It starts by ideating course concepts based on user input, then designs modules and sub-modules, and finally stores all this information in Airtable.

## Features

*   **Course Idea Generation**: An AI agent generates compelling course ideas tailored to a user's background, skills, and interests.
*   **Module Design**: Another AI agent designs 4 core modules and 2 bonus modules for the generated course, complete with short titles and descriptions.
*   **Sub-Module Breakdown**: Further AI processing breaks down modules into detailed sub-modules with teaching points.
*   **Airtable Integration**: All course ideas, modules, and sub-modules are systematically stored and updated in an Airtable CRM.

## How it Works

1.  **Start Course Creation (Telegram Trigger)**: The workflow is initiated, likely via a Telegram bot, to gather initial user information (name, expertise, experience, passion, audience).
2.  **Course Idea Creator Agent**: An AI agent uses the provided user context to generate a unique course concept, including title, target audience, pain point, transformation, and a 

Unique Value Zone score.
3.  **Structured Output Parser**: Parses the AI-generated course idea into a structured JSON format.
4.  **Module Creator Agent**: An AI agent takes the course idea and designs 4 core modules and 2 bonus modules, each with a title and a 20-word description.
5.  **Module Code**: Formats the modules for storage.
6.  **Update Modules (Airtable)**: Stores the generated modules in Airtable, linking them to the course overview.
7.  **Split Out / Loop Over Items**: Iterates through each module to create sub-modules.
8.  **Sub-Module Creator Agent**: An AI agent generates detailed sub-modules with bullet points for each main module.
9.  **Structured Output Parser (Sub-modules)**: Parses the AI-generated sub-modules.
10. **Sub-Module Code**: Formats the sub-modules for storage.
11. **Update Sub-Modules (Airtable)**: Stores the generated sub-modules in Airtable.

## Setup Instructions

1.  **n8n Instance**: Ensure you have a running n8n instance.
2.  **Credentials**: Configure credentials for:
    *   Telegram API (for the trigger)
    *   OpenAI API (for the AI agents)
    *   Airtable API (for storing course data)
3.  **Airtable Base**: Set up an Airtable base with tables for "Course Overview", "Modules", and "Sub-Modules" as referenced in the workflow.
4.  **Workflow Import**: Import the provided `.json` workflow file into your n8n instance.
5.  **Configuration**: Adjust the Telegram trigger, Airtable base/table IDs, and any specific parameters within the AI nodes as needed.

## Workflow File

[Course_Creator_Agent_Team.json](Course_Creator_Agent_Team.json)

