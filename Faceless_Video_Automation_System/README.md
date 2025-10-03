# Faceless Video Automation System

This n8n workflow automates the creation of faceless videos for platforms like YouTube or TikTok. It integrates various AI services to generate scripts, create voiceovers, find stock footage, and even render the final video. It also includes a human quality control (QC) gate to ensure high-quality output.

## Features

*   **Script Generation**: Uses GPT-4o to generate video scripts based on a prompt.
*   **Scene Breakdown**: Parses the script into individual scenes with narration and image prompts.
*   **Image Generation**: Generates images for each scene using Leonardo AI.
*   **Voiceover Generation**: Creates natural-sounding voiceovers using ElevenLabs.
*   **Video Compilation**: Builds a video timeline and renders the final video using Shotstack.
*   **Human QC Gate**: Integrates a manual approval step via Slack to review generated videos before publishing, preventing 

'Uncanny Valley' failures.

## How it Works

1.  **Airtable Trigger**: The workflow is triggered by a new video prompt in Airtable.
2.  **Generate Script with GPT-4o**: An OpenAI model generates a video script based on the prompt.
3.  **Parse Script JSON**: The script is parsed into individual scenes, each with narration text and an image prompt.
4.  **Save Scenes to Airtable**: The parsed scenes are saved back to Airtable.
5.  **Generate Image - Leonardo AI**: For each scene, an image is generated using Leonardo AI based on the image prompt.
6.  **Wait for Image Generation**: The workflow waits for the image generation to complete.
7.  **Fetch Generated Image**: The URL of the generated image is retrieved.
8.  **Extract Image URL**: The image URL is extracted from the response.
9.  **Generate Voiceover - ElevenLabs**: Narration for each scene is converted into an audio file using ElevenLabs.
10. **Upload Audio/Image to Drive**: Both the generated audio and image files are uploaded to Google Drive.
11. **Merge Image + Audio Data**: The image and audio data for each scene are merged.
12. **Aggregate All Scenes**: All scene data is aggregated and sorted.
13. **Build Shotstack Timeline**: A Shotstack timeline JSON is constructed from the aggregated scene data, including background music.
14. **Render Video - Shotstack**: The video is rendered using Shotstack.
15. **Wait for Video Render**: The workflow waits for the video rendering to complete.
16. **Check Render Status**: The status of the video render is checked.
17. **Check if Render Complete**: If the render is complete, the workflow proceeds.
18. **Update Airtable with Video**: The Airtable record is updated with the URL of the final video.

## Setup Instructions

1.  **n8n Instance**: Ensure you have a running n8n instance.
2.  **Credentials**: Configure credentials for:
    *   Airtable API
    *   OpenAI API (for script generation)
    *   Leonardo AI API (for image generation)
    *   ElevenLabs API (for voiceover generation)
    *   Shotstack API (for video rendering)
    *   Google Drive API
    *   Slack API (for QC notifications)
3.  **Airtable Base**: Set up an Airtable base with tables for video prompts and scenes.
4.  **Workflow Import**: Import the provided `.json` workflow file into your n8n instance.
5.  **Configuration**: Adjust Airtable base/table IDs, API keys, and any specific parameters within the nodes as needed. Ensure the Google Drive folder ID is correctly set.

## Workflow File

[Faceless_Video_Automation_System.json](Faceless_Video_Automation_System.json)

