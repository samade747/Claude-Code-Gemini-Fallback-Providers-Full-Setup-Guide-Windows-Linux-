<!-- HEADER SECTION (BLACK THEME) -->
<header style="text-align:center; padding: 40px 10px; background:#000; border-bottom: 2px solid #222;">
    <h1 style="margin:0; font-size: 42px; font-weight:700; color:#fff;">
        Samad
    </h1>

    <p style="margin:14px 0; font-size:20px;">
        <a href="https://github.com/samade747" target="_blank" 
           style="text-decoration:none; color:#4da6ff; font-weight:600;">
            GitHub
        </a>
        &nbsp;•&nbsp;
        <a href="https://www.linkedin.com/in/samaddeveloper-aiagents-developer/" target="_blank" 
           style="text-decoration:none; color:#4da6ff; font-weight:600;">
            LinkedIn
        </a>
    </p>
</header>




# 🚀 Claude Code + Gemini + Fallback Providers — Full Setup Guide  
### Works on: **Windows (PowerShell)** + **Linux/macOS (bash/zsh)**  
### Includes: Claude-Code, Claude-Code-Router (CCR), Gemini, OpenAI, Qwen, Grok, OpenRouter & MCP Server Guide

---

# 📌 1. Requirements

- **Node.js v18+** → https://nodejs.org  
  Check:  
  ```bash
  node --version
  ```
- npm (comes with Node.js)
- API keys:
  - Google Gemini → https://aistudio.google.com
  - (Optional) OpenAI, Qwen, Grok (xAI), OpenRouter
- Terminal:
  - Windows → **PowerShell**
  - Linux/macOS → **bash/zsh**

---

# 🟦 2. Windows Setup (PowerShell)

## ✅ STEP 1 — Install tools
```powershell
npm install -g @anthropic-ai/claude-code
npm install -g @musistudio/claude-code-router
```

## ✅ STEP 2 — Create config folders
```powershell
mkdir "$env:USERPROFILE\.claude-code-router"
mkdir "$env:USERPROFILE\.claude"
```

## ✅ STEP 3 — Create config.json
```powershell
notepad "$env:USERPROFILE\.claude-code-router\config.json"
```

Paste the following minimal **Gemini** config:

```json
{
  "LOG": true,
  "LOG_LEVEL": "info",
  "HOST": "127.0.0.1",
  "PORT": 3456,
  "API_TIMEOUT_MS": 600000,
  "Providers": [
    {
      "name": "gemini",
      "api_base_url": "https://generativelanguage.googleapis.com/v1beta/models/",
      "api_key": "$GOOGLE_API_KEY",
      "models": ["gemini-2.5-flash", "gemini-2.0-flash"],
      "transformer": { "use": ["gemini"] }
    }
  ],
  "Router": {
    "default": "gemini,gemini-2.5-flash",
    "background": "gemini,gemini-2.5-flash",
    "think": "gemini,gemini-2.5-flash",
    "longContext": "gemini,gemini-2.5-flash",
    "longContextThreshold": 60000
  }
}
```

Save & close.

## ✅ STEP 4 — Add your Google API Key
```powershell
[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'YOUR_KEY_HERE', 'User')
```

Restart PowerShell → verify:
```powershell
echo $env:GOOGLE_API_KEY
```

---

# 🟧 3. Linux / macOS Setup

## Install tools
```bash
npm install -g @anthropic-ai/claude-code @musistudio/claude-code-router
```

## Create folders
```bash
mkdir -p ~/.claude-code-router ~/.claude
```

## Create config.json
```bash
cat > ~/.claude-code-router/config.json << 'EOF'
{
  "LOG": true,
  "LOG_LEVEL": "info",
  "HOST": "127.0.0.1",
  "PORT": 3456,
  "API_TIMEOUT_MS": 600000,
  "Providers": [
    {
      "name": "gemini",
      "api_base_url": "https://generativelanguage.googleapis.com/v1beta/models/",
      "api_key": "$GOOGLE_API_KEY",
      "models": ["gemini-2.5-flash", "gemini-2.0-flash"],
      "transformer": { "use": ["gemini"] }
    }
  ],
  "Router": {
    "default": "gemini,gemini-2.5-flash",
    "background": "gemini,gemini-2.5-flash",
    "think": "gemini,gemini-2.5-flash",
    "longContext": "gemini,gemini-2.5-flash",
    "longContextThreshold": 60000
  }
}
EOF
```

## Add API Key
zsh:
```bash
echo 'export GOOGLE_API_KEY="YOUR_KEY_HERE"' >> ~/.zshrc
source ~/.zshrc
```

bash:
```bash
echo 'export GOOGLE_API_KEY="YOUR_KEY_HERE"' >> ~/.bashrc
source ~/.bashrc
```

---

# 🌐 4. Multi-Provider Fallback Setup (Optional)

Replace your config with this to enable **Gemini + OpenAI + Qwen + Grok + OpenRouter**:

```json
{
  "LOG": true,
  "LOG_LEVEL": "info",
  "HOST": "127.0.0.1",
  "PORT": 3456,
  "API_TIMEOUT_MS": 600000,

  "Providers": [
    {
      "name": "gemini",
      "api_base_url": "https://generativelanguage.googleapis.com/v1beta/models/",
      "api_key": "$GOOGLE_API_KEY",
      "models": ["gemini-2.5-flash","gemini-2.0-flash"],
      "transformer": { "use": ["gemini"] }
    },
    {
      "name": "openai",
      "api_base_url": "https://api.openai.com/v1",
      "api_key": "$OPENAI_API_KEY",
      "models": ["gpt-5", "gpt-4o-mini"],
      "transformer": { "use": ["openai"] }
    },
    {
      "name": "qwen",
      "api_base_url": "https://api.qwen.ai",
      "api_key": "$QWEN_API_KEY",
      "models": ["qwen-2.5", "qwen-3-coder"],
      "transformer": { "use": ["qwen"] }
    },
    {
      "name": "grok",
      "api_base_url": "https://api.x.ai",
      "api_key": "$XAI_API_KEY",
      "models": ["grok-4.1-fast", "grok-3"],
      "transformer": { "use": ["grok"] }
    },
    {
      "name": "openrouter",
      "api_base_url": "https://openrouter.ai/api/v1/chat/completions",
      "api_key": "$OPENROUTER_API_KEY",
      "models": ["google/gemini-2.5-pro-preview","anthropic/claude-3.5-sonnet"],
      "transformer": { "use": ["openrouter"] }
    }
  ],

  "Router": {
    "default": "gemini,gemini-2.5-flash",
    "background": "openai,gpt-4o-mini",
    "think": "openai,gpt-5",
    "fallback": [
      "openai,gpt-4o-mini",
      "openrouter,google/gemini-2.5-pro-preview",
      "grok,grok-4.1-fast"
    ],
    "longContext": "grok,grok-4.1-fast",
    "longContextThreshold": 60000
  }
}
```

### Add extra keys (Windows)
```powershell
[System.Environment]::SetEnvironmentVariable('OPENAI_API_KEY','sk-xxxx','User')
[System.Environment]::SetEnvironmentVariable('QWEN_API_KEY','qwen-xxxx','User')
[System.Environment]::SetEnvironmentVariable('XAI_API_KEY','xai-xxxx','User')
[System.Environment]::SetEnvironmentVariable('OPENROUTER_API_KEY','or-xxxx','User')
```

---

# ▶️ 5. Daily Usage

## Terminal 1 — Start router
```powershell
ccr start
```
or Linux:
```bash
ccr start
```

Wait for:
```
✔ Service started successfully
```

## Terminal 2 — Use Claude
```bash
ccr code
```
or:
```bash
eval "$(ccr activate)"
claude
```

Test:
```
hi
```

---

# 🧩 6. MCP Server Setup (Optional)

## Install MCP SDK
```bash
python -m venv .venv
source .venv/bin/activate
pip install modelcontextprotocol
```

## Example MCP server (`mcp_server.py`)
```python
from modelcontextprotocol import FastMCP

mcp = FastMCP()

@mcp.tool()
async def list_files(path: str = "."):
    import os
    return "
".join(os.listdir(path))

if __name__ == "__main__":
    mcp.run(transport="stdio")
```

Run:
```bash
python mcp_server.py
```

---

# 🔐 7. Security Checklist
- Use environment variables; **never** store API keys in config.json.
- Keep CCR on `127.0.0.1`.
- Use only trusted MCP servers.
- Rotate API keys when unsure.

---

# 🎉 Setup Complete!
You now have:
- Claude Code  
- Claude Router  
- Gemini  
- Multi-provider fallback  
- MCP server support  

Need an auto-installer script? Just ask!
