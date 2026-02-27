# Svelte MCP Power

Official Svelte Model Context Protocol server power for Kiro, providing up-to-date documentation, code analysis, and playground integration for building better Svelte applications with AI assistance.

## What is this?

This is a Kiro Power that integrates the official Svelte MCP server into your development workflow. It enables AI assistants to:

- Access up-to-date Svelte documentation directly from svelte.dev
- Analyze Svelte code and provide best practice suggestions
- Generate playground links for quick testing
- Stay current with Svelte 5 features and patterns

## Installation

### Via Kiro Powers UI (Recommended)

1. Open Kiro
2. Open the Powers panel (Command Palette → "Powers: Open Panel")
3. Click "Add Custom Power"
4. Choose one of these options:
   - **GitHub URL**: `https://github.com/coreyx/svelte-mcp-power`
   - **Local Directory**: Point to the `svelte-mcp-power` directory

### Manual Installation

Clone this repository and add the power via local directory:

```bash
git clone https://github.com/coreyx/svelte-mcp-power.git
cd svelte-mcp-power
```

Then in Kiro:
1. Open Powers panel
2. Click "Add Custom Power"
3. Select "Local Directory"
4. Provide the full path to `svelte-mcp-power`

## What's Included

### MCP Server Configuration

The power automatically configures the Svelte MCP server (`@sveltejs/mcp`) when installed. No manual MCP setup required!

### Documentation

Comprehensive documentation covering:
- **Onboarding**: Installation and verification
- **Workflows**: 4 complete workflows for common tasks
- **Tools Reference**: Detailed documentation for all 4 MCP tools
- **Troubleshooting**: Solutions for common issues
- **Best Practices**: Guidelines for effective usage

### Available Tools

Once installed, you'll have access to these MCP tools:

- **list-sections**: Browse available Svelte documentation sections
- **get-documentation**: Fetch full documentation content
- **svelte-autofixer**: Analyze code and get improvement suggestions
- **playground-link**: Generate shareable Svelte playground links

## Usage

After installation, simply mention Svelte-related topics in your conversations with Kiro, and the power will automatically activate. The AI assistant will use the MCP tools to:

1. Fetch relevant Svelte documentation
2. Generate Svelte 5 code with best practices
3. Analyze and fix code issues
4. Create playground links for testing

### Example Requests

- "Create a counter component using Svelte 5 runes"
- "Show me how to use $derived in Svelte 5"
- "Analyze this Svelte component and suggest improvements"
- "Generate a playground link for this code"

## Requirements

- Kiro IDE
- Node.js 16+ (for npx)
- Internet connection (for fetching documentation)

## About Svelte MCP

This power wraps the official Svelte MCP server maintained by the Svelte team. The server provides real-time access to Svelte documentation and code analysis tools.

- **Official Repository**: https://github.com/sveltejs/mcp
- **Documentation**: https://svelte.dev/docs/mcp
- **npm Package**: https://www.npmjs.com/package/@sveltejs/mcp

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## License

This power documentation is provided as-is. The Svelte MCP server itself is maintained by the Svelte team under their license terms.

## Author

Created by coreyx

---

**Keywords**: svelte, svelte5, documentation, code-analysis, playground
