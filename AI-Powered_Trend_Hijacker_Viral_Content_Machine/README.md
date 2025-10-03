# AI-Powered Trend Hijacker & Viral Content Machine

This n8n workflow leverages AI to identify trending topics across various platforms (Twitter, Reddit, Google Trends) and automatically generates engaging social media content. It analyzes trends for engagement potential and controversy risk, then creates catchy captions and relevant images for platforms like Twitter and LinkedIn. The workflow also includes a step to save generated content to Google Drive.

## Features

*   **Trend Identification**: Gathers trending topics from Twitter, Reddit, and Google Trends.
*   **AI Analysis**: Uses AI to analyze trends for general audience alignment, engagement potential, controversy risk, and suggested content angles.
*   **Content Generation**: Generates multiple variations of social media captions with catchy hooks, hashtags, and calls-to-action.
*   **Image Generation**: Creates relevant images to accompany the generated captions.
*   **Multi-Platform Posting**: Posts content to Twitter and LinkedIn.
*   **Content Archiving**: Saves all generated content to Google Drive for record-keeping.

## How it Works

1.  **Schedule Trigger**: The workflow is initiated on a schedule.
2.  **Gather Trends**: Makes HTTP requests to Twitter, Reddit, and Google Trends APIs to fetch current trending topics.
3.  **Merge Trends**: Combines the data from various trend sources.
4.  **AI Trend Analysis**: An AI model (e.g., GPT-4) analyzes the merged trends to assess their suitability for content creation.
5.  **Filter High Engagement**: Filters out trends that have high engagement potential and low controversy risk.
6.  **Generate Captions**: Uses AI to create engaging social media post variations based on the selected trends.
7.  **Generate Image**: Uses AI (e.g., DALL-E) to generate a visual asset for the post.
8.  **Combine Content & Image**: Merges the generated caption and image data.
9.  **Post & Save**: Posts the complete content to Twitter and LinkedIn, and saves it to Google Drive.

## Setup Instructions

1.  **n8n Instance**: Ensure you have a running n8n instance.
2.  **Credentials**: Configure credentials for:
    *   Twitter API
    *   Reddit API (if required, though often public data)
    *   Google Trends API (if required, though often public data)
    *   OpenAI API (for AI Trend Analysis and Generate Captions)
    *   DALL-E API (for Generate Image)
    *   LinkedIn API
    *   Google Drive API
3.  **Workflow Import**: Import the provided `.json` workflow file into your n8n instance.
4.  **Configuration**: Adjust the schedule trigger and any specific parameters within the AI nodes or API requests as needed.

## Workflow File

[AI-Powered_Trend_Hijacker_Viral_Content_Machine.json](AI-Powered_Trend_Hijacker_Viral_Content_Machine.json)

