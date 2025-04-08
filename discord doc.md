Documentation: Daemons Discord Bot with ChromaDB and ChatGPT
Overview
This document provides instructions for setting up and running the Daemons Discord bot, which uses ChromaDB for document storage and retrieval, and OpenAI's ChatGPT for generating responses to user queries about the Daemons blockchain game.
Prerequisites
1. System Requirements
Python 3.8 or higher
Discord account with developer permissions
OpenAI API key
Playwright (for web scraping functionality)
2. Software Dependencies
Install the required Python packages:
pip install discord.py openai chromadb unstructured playwright beautifulsoup4 requests python-dotenv pandas
Install Playwright browsers:
playwright install
3. Environment Variables
Create a .env file in your project directory with the following variables:
DISCORD_BOT_TOKEN=your_discord_bot_token_here
OPENAI_API_KEY=your_openai_api_key_here
Setup Instructions
1. Initial Setup
Clone the repository containing the bot code
Install the prerequisites listed above
Create your .env file with the required credentials

The bot will automatically create a ChromaDB database in the specified location (c:\Users\UK-PC\Desktop\discordBot\chroma_db)- change this path to were you want.
2. Document Sources
The bot comes pre-configured with the following Daemons documentation sources:
Daemons Home
Daemons Editor
Daemons Roadmap
Daemons Partners
Daemons Assets
Daemons Lore
And more (see full list in the code)

These URLs are automatically scraped and processed when the bot starts.
Running the Bot
1. Starting the Bot
Run the bot with: python your_bot_file_name.py
2. First Run Behavior
On first run:
The bot will scrape all configured documentation URLs
It will process the content into meaningful chunks
It will create embeddings using OpenAI's text-embedding-3-small model
It will store these in ChromaDB
Subsequent runs will use the cached data unless forced to refresh
Note: The first run may take several minutes as it processes all documents.

Bot Commands
User Commands
!daemon [question] - Ask any question about Daemons
Example: !daemon What is the Daemons roadmap?
Admin Commands-(can be perform only by the channel administrator)
!debug_collection - Shows statistics about the vector database
!refresh_data - Forces a refresh of all documentation data
Features
1. Knowledge Base
The bot maintains a vector database of Daemons documentation
It can answer questions by retrieving relevant documents and generating responses
2. Daily Insights
Posts a random Daemons fact or tip daily in a configured channel
3. Web Scraping
Uses Playwright to scrape dynamic content from documentation pages
Processes HTML into meaningful chunks with headers and structure
4. Response Generation
Uses GPT-4 to generate responses based on retrieved documents
Provides source links for reference
