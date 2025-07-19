# Perplexity Pro MCP - Setup Instructions

## 📦 **Installation Guide**

### Option 1: NPM Package (Recommended)

```bash
# Quick install
npx @mlllm/perplexity-pro-mcp

# Or install globally
npm install -g @mlllm/perplexity-pro-mcp
```

### Option 2: GitHub Repository

```bash
# Clone and install
git clone https://github.com/sergekostenchuk/perplexity-pro-mcp.git
cd perplexity-pro-mcp
npm install
npm run build
npm run install-local
```

### Option 3: Manual Configuration

1. **Download the release:**
   ```bash
   curl -L https://github.com/sergekostenchuk/perplexity-pro-mcp/archive/v2.0.0.tar.gz | tar -xz
   cd perplexity-pro-mcp-2.0.0
   ```

2. **Install dependencies:**
   ```bash
   npm install
   npm run build
   ```

3. **Configure Claude Desktop manually:**
   
   **macOS/Linux:**
   ```bash
   # Edit the config file
   code ~/.config/claude-desktop/claude_desktop_config.json
   ```
   
   **Windows:**
   ```bash
   # Edit the config file
   notepad %APPDATA%\Claude\claude_desktop_config.json
   ```

4. **Add MCP server configuration:**
   ```json
   {
     "mcpServers": {
       "perplexity-pro": {
         "command": "node",
         "args": ["/full/path/to/perplexity-pro-mcp/dist/index.js"],
         "env": {
           "PERPLEXITY_API_KEY": "your-perplexity-api-key-here"
         }
       }
     }
   }
   ```

## 🔑 **API Key Setup**

1. **Get Perplexity API Key:**
   - Visit [Perplexity API Settings](https://www.perplexity.ai/settings/api)
   - Create new API key
   - Copy the key (starts with `pplx-`)

2. **Set Environment Variable:**
   ```bash
   # Add to your shell profile (.bashrc, .zshrc, etc.)
   export PERPLEXITY_API_KEY="your-api-key-here"
   ```

3. **Test the key:**
   ```bash
   curl -H "Authorization: Bearer $PERPLEXITY_API_KEY" \
        https://api.perplexity.ai/chat/completions \
        -d '{"model":"pplx-7b-online","messages":[{"role":"user","content":"test"}]}'
   ```

## 🔧 **Configuration Options**

### Claude Desktop Config

```json
{
  "mcpServers": {
    "perplexity-pro": {
      "command": "node",
      "args": ["/path/to/dist/index.js"],
      "env": {
        "PERPLEXITY_API_KEY": "pplx-your-key",
        "DEBUG": "perplexity:*",          // Optional: Enable debug logs
        "NODE_ENV": "production",         // Optional: Environment
        "MAX_CONNECTIONS": "5",           // Optional: Connection pool size
        "CACHE_TTL": "300"               // Optional: Cache TTL in seconds
      }
    }
  }
}
```

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `PERPLEXITY_API_KEY` | - | **Required** API key |
| `DEBUG` | - | Debug logging (`perplexity:*`) |
| `NODE_ENV` | `production` | Environment mode |
| `MAX_CONNECTIONS` | `5` | HTTP connection pool size |
| `CACHE_TTL` | `300` | Default cache TTL (seconds) |
| `TIMEOUT` | `30000` | Request timeout (ms) |

## ✅ **Verification**

1. **Check Claude Desktop:**
   - Restart Claude Desktop
   - Look for MCP server in status
   - Should show "perplexity-pro: Connected"

2. **Test basic command:**
   ```
   search("Hello world")
   ```

3. **Test advanced command:**
   ```
   multiSearch(["AI news", "Tech trends"])
   ```

## 🚨 **Troubleshooting**

### Common Issues

#### "MCP server not found"
```bash
# Check Claude Desktop config location
ls ~/.config/claude-desktop/
# or
ls %APPDATA%\Claude\

# Verify config syntax
cat ~/.config/claude-desktop/claude_desktop_config.json | jq .
```

#### "API key invalid"
```bash
# Test API key manually
curl -H "Authorization: Bearer $PERPLEXITY_API_KEY" \
     https://api.perplexity.ai/chat/completions \
     -d '{"model":"pplx-7b-online","messages":[{"role":"user","content":"test"}]}'
```

#### "Connection timeout"
```bash
# Check network connectivity
ping api.perplexity.ai

# Test HTTPS access
curl -I https://api.perplexity.ai
```

#### "Module not found"
```bash
# Reinstall dependencies
npm clean-install
npm run build

# Check dist directory
ls -la dist/
```

### Debug Mode

Enable detailed logging:

```bash
# Set debug environment
export DEBUG=perplexity:*
export NODE_ENV=development

# Restart Claude Desktop with debug output
```

### Log Locations

- **Claude Desktop logs:** `~/Library/Logs/Claude/` (macOS)
- **MCP server logs:** Check Claude Desktop console
- **Custom logs:** Set `DEBUG=perplexity:*`

## 🔄 **Updates**

### Automatic Updates

```bash
# Update to latest version
npm update -g @mlllm/perplexity-pro-mcp
```

### Manual Updates

```bash
# Check current version
perplexity-pro-mcp --version

# Update from GitHub
git pull origin main
npm install
npm run build
```

## 📋 **System Requirements**

- **Node.js:** v20+ (required)
- **NPM:** v10+ (recommended)
- **Claude Desktop:** Latest version
- **OS:** macOS, Linux, Windows
- **RAM:** 512MB+ available
- **Network:** HTTPS access to api.perplexity.ai

## 🎯 **Performance Tuning**

### Connection Pool
```json
{
  "env": {
    "MAX_CONNECTIONS": "10",    // Increase for heavy usage
    "TIMEOUT": "60000"          // Increase for slow networks
  }
}
```

### Caching
```json
{
  "env": {
    "CACHE_TTL": "600",         // 10 minutes cache
    "CACHE_SIZE": "200"         // Max cache entries
  }
}
```

### Memory Usage
```json
{
  "env": {
    "NODE_OPTIONS": "--max-old-space-size=1024"  // Limit memory to 1GB
  }
}
```

---

## 📞 **Support**

- **Issues:** [GitHub Issues](https://github.com/sergekostenchuk/perplexity-pro-mcp/issues)
- **Discussions:** [GitHub Discussions](https://github.com/sergekostenchuk/perplexity-pro-mcp/discussions)
- **Documentation:** [README.md](https://github.com/sergekostenchuk/perplexity-pro-mcp/blob/main/README.md)

**Version:** 2.0.0  
**Last Updated:** July 2025