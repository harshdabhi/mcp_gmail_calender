# Langchain MCP Agent

This project demonstrates a Langchain agent integrated with multiple MCP (Multi-tool Coordination Protocol) servers, including a custom Gmail MCP server, a Google Calendar MCP server, and other utility tools like math and search.

## Setup and Running Locally

To run this project on your local system using `uv`, follow these steps:

1. **Clone the repository:**

   ```bash
   git clone https://github.com/harshdabhi/mcp_gmail_calender.git
   cd mcp_gmail_calender


   ```
2. **Install `uv`:**

   If you don't have `uv` installed, you can install it using pip:

   ```bash
   pip install uv
   ```

   Or, if you prefer a standalone executable, follow the instructions on the official `uv` documentation.
3. **Install Python Dependencies:**

   Ensure you have all the necessary Python packages installed. From the project root, run:

   ```bash
   uv pip install -r requirements.txt
   ```
4. **Set up Environment Variables (.env file):**

   Create a `.env` file in the root of your project and add your `GROQ_API_KEY`:

   ```
   GROQ_API_KEY=your_groq_api_key
   ```

   Replace `your_groq_api_key` with your actual Groq API key.
5. **Configure MCP Servers:**

   The project uses a `mcp_config/mcp_servers_file.json` to configure the MCP servers. Ensure this file is correctly set up with the paths to your local MCP server implementations.
6. **Gmail MCP Server Setup:**

   For detailed instructions on how to enable and authenticate the Gmail MCP server, refer to its documentation:
   [https://glama.ai/mcp/servers/@GongRzhe/Gmail-MCP-Server](https://glama.ai/mcp/servers/@GongRzhe/Gmail-MCP-Server)

   A common step involves moving your `gcp-oauth.keys.json` to `~/.gmail-mcp/` and running an `npx` command for authentication:

   ```bash
   mkdir -p ~/.gmail-mcp/
   mv <path_to_your_gcp-oauth.keys.json> ~/.gmail-mcp/
   npx @gongrzhe/server-gmail-autoauth-mcp auth
   ```

   *Note: You need Node.js and npm installed for `npx` to work. If you encounter `npx: command not found`, please install Node.js and npm (e.g., using `brew install node` on macOS).*
7. **Google Calendar MCP Server Setup:**

   For detailed instructions on how to enable and use the Google Calendar MCP server, refer to its documentation:
   [https://glama.ai/mcp/servers/@cablate/mcp-google-calendar](https://glama.ai/mcp/servers/@cablate/mcp-google-calendar)

   Similar to Gmail, you might need to set up authentication and ensure `GOOGLE_CALENDAR_ID`, `GOOGLE_TIME_ZONE`, and `GOOGLE_CREDENTIALS_PATH` are correctly configured, preferably via environment variables in your `.env` file.
8. **Run the Langchain Agent:**

   Once all dependencies are installed and configurations are in place, you can run the Langchain agent:

   ```bash
   python server/langchain_server
   ```

   This will start an interactive chat in your terminal. Type your queries, and the agent will respond using the configured MCP tools. Type `exit` or `quit` to end the session.

## LangSmith Tracing

This project is configured to use [LangSmith](https://www.langchain.com/langsmith) for tracing agent interactions. To enable tracing, ensure you have the following environment variables set in your `.env` file:

```
LANGCHAIN_TRACING_V2=true
LANGCHAIN_API_KEY=your_langsmith_api_key
LANGCHAIN_PROJECT=your_project_name  # Optional: Replace with your desired project name
```

Replace `your_langsmith_api_key` with your actual LangSmith API key.

After setting these variables, run the agent as described in step 8 of the "Setup and Running Locally" section. Your traces will automatically appear in your LangSmith account.

## Video Demonstration

https://youtu.be/Rjx7djPGeaw
