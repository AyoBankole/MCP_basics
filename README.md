# Weather MCP Server

A simple MCP (Message Control Protocol) server built with Python and [uv](https://github.com/astral-sh/uv) for serving weather data, designed to integrate with Claude for Desktop or other MCP clients.

## Features

- Fetches real-time weather alerts for any US state using the National Weather Service (NWS) API.
- Provides detailed weather forecasts for any latitude/longitude in the US.
- Exposes easy-to-use MCP tools for integration with Claude or other clients.

## Requirements

- Python 3.10 or newer
- [uv](https://github.com/astral-sh/uv) (for running the server)
- [httpx](https://www.python-httpx.org/) (for async HTTP requests)
- [mcp](https://github.com/anthropics/mcp) (for MCP protocol support)

## Installation

1. Clone this repository or copy the `weather` folder into your project.
2. Install dependencies using [uv](https://github.com/astral-sh/uv):

   ```sh
   uv pip install -r requirements.txt

  ## Usage
- You can run the weather MCP server directly:
  ```sh
  uv run weather.py


## MCP Tools

The server exposes the following MCP tools:

### `get_alerts(state: str) -> str`

Fetches active weather alerts for a given US state (e.g., `"CA"`, `"NY"`).

### `get_forecast(latitude: float, longitude: float) -> str`

Fetches a weather forecast for the given latitude and longitude.

## Claude Desktop Configuration

To integrate this server with Claude for Desktop, add the following to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "weather": {
      "command": "C:\\Users\\User\\.local\\bin\\uv.exe",
      "args": [
        "--directory",
        "C:\\mcp_tutorial\\weather",
        "run",
        "weather.py"
      ]
    }
  }
}
