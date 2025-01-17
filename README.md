# MCP Tools Guide

## Configuration Locations

Before setting up any tools, ensure you're updating the correct configuration file based on your client:

### Claude Desktop App:
```
~/Library/Application Support/Claude/claude_desktop_config.json
```

### Cline (VS Code Extension):
```
~/Library/Application Support/Code/User/globalStorage/saoudrizwan.claude-dev/settings/cline_mcp_settings.json
```

## Available Tools

1. **Filesystem** (@modelcontextprotocol/server-filesystem)
   - File operations (read, write, list, search)
   - Directory management
   - Configuration template:
   ```json
   "filesystem": {
     "command": "npx",
     "args": [
       "-y",
       "@modelcontextprotocol/server-filesystem",
       "/path/to/allowed/directory1",
       "/path/to/allowed/directory2"
     ]
   }
   ```

2. **SQLite** (mcp-server-sqlite)
   - Database operations
   - Query execution
   - Configuration template:
   ```json
   "sqlite": {
     "command": "uvx",
     "args": [
       "mcp-server-sqlite",
       "--db-path",
       "/path/to/database.db"
     ]
   }
   ```

3. **Brave Search** (@modelcontextprotocol/server-brave-search)
   - Web and local search capabilities
   - Configuration template:
   ```json
   "brave-search": {
     "command": "npx",
     "args": [
       "-y",
       "@modelcontextprotocol/server-brave-search"
     ],
     "env": {
       "BRAVE_API_KEY": "YOUR_API_KEY"
     }
   }
   ```

4. **GitHub** (@modelcontextprotocol/server-github)
   - Repository management
   - Code access and search
   - Issue tracking
   - Important Notes:
     * For pushing multiple files, use `push_files` instead of `create_or_update_file`
     * Repository must exist before pushing files
     * Token needs appropriate permissions (Contents: Read & write)
   - Configuration template:
   ```json
   "github": {
     "command": "npx",
     "args": [
       "-y",
       "@modelcontextprotocol/server-github"
     ],
     "env": {
       "GITHUB_PERSONAL_ACCESS_TOKEN": "YOUR_TOKEN_HERE"
     }
   }
   ```

5. **Puppeteer** (@modelcontextprotocol/server-puppeteer)
   - Browser automation
   - Web scraping
   - Configuration template:
   ```json
   "puppeteer": {
     "command": "npx",
     "args": [
       "-y",
       "@modelcontextprotocol/server-puppeteer"
     ],
     "env": {
       "DEBUG": "puppeteer:*",
       "PUPPETEER_EXECUTABLE_PATH": "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
     }
   }
   ```

6. **YouTube Server** (@chrishayuk/mcp-youtube-server)
   - Video transcript fetching
   - Configuration template:
   ```json
   "mcp-youtube-server": {
     "command": "uvx",
     "args": [
       "@chrishayuk/mcp-youtube-server",
       "fetch-transcript",
       "VIDEO_ID"
     ],
     "env": {
       "VIDEO_ID": "YOUR_VIDEO_ID"
     }
   }
   ```

7. **Home Assistant** (@modelcontextprotocol/server-homeassistant)
   - Home automation control and monitoring
   - Device state management
   - Service calls and automation
   - Configuration template:
   ```json
   "homeassistant": {
     "command": "uvx",
     "args": [
       "@modelcontextprotocol/server-homeassistant"
     ],
     "env": {
       "HASS_URL": "YOUR_HASS_URL",
       "HASS_TOKEN": "YOUR_TOKEN"
     }
   }
   ```

## Working Tools (as of January 2025)

### Confirmed Working
1. Brave Search (Web & Local Search)
2. Filesystem (File Operations)
3. SQLite (Database)
4. GitHub (Full functionality)
5. Puppeteer (Browser Automation)
6. YouTube Server (Transcripts)
7. Home Assistant (Device control)

### GitHub Tool Notes
- Successfully creates private repositories
- Handles multiple file pushes
- Requires appropriate token permissions:
  * Actions (Read & write)
  * Administration (Read & write)
  * Contents (Read & write)
  * Metadata (Read-only)
  * Pull requests (Read & write)
  * Workflows (Read & write)

### Home Assistant Tool Notes
- Successfully connects to local or remote Home Assistant instances
- Supports all Home Assistant service calls
- Requires:
  * Valid Home Assistant URL
  * Long-Lived Access Token with appropriate permissions
  * Network access to Home Assistant instance

## Installation and Configuration

1. Install the desired server package:
   ```bash
   npm install @modelcontextprotocol/server-name
   ```

2. Add the configuration to your client's config file (see Configuration Locations above)

3. Restart your client (Claude Desktop or Cline)

4. Test the functionality with a simple command

## Common Issues

1. **Command not found**
   - Try switching between `npx` and `uvx`
   - Verify package installation
   - Check command spelling

2. **Connection errors**
   - Verify environment variables
   - Check network connectivity
   - Ensure service/API is accessible

_Last updated: January 17, 2025_