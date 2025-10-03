# TikTok Shop Affiliate UGC Generator

This n8n workflow automates the creation of user-generated content (UGC) style videos for TikTok Shop affiliate marketing. It integrates with Google Sheets to ingest product catalogs, leverages AI (Gemini) to generate viral TikTok scripts based on current trends, and uses a video generation service (HeyGen/Synthesia) to create hyper-realistic videos. A critical human Quality Control (QC) gate is included to ensure video quality before publishing to TikTok.

## Features

*   **Product Catalog Ingestion**: Reads product data from Google Sheets.
*   **Viral Trend Integration**: Fetches current viral trends via Google Search to inform script generation.
*   **AI Script Generation**: Uses the Gemini API to create high-converting, UGC-style TikTok scripts with Gen Z slang, integrating product benefits naturally.
*   **Hyper-Realistic Video Generation**: Integrates with video generation platforms (e.g., HeyGen or Synthesia) to produce videos from the generated scripts.
*   **Human Quality Control (QC) Gate**: A mandatory approval step via Slack ensures that only high-quality, hyper-realistic videos are published, preventing 

"'Uncanny Valley'" scenarios.
*   **TikTok Posting**: Automatically posts approved videos to TikTok.
*   **Content Logging**: Logs published content to Google Sheets.

## How it Works

1.  **Schedule - Daily Run**: The workflow is triggered daily to check for new products and trends.
2.  **Google Sheets - Product Catalog Ingest**: Fetches product information (e.g., ProductName, KeyBenefit, ProductImageURL, Category) from a specified Google Sheet.
3.  **Split in Batches (Scale)**: Processes products in batches.
4.  **Google Search - Fetch Viral Trends**: Performs a Google Search to identify current viral trends relevant to TikTok.
5.  **Function - Gemini Script Generator (UGC Style)**: Uses the Gemini API to generate a TikTok script for each product, incorporating viral trends and a UGC-style tone. It includes retry logic for API calls.
6.  **HTTP Request - HeyGen Video Generation (Hyper-Realistic)**: Sends the generated script and product image URL to a video generation service (e.g., HeyGen or Synthesia) to create the video.
7.  **Wait - For Video Generation**: Pauses the workflow to allow time for video rendering.
8.  **Slack - Post QC Approval Request**: Posts a notification to a Slack channel with the generated video URL, requesting human review and approval.
9.  **Approval Waiter (QC Gate)**: The workflow waits for manual approval from a human reviewer.
10. **IF - QC Approved (Hyper-Realistic)**: If the video is approved, it proceeds to post to TikTok.
11. **HTTP Request - TikTok Post (Final Deliverable)**: Posts the approved video to TikTok with a generated caption and relevant hashtags.
12. **Google Sheets - Log Published Content**: Logs details of the published video (e.g., product name, video URL) to a Google Sheet.

## Setup Instructions

1.  **n8n Instance**: Ensure you have a running n8n instance.
2.  **Credentials**: Configure credentials for:
    *   Google Sheets API
    *   Google Search API
    *   Gemini API (via HTTP Request node, requires API key)
    *   HeyGen/Synthesia API (or similar video generation service)
    *   Slack API
    *   TikTok API
3.  **Google Sheet**: Prepare a Google Sheet with your product catalog, including columns like `ProductName`, `KeyBenefit`, `ProductImageURL`, and `Category`.
4.  **Workflow Import**: Import the provided `.json` workflow file into your n8n instance.
5.  **Configuration**: Adjust API keys, sheet IDs, Slack channel IDs, and any other specific parameters within the nodes as needed. Ensure the `apiKey` variable in the Gemini Script Generator function node is updated with your actual Gemini API key.

## Workflow File

[TikTok_Shop_Affiliate_UGC_Generator.json](TikTok_Shop_Affiliate_UGC_Generator.json)

