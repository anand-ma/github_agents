# 🔮 MCP GitHub Agent

A Streamlit application that allows you to explore and analyze GitHub repositories using natural language queries through the Model Context Protocol (MCP).

## Features

- **Natural Language Interface**: Ask questions about repositories in plain English
- **Comprehensive Analysis**: Explore issues, pull requests, repository activity, and code statistics
- **Interactive UI**: User-friendly interface with example queries and custom input
- **MCP Integration**: Leverages the Model Context Protocol to interact with GitHub's API
- **Real-time Results**: Get immediate insights on repository activity and health

## Demo

Try the live demo here: [GitHub Agent](https://githup-agent.streamlit.app/)

## Setup

### Requirements

- Python 3.8+
- Node.js and npm (for MCP GitHub server)
  - This is a critical requirement! The app uses `npx` to run the MCP GitHub server
  - Download and install from [nodejs.org](https://nodejs.org/)
- GitHub Personal Access Token with appropriate permissions
- OpenAI API Key

### Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/anand-ma/github_agents.git
   cd github-agent
   ```

2. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

3. Verify Node.js and npm are installed:
   ```bash
   node --version
   npm --version
   npx --version
   ```
   All of these commands should return version numbers. If they don't, please install Node.js.

4. Set up your API keys:
   - Add your OpenAI API Key and GitHub token to the Streamlit secrets file:
     ```toml
     # .streamlit/secrets.toml
     github_token = "your-github-token-here"
     openai_api_key = "your-openai-api-key-here"
     ```
   - Alternatively, you can set the GitHub token as an environment variable:
     ```bash
     export OPENAI_API_KEY=your-openai-api-key
     export GITHUB_TOKEN=your-github-token
     ```

5. Create a GitHub Personal Access Token:
   - Visit https://github.com/settings/tokens
   - Create a new token with `repo` and `user` scopes
   - Save the token somewhere secure

### Running the App

1. Start the Streamlit app:
   ```bash
   streamlit run app.py
   ```

2. In the app interface:
   - Enter your GitHub token in the sidebar
   - Specify a repository to analyze
   - Select a query type or write your own
   - Click "Run Query"

## Key Packages Used

This project uses the following key packages:

1. **[Agno](https://github.com/agno-agi/agno)**
   - Provides tools for building AI agents.
   - lightweight library for building Reasoning Agents with memory, knowledge, tools and native multi-modal support. Use Agno to build Reasoning Agents, Multi-Modal Agents, Teams of Agents and Agentic Workflows.
   - The `Agent` class is used to create an AI agent that interacts with the user and tools.

2. **[MCPTools](https://docs.agno.com/tools/mcp)**
   - A set of tools for interacting with the Model Context Protocol (MCP).
   - Used to initialize and interact with the MCP server for GitHub data.

3. **[MCP (Model Context Protocol)](https://modelcontextprotocol.io/introduction)**
   - A protocol for real-time interaction with external systems like GitHub.
   
4. **[MCP Client](https://github.com/modelcontextprotocol/python-sdk)**
   - Provides the `stdio_client` for establishing a connection to the MCP server.
   - Enables seamless communication between the app and the MCP server.
   - Includes `ClientSession` for managing communication and `StdioServerParameters` for server configuration.

5. **[MCP Servers](https://github.com/modelcontextprotocol/servers)**
   - Provides a list of servers that can be used with `StdioServerParameters`.
   - Includes configurations for GitHub, GitLab, and other integrations.

### Example Queries

#### Issues
- "Show me issues by label"
- "What issues are being actively discussed?"
- "Find issues labeled as bugs"

#### Pull Requests
- "What PRs need review?"
- "Show me recent merged PRs"
- "Find PRs with conflicts"

#### Repository
- "Show repository health metrics"
- "Show repository activity patterns"
- "Analyze code quality trends"
