# MCP for Unity

## Overview

This document explains how to install **MCP (Model Context Protocol)** so that you can directly connect and develop AI Agents inside Unity.

Using Unity’s **free Factory and Warehouse scenes**, we will use MCP to place robots in the scene and control their behavior.

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/9368f4cb-7b6b-42e6-91cb-d1e265f6fb93" />
<img width="1920" height="1017" alt="Image" src="https://github.com/user-attachments/assets/c0ab072c-8be0-46ff-af8c-efd49902ec55" />

### Sample Assets

* **Unity Warehouse (HDRP)**  
  https://assetstore.unity.com/packages/3d/environments/industrial/unity-warehouse-276394
* **Unity Factory (HDRP)**  
  https://assetstore.unity.com/packages/3d/environments/industrial/unity-factory-276400

### Steps

1. Install a GPT service  
2. Install Unity  
3. Install MCP for Unity  
4. Start development in Unity  

---

## AI Client Installation

Install a GPT-based service to be used as the MCP client.

![service-list](./imgs/03-MCP/2025-12-14%2009%2029%2008.png)

Supported services:

1. Google **Antigravity**
2. **Cursor**
3. **Claude Code**
4. OpenAI **Codex**

All of the above services have been tested and confirmed to work correctly.  
Performance depends on the **model** and whether you are using **free or paid plans**.  
All services provide free tiers, so you can start for free.

In this guide:
- **Cursor** will be used via the desktop app
- **Codex (OpenAI)** will be used via CLI / Terminal

---

### Installing Cursor

Just download and install:

1. https://cursor.com/download  
2. https://docs.cursor.com/ko/get-started/installation  

---

### Installing Codex

#### Windows (WSL)

https://developers.openai.com/codex/windows

1. Set up WSL
2. Press `Ctrl + R`
3. Run `cmd`
4. Enter WSL:
   ```bash
   wsl
   ```
5. Install NVM:
   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
   ```
6. Open a new WSL terminal and install Node.js:
   ```bash
   nvm install 22
   ```
7. Run Codex:
   ```bash
   codex
   ```

![wsl-install1](./imgs/03-MCP/2025-12-14%2009%2046%2054.png)  
![wsl-install2](./imgs/03-MCP/2025-12-14%2009%2047%2047.png)  
![wsl-install3](./imgs/03-MCP/2025-12-14%2009%2047%2059.png)

#### macOS

https://developers.openai.com/codex/cli

```bash
brew install codex
codex
```

---

## Unity Installation

### Install Unity Hub

https://docs.unity3d.com/hub/manual/InstallHub.html

### Install Unity Editor

https://unity.com/releases/editor/archive

As of today, versions up to **Unity 6000.3.1f1** are available.

For this guide, download:

* **Unity 6000.0.64f1**

Direct link:
```
unityhub://6000.0.64f1/5360b7cd7953
```

Version naming:
- `6000` → Unity 6
- `6000.0` → Unity 6.0
- `6000.3` → Unity 6.3

---

## Creating a Unity Project

### In Unity Hub

1. Open **Projects** → **New Project**
2. Confirm the installed Editor version
3. **Important:** Select **High Definition 3D (HDRP)** template
4. Set project name and location
5. Click **Create Project**

![start-newproject](./imgs/02-start/2025-12-14%2008%2044%2032.png)

### In Unity Editor

1. Open **Window → Package Manager**
2. Tabs overview:
   - **In Project** – assets in the current project
   - **Unity Registry** – assets provided by Unity
   - **My Assets** – assets you own
3. Add the free Warehouse asset:
   - https://assetstore.unity.com/packages/3d/environments/industrial/unity-warehouse-276394
   - Click **Add to My Assets**

![start-download](./imgs/02-start/2025-12-14%2009%2004%2010.png)

4. Back in Unity Editor:
   - Open **Package Manager**
   - Find **Unity Warehouse**
   - Click **Download**
   - After download, click **Import**
   - Confirm import

![start-import](./imgs/02-start/2025-12-14%2009%2012%2030.png)

---

## Installing and Configuring MCP for Unity

### Installation

1. Open **Window → Package Manager**
2. Click **+** → **Add package from git URL…**
3. Enter:
```
https://github.com/CoplayDev/unity-mcp.git?path=/MCPForUnity
```
4. After installation, open **Window → MCP for Unity**

![mcp-window-tap](./imgs/03-MCP/2025-12-14%2009%2025%2047.png)

---

### Configuration (Important)

1. **Settings**
   - Enable **Show Debug Logs**
2. **Connection**
   - Set **Transport** to `Stdio`
   - Click **Start Session**
   - Confirm the **green indicator**
3. **Client Configuration**
   - Select AI Agent (e.g. `Cursor`)
   - Click **Configure**
   - Confirm the **green indicator**

---

## Verification and Start

### In Unity

1. Open **Window → MCP for Unity**
2. Confirm:
   - Session status is green
   - Client Configuration status is green

![setting-green](./imgs/03-MCP/2025-12-14%2010%2026%2003.png)

### In Cursor

1. Open **Cursor Settings**
2. Go to **Tools & MCP**
3. Confirm:
   - `unityMCP` is listed
   - Status is green

### HDRP Note

The Unity Warehouse sample is built with **HDRP**.  
Make sure your project uses **HDRP**.

---

## Start Developing

If all indicators are green and the Unity project is open,
you can immediately start Unity development using LLM prompts.

---

## Example LLM Prompt

```text
I want to set up a factory warehouse in the currently open scene.
Search the Project window for available assets and place a warehouse building if one exists.
Then populate the interior with racks, pallets, and people to make the scene feel complete and realistic.
```
