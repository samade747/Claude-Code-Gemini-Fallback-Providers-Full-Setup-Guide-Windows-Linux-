<!-- ========================================= -->
<!-- ULTRA-FUTURISTIC HEADER (REPLACES OLD BLACK HEADER) -->
<!-- Paste this entire file into docs/index.md -->
<!-- ========================================= -->

<style>
/* Neon GRID background */
.neon-grid {
  background: #000;
  position: relative;
  overflow: hidden;
  padding: 70px 20px;
  border-bottom: 3px solid #0ff;
}

/* Grid lines */
.neon-grid::before {
  content: "";
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background-image:
        linear-gradient(rgba(0,238,255,0.06) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,238,255,0.06) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: gridMove 12s linear infinite;
  pointer-events: none;
}

/* Grid movement */
@keyframes gridMove {
  0% { transform: translateY(0); }
  100% { transform: translateY(50px); }
}

/* Floating particles */
@keyframes floatParticle {
  0% { transform: translateY(0) translateX(0); opacity: 0.9; }
  50% { transform: translateY(-20px) translateX(10px); opacity: 0.6; }
  100% { transform: translateY(0) translateX(0); opacity: 0.9; }
}

.particle {
  position: absolute;
  width: 10px;
  height: 10px;
  background: radial-gradient(circle, #00eaff, rgba(0,234,255,0.2));
  border-radius: 50%;
  filter: blur(4px);
  animation: floatParticle 6s ease-in-out infinite;
  pointer-events: none;
}

/* Glassmorphism card */
.glass-box {
  position: relative;
  display: inline-block;
  padding: 28px 32px;
  border-radius: 18px;
  background: rgba(0, 255, 255, 0.03);
  border: 1px solid rgba(0, 255, 255, 0.12);
  backdrop-filter: blur(8px);
  box-shadow: 0 8px 30px rgba(0,0,0,0.6);
  z-index: 2;
  text-align: center;
  max-width: 920px;
  width: 100%;
}

/* Profile image */
.profile-img {
  width: 132px;
  height: 132px;
  border-radius: 50%;
  border: 3px solid rgba(0, 234, 255, 0.9);
  box-shadow: 0 0 26px rgba(0,234,255,0.18);
  object-fit: cover;
}

/* Name glow */
.name-glow {
  font-size: 48px;
  font-weight: 800;
  color: #e6ffff;
  margin: 16px 0 6px;
  text-shadow: 0 0 12px #00eaff, 0 0 30px #00b8ff;
}

/* Typing animation */
.typing {
  color: #9fe6ff;
  font-size: 20px;
  white-space: nowrap;
  overflow: hidden;
  border-right: 2px solid #9fe6ff;
  width: 0;
  display: inline-block;
  animation: typing 4.5s steps(30, end) infinite, blink 0.9s step-end infinite;
  margin-bottom: 14px;
}

@keyframes typing {
  0% { width: 0; }
  45% { width: 260px; }
  100% { width: 0; }
}
@keyframes blink {
  50% { border-color: transparent; }
}

/* Navbar */
.navbar {
  margin-top: 20px;
  display: flex;
  justify-content: center;
  gap: 16px;
  flex-wrap: wrap;
}

.navbar a {
  color: #aef0ff;
  text-decoration: none;
  font-weight: 600;
  padding: 8px 14px;
  border-radius: 8px;
  transition: all 0.25s ease;
  border-bottom: 2px solid transparent;
}

.navbar a:hover {
  color: #ffffff;
  background: rgba(255,255,255,0.02);
  border-bottom: 2px solid #00eaff;
  transform: translateY(-2px);
}

/* Social icons row */
.social-links {
  margin-top: 18px;
}

.social-links a {
  display: inline-block;
  margin: 0 10px;
  text-decoration: none;
  color: #9fe6ff;
  transition: color 0.2s;
}
.social-links a img { vertical-align: middle; width: 28px; height: 28px; filter: drop-shadow(0 0 6px rgba(0,234,255,0.12)); }

</style>

<div class="neon-grid">
  <!-- PARTLES (positions randomized; you can add/remove) -->
  <div class="particle" style="top:8%; left:18%; animation-delay:0s;"></div>
  <div class="particle" style="top:28%; left:72%; animation-delay:0.9s;"></div>
  <div class="particle" style="top:62%; left:45%; animation-delay:1.6s;"></div>
  <div class="particle" style="top:46%; left:12%; animation-delay:2.3s;"></div>
  <div class="particle" style="top:14%; left:86%; animation-delay:3.1s;"></div>

  <div style="display:flex; justify-content:center; padding:40px 16px;">
    <div class="glass-box">

      <!-- profile image (uses GitHub username .png endpoint) -->
      <img class="profile-img" src="https://github.com/samade747.png" alt="Samad Profile">

      <!-- name -->
      <div class="name-glow">Samad</div>

      <!-- typing subtitle -->
      <div class="typing">AI Agents Developer</div>

      <!-- navbar -->
      <div class="navbar">
        <a href="#guide">Guide</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
        <a> ![Profile Views](https://komarev.com/ghpvc/?username=samade747&style=flat-square)</a>
      </div>

      <!-- social links -->
      <div class="social-links">
        <a href="https://github.com/samade747" target="_blank" title="GitHub">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="GitHub">
        </a>
        <a href="https://www.linkedin.com/in/samaddeveloper-aiagents-developer/" target="_blank" title="LinkedIn">
          <img src="https://cdn-icons-png.flaticon.com/512/174/174857.png" alt="LinkedIn">
        </a>
      </div>

    </div>
  </div>
</div>

---

# 🚀 Claude Code + Gemini + Fallback Providers — Full Setup Guide  
### Works on: **Windows (PowerShell)** + **Linux/macOS (bash/zsh)**  
### Includes: Claude-Code, Claude-Code-Router (CCR), Gemini, OpenAI, Qwen, Grok, OpenRouter & MCP Server Guide

---

# 📌 1. Requirements

- **Node.js v18+** → https://nodejs.org  
  Check:  
  ```bash
  node --version


# 🚀 Claude Code + Gemini + Fallback Providers — Full Setup Guide  
### Works on: **Windows (PowerShell)** + **Linux/macOS (bash/zsh)**  
### Includes: Claude-Code, Claude-Code-Router (CCR), Gemini, OpenAI, Qwen, Grok, OpenRouter & MCP Server Guide

---

# 📌 1. Requirements

- **Node.js v18+** → https://nodejs.org  
  Check:  
  ```bash
  node --version




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


<img src="https://gh-pixels.vercel.app/api/visitor?repo=samade747" />


![Profile Views](https://komarev.com/ghpvc/?username=samade747&style=flat-square)


