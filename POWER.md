---
name: "svelte-mcp-power"
displayName: "Svelte MCP"
description: "Official Svelte Model Context Protocol server providing up-to-date documentation, code analysis, and playground integration for building better Svelte applications with AI assistance."
keywords: ["svelte", "svelte5", "documentation", "code-analysis", "playground"]
author: "coreyx"
---

# Svelte MCP

## Overview

The Svelte MCP (Model Context Protocol) server is the official tool from the Svelte team that helps AI assistants write better Svelte code. It provides real-time access to Svelte documentation, static code analysis with suggestions, and playground integration for testing generated code.

This power enables AI assistants to:
- Access up-to-date Svelte documentation directly from svelte.dev
- Analyze Svelte code and provide best practice suggestions
- Generate playground links for quick testing
- Stay current with Svelte 5 features and patterns

The MCP server is particularly useful when working with Svelte 5's new features like runes, snippets, and the updated reactivity model.

## Onboarding

### Prerequisites

- Node.js 16+ or compatible JavaScript runtime
- npx (comes with npm 5.2+)
- Internet connection (for fetching documentation)

### Installation

The Svelte MCP server is available via the `@sveltejs/mcp` npm package. No global installation is required - it can be run directly with npx.

**For Kiro:**

The MCP server configuration has been added to your workspace. The server will automatically start when Kiro loads.

If you need to manually configure it, add this to `.kiro/settings/mcp.json`:

```json
{
  "mcpServers": {
    "svelte": {
      "command": "npx",
      "args": ["-y", "@sveltejs/mcp"]
    }
  }
}
```

### Verification

Once configured, the Svelte MCP server should appear in your MCP servers list. You can verify it's working by checking that the following tools are available:
- `list-sections`
- `get-documentation`
- `svelte-autofixer`
- `playground-link`

## Common Workflows

### Workflow 1: Getting Svelte Documentation

When you need to understand a Svelte concept or feature, use the documentation tools to fetch relevant information.

**Steps:**

1. **List available documentation sections** to see what's available:
   - Use `list-sections` tool to get all documentation sections
   - Review the returned sections and their use cases
   - Identify which sections are relevant to your task

2. **Fetch specific documentation** for the sections you need:
   - Use `get-documentation` tool with the section paths
   - Can request single or multiple sections at once
   - Documentation is fetched directly from svelte.dev (always up-to-date)

**Example Use Cases:**
- Learning about Svelte 5 runes ($state, $derived, $effect)
- Understanding component composition with snippets
- Exploring reactivity patterns
- Checking API references for built-in functions

**Best Practice:** Always call `list-sections` first to understand what documentation is available, then use `get-documentation` to fetch the relevant sections.

### Workflow 2: Analyzing and Fixing Svelte Code

Use the static analysis tool to check generated Svelte code for issues and get suggestions for improvements.

**Steps:**

1. **Generate or write Svelte code** for your component or module

2. **Run the autofixer** on your code:
   - Use `svelte-autofixer` tool with your code
   - Receives analysis results with issues and suggestions
   - Issues are categorized by severity

3. **Apply suggested fixes** iteratively:
   - Review the suggestions from the autofixer
   - Apply fixes to your code
   - Run autofixer again to verify fixes
   - Repeat until all issues are resolved

**What the Autofixer Checks:**
- Svelte 5 best practices
- Proper use of runes and reactivity
- Component structure and patterns
- Common mistakes and anti-patterns
- Performance considerations

**Example:**
```svelte
<!-- Before autofixer -->
<script>
  let count = 0;
</script>

<!-- After autofixer suggests Svelte 5 runes -->
<script>
  let count = $state(0);
</script>
```

### Workflow 3: Creating Playground Links

Generate shareable playground links to test and demonstrate Svelte code without creating files.

**Steps:**

1. **Prepare your Svelte code** (component or example)

2. **Generate playground link**:
   - Use `playground-link` tool with your code
   - Receives a URL to the Svelte playground
   - Code is embedded in the URL (no server storage)

3. **Share or test**:
   - Open the link to test in the browser
   - Share with others for collaboration
   - Use for quick prototyping

**Use Cases:**
- Testing generated code snippets
- Creating shareable examples
- Demonstrating concepts
- Quick prototyping without file creation

**Note:** The generated URLs can be quite large since the code is embedded in the URL itself.

### Workflow 4: Building a Svelte Component with AI

Complete workflow combining all tools to build a Svelte component with AI assistance.

**Steps:**

1. **Describe your component requirements** to the AI assistant

2. **Fetch relevant documentation**:
   - AI uses `list-sections` to find relevant docs
   - AI uses `get-documentation` to fetch needed sections
   - Documentation informs the implementation approach

3. **Generate initial component code**:
   - AI writes the component based on requirements and docs
   - Uses Svelte 5 patterns and best practices

4. **Analyze and refine**:
   - AI uses `svelte-autofixer` to check the code
   - Reviews suggestions and issues
   - Applies fixes and improvements
   - Repeats until code is clean

5. **Test in playground** (optional):
   - AI uses `playground-link` to generate test URL
   - You can verify the component works as expected

6. **Write to file** in your project

**Example Request:**
"Create a counter component using Svelte 5 runes with increment and decrement buttons"

The AI will:
- Fetch documentation on $state and event handling
- Generate the component code
- Run autofixer to ensure best practices
- Optionally create a playground link for testing

## Available Tools

### list-sections

**Purpose:** Provides a list of all available documentation sections from svelte.dev

**When to use:**
- Before fetching documentation to see what's available
- To understand the structure of Svelte documentation
- To find relevant sections for your task

**Returns:** Array of documentation sections with:
- Section path/identifier
- Section title
- Use cases for when to reference this section

### get-documentation

**Purpose:** Retrieves full documentation content for specified sections

**Parameters:**
- `sections` (array): One or more section paths to fetch

**When to use:**
- After identifying relevant sections with `list-sections`
- When you need detailed information about Svelte features
- To get up-to-date API references

**Returns:** Complete documentation content for requested sections

**Best Practice:** Fetch multiple related sections in a single call when possible.

### svelte-autofixer

**Purpose:** Analyzes Svelte code using static analysis and provides suggestions

**Parameters:**
- `code` (string): The Svelte code to analyze

**When to use:**
- After generating Svelte component code
- To validate code follows best practices
- To catch common mistakes
- In an iterative loop until all issues are resolved

**Returns:** Analysis results with:
- Issues found (with severity levels)
- Suggestions for improvements
- Best practice recommendations

**Agentic Pattern:** Use in a loop - analyze, fix, analyze again until clean.

### playground-link

**Purpose:** Generates an ephemeral Svelte playground link with provided code

**Parameters:**
- `code` (string): The Svelte code to embed in the playground

**When to use:**
- Testing generated code without creating files
- Creating shareable examples
- Quick prototyping and experimentation
- Demonstrating concepts

**Returns:** URL to Svelte playground with code embedded

**Note:** Code is stored in the URL itself, resulting in potentially long URLs.

## Troubleshooting

### MCP Server Connection Issues

**Problem:** Svelte MCP server won't start or connect

**Symptoms:**
- Error: "Connection refused"
- Server not responding
- Tools not available

**Solutions:**

1. **Verify npx is available:**
   ```bash
   npx --version
   ```
   If not found, update npm: `npm install -g npm@latest`

2. **Test the server manually:**
   ```bash
   npx -y @sveltejs/mcp
   ```
   This should start the server and show it's running

3. **Check MCP configuration:**
   - Verify `.kiro/settings/mcp.json` has correct configuration
   - Ensure no typos in command or args
   - Restart Kiro after configuration changes

4. **Check internet connection:**
   - Server needs internet to fetch documentation
   - Verify you can access svelte.dev

### Tool Execution Errors

**Error:** "Failed to fetch documentation"

**Cause:** Network issues or invalid section path

**Solution:**
1. Check internet connection
2. Verify section path using `list-sections` first
3. Try fetching a different section to isolate the issue

---

**Error:** "Autofixer analysis failed"

**Cause:** Invalid Svelte code syntax or malformed input

**Solution:**
1. Verify the code is valid Svelte syntax
2. Check for unclosed tags or brackets
3. Ensure code is a complete component or module
4. Try with a simpler code example first

---

**Error:** "Playground link generation failed"

**Cause:** Code too large or contains invalid characters

**Solution:**
1. Reduce code size if possible
2. Check for special characters that might break URL encoding
3. Verify code is valid Svelte syntax

### Documentation Not Up-to-Date

**Problem:** Documentation seems outdated or missing new features

**Cause:** Cached documentation or server issue

**Solution:**
1. Restart the MCP server (reconnect in Kiro)
2. Verify you're using the latest version: `npx -y @sveltejs/mcp`
3. Check svelte.dev directly to confirm documentation exists
4. Report issue to Svelte team if documentation is genuinely missing

## Best Practices

### Documentation Fetching

- Always use `list-sections` before `get-documentation` to understand available content
- Fetch multiple related sections in a single call to reduce round trips
- Review section use cases to ensure you're fetching relevant documentation
- Don't fetch all documentation at once - be selective based on your task

### Code Analysis

- Run `svelte-autofixer` on all generated Svelte code before finalizing
- Use autofixer in an iterative loop until all issues are resolved
- Pay attention to severity levels - fix critical issues first
- Apply suggestions even if code "works" - they improve maintainability

### Svelte 5 Patterns

- Use runes ($state, $derived, $effect) instead of legacy reactivity
- Prefer snippets over slots for component composition
- Follow the suggestions from autofixer for Svelte 5 best practices
- Fetch Svelte 5 documentation sections when working with new features

### Playground Usage

- Use playground links for quick testing and sharing
- Be aware that URLs can be very long with complex code
- Don't rely on playground links for permanent storage
- Consider creating actual files for production code

### Agentic Workflows

- Combine tools in sequence: list → get docs → generate → autofix → playground
- Let the AI iterate on autofixer suggestions automatically
- Use documentation to inform code generation, not just for reference
- Leverage the specialized Svelte agent (if available) for .svelte file editing

## Configuration

**No additional configuration required** - the MCP server works out of the box after installation in Kiro.

**Optional Environment Variables:**

The Svelte MCP server doesn't require environment variables for basic operation. All configuration is handled through the MCP server setup.

**Server Reconnection:**

If you need to restart the MCP server:
1. Open the MCP Server view in Kiro
2. Find "svelte" in the server list
3. Click reconnect or restart

Changes to `.kiro/settings/mcp.json` will automatically trigger a server restart.

## Additional Resources

- **Official Documentation:** https://svelte.dev/docs/mcp
- **GitHub Repository:** https://github.com/sveltejs/mcp
- **Svelte Documentation:** https://svelte.dev/docs
- **npm Package:** https://www.npmjs.com/package/@sveltejs/mcp

---

**Package:** `@sveltejs/mcp`  
**MCP Server:** svelte
