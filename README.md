# AI Agent Skills Configuration

A comprehensive configuration setup for AI-assisted development with support for Python, Go, and Rust development workflows.

## Overview

This repository provides structured configuration for AI coding agents (Claude, Cline/Roo Code) including:
- Coding standards and rules
- Custom prompt templates
- MCP (Model Context Protocol) server configurations
- Language-specific best practices

## Repository Structure

```
./
├── .clinerules              # Cline/Roo Code rules and coding standards
├── .clauderc                # Claude CLI configuration
├── prompts/                 # Custom AI prompts for specific tasks
│   ├── code-review.md      # Comprehensive code review template
│   ├── debugging.md        # Systematic debugging methodology
│   └── documentation.md    # Documentation generation guidelines
└── mcp-servers/            # MCP server configurations
    └── config.json         # Server definitions and settings
```

## Quick Start

### 1. Clone and Setup

```bash
git clone <your-repo-url>
cd ai-agent-config
```

### 2. Configure for Your Project

Edit [.clinerules](.clinerules) to add project-specific preferences:
```bash
# Add your custom rules at the bottom of .clinerules
# Example: preferred libraries, frameworks, patterns
```

### 3. Enable MCP Servers

Edit [mcp-servers/config.json](mcp-servers/config.json) and enable the servers you need:
```json
{
  "mcpServers": {
    "filesystem": { "enabled": true },
    "git": { "enabled": true },
    "python-tools": { "enabled": true }
  }
}
```

### 4. Set Environment Variables

For servers requiring API keys or credentials:
```bash
# Add to your .env file (not committed to git)
export POSTGRES_PASSWORD="your-password"
export BRAVE_API_KEY="your-api-key"
export CUSTOM_API_KEY="your-key"
```

## Configuration Files

### .clinerules

Defines coding standards and best practices for:
- **Python**: PEP 8, type hints, async patterns
- **Go**: Error handling, interfaces, concurrency
- **Rust**: Ownership, error handling, performance

[View full rules](.clinerules)

### .clauderc

Claude CLI configuration including:
- Model preferences for different task types
- Tool enablement and restrictions
- Hooks for pre-commit/pre-push checks
- File inclusion/exclusion patterns
- Output formatting preferences

[View configuration](.clauderc)

### Prompt Templates

#### Code Review ([prompts/code-review.md](prompts/code-review.md))
Systematic code review covering:
- Functionality and logic
- Code quality and style
- Language-specific standards
- Testing and security
- Performance and documentation

#### Debugging ([prompts/debugging.md](prompts/debugging.md))
Structured debugging methodology:
- Problem definition
- Information gathering
- Hypothesis formation
- Language-specific common issues
- Debugging strategies

#### Documentation ([prompts/documentation.md](prompts/documentation.md))
Documentation generation guidelines:
- API documentation templates
- Language-specific docstring formats
- Tutorial writing best practices
- Architecture documentation

### MCP Servers

Pre-configured servers for enhanced capabilities:

**Enabled by Default:**
- `filesystem` - Enhanced file operations
- `git` - Advanced git operations
- `python-tools` - Python linting, testing, formatting
- `rust-tools` - Cargo, clippy, rustfmt
- `go-tools` - Go build, test, fmt, vet

**Optional (Disabled):**
- `sqlite` - SQLite database operations
- `postgres` - PostgreSQL operations
- `web-search` - Brave Search API
- `docker` - Container management
- `kubernetes` - K8s cluster management
- `custom-api` - Your custom MCP server

[View MCP configuration](mcp-servers/config.json)

## Usage

### Using Custom Prompts

Reference prompts in your AI agent conversations:

```
"Please review this code using the code-review.md template"
"Debug this issue following the debugging.md methodology"
"Generate documentation using the documentation.md guidelines"
```

### Enabling/Disabling MCP Servers

Edit [mcp-servers/config.json](mcp-servers/config.json):

```json
{
  "mcpServers": {
    "server-name": {
      "enabled": true,  // Set to false to disable
      ...
    }
  }
}
```

### Adding Custom Rules

Add project-specific rules to [.clinerules](.clinerules):

```
## Project-Specific Preferences
- Use SQLAlchemy for database operations in Python
- Prefer slog for logging in Go
- Use tokio for async runtime in Rust
- Always include integration tests for API endpoints
```

## Language Support

### Python
- PEP 8 compliance
- Type hints and mypy
- pytest for testing
- black for formatting
- ruff for linting

### Go
- gofmt formatting
- Comprehensive error handling
- Table-driven tests
- Context usage for cancellation
- Race detection

### Rust
- rustfmt formatting
- clippy linting
- Ownership best practices
- Result/Option error handling
- Comprehensive documentation

## Customization

### Adding New Prompts

Create new prompt templates in the [prompts/](prompts/) directory:

```bash
touch prompts/refactoring.md
# Add your prompt template content
```

Update [.clauderc](.clauderc) to auto-load:
```json
{
  "prompts": {
    "load_on_startup": [
      "code-review.md",
      "debugging.md",
      "documentation.md",
      "refactoring.md"
    ]
  }
}
```

### Adding Custom MCP Servers

1. Add server configuration to [mcp-servers/config.json](mcp-servers/config.json)
2. Install the server binary/package
3. Set required environment variables
4. Enable the server

Example:
```json
{
  "your-server": {
    "command": "/path/to/server",
    "args": ["--config", "config.json"],
    "enabled": true,
    "capabilities": ["tool1", "tool2"],
    "env": {
      "API_KEY": "${YOUR_API_KEY}"
    }
  }
}
```

## Best Practices

1. **Review Rules Regularly**: Update [.clinerules](.clinerules) as your team's practices evolve
2. **Keep Prompts Updated**: Refine prompt templates based on what works well
3. **Secure Credentials**: Never commit API keys or passwords
4. **Enable Only Needed Servers**: Disable unused MCP servers to reduce overhead
5. **Version Control**: Track changes to configuration files
6. **Document Custom Changes**: Add comments explaining project-specific rules

## Security Considerations

- API keys and credentials in environment variables only
- [mcp-servers/config.json](mcp-servers/config.json) includes path restrictions
- Review enabled MCP servers and their permissions
- Use readonly mode for database servers when possible
- Regularly update MCP server packages

## Troubleshooting

### MCP Server Not Starting
- Check server is installed: `which <server-command>`
- Verify environment variables are set
- Check logs: `tail -f logs/mcp-servers.log`
- Ensure paths in config are absolute

### Rules Not Being Followed
- Verify [.clinerules](.clinerules) is in project root
- Check [.clauderc](.clauderc) has `"enforce": true`
- Ensure AI agent is configured to read .clinerules

### Prompts Not Loading
- Check file paths in [.clauderc](.clauderc)
- Verify prompts directory exists
- Ensure prompt files are valid markdown

## Contributing

Contributions are welcome! Areas for improvement:
- Additional language support
- More prompt templates
- Additional MCP server configurations
- Improved coding rules and standards

## License

See [LICENSE](LICENSE) file for details.