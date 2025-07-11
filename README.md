# ModelScope Unofficial MCP Server

> 🚧 **WIP**: This project is currently under development and not yet complete. It's in the early development stage, and features and APIs may change.

## Features

- [x] Generate image URL from text

## Usage

### Runing the Demo

```bash
export MODELSCOPE_API_KEY="your_api_key_here"

uv run python demo.py
```

### Integrate with popular MCP clients

- Use in Claude Desktop / Cursor / Cherry Studio:

```json
{
  "mcpServers": {
    "modelscope-mcp-server": {
      "command": "uvx",
      "args": ["modelscope-mcp-server"],
      "env": {
        "MODELSCOPE_API_KEY": "your-api-key"
      }
    }
  }
}
```

## Contributing

### Prerequisites

- Python 3.12+
- [uv](https://docs.astral.sh/uv/) (Recommended for environment management)

### Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/pengqun/modelscope-mcp-server.git
   cd modelscope-mcp-server
   ```

2. Create and sync the environment:

   ```bash
   uv sync
   ```

   This installs all dependencies, including dev tools.

3. Activate the virtual environment (e.g., `source .venv/bin/activate` or via your IDE).

### Run the Server

```bash
# Run with stdio transport (default)
uv run modelscope-mcp-server

# Run with streamable HTTP transport
fastmcp run src/modelscope_mcp_server/server.py --transport http
```

### Unit Tests

All PRs must introduce or update tests as appropriate and pass the full suite.

Run tests using pytest:

```bash
pytest
```

or if you want an overview of the code coverage

```bash
uv run pytest --cov=src --cov=examples --cov-report=html
```

### Static Checks

This project uses `pre-commit` for code formatting, linting, and type-checking. All PRs must pass these checks (they run automatically in CI).

Install the hooks locally:

```bash
uv run pre-commit install
```

The hooks will now run automatically on `git commit`. You can also run them manually at any time:

```bash
pre-commit run --all-files
# or via uv
uv run pre-commit run --all-files
```

### Publish to PyPI

```bash
# Run the publishing script
python scripts/publish.py
```

TODO: auto publish via Github Actions

## References

- Model Context Protocol - <https://modelcontextprotocol.io/>
- FastMCP v2 - <https://github.com/jlowin/fastmcp>
- MCP Python SDK - <https://github.com/modelcontextprotocol/python-sdk>
- MCP Example Servers - <https://github.com/modelcontextprotocol/servers>
- Hugging Face Official MCP Server - <https://github.com/evalstate/hf-mcp-server>
- mcp-hfspace MCP Server - <https://github.com/evalstate/mcp-hfspace>
- shreyaskarnik/huggingface-mcp-server - <https://github.com/shreyaskarnik/huggingface-mcp-server>
- Cursor – Model Context Protocol - <https://docs.cursor.com/context/model-context-protocol>
