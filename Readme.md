

# **🎵 Tunzy – Your SoundCloud, Everywhere**

**Take control of your SoundCloud library. Sync, download, and stream your favorite music anywhere, anytime.**

Tunzy runs as a **lightweight Docker container**, making it easy to deploy on:

-   **Local machines** 💻
    
-   **Home servers** 🏠
    
-   **VPS providers** ☁️
    
-   **Cloud instances** 🌐
    

----------

## 🚀 Features

-   **Instant sync** of playlists and liked tracks from SoundCloud ✅
    
-   **Download and store tracks locally** for offline playback 💾
    
-   **Stream tracks directly** from your server 🎶
    
-   **Multi-architecture Docker image** (AMD64 + ARM64) ⚡
    
-   **Lightweight & ready-to-run** with minimal dependencies 🐳
    

----------

## 📦 Quick Start

**1. Pull the Docker image:**

```bash
docker pull balckhole/tunzy:latest

```

**2. Run Tunzy:**

```bash
docker run -d \
  -p 18000:8000 \
  -v tunzy-data:/data \
  --name tunzy \
  --restart unless-stopped \
  balckhole/tunzy:latest

```

**3. Open the dashboard:**

```
http://localhost:18000

```

Or on a remote server:

```
http://YOUR_SERVER_IP:18000

```

> Make sure port **18000** is open in your firewall or cloud security group.

----------

## 🔑 Connect Your SoundCloud Account

Tunzy uses your **SoundCloud OAuth token**. You can get it in two ways:

### 1️⃣ From the Network Tab

1.  Log in to [SoundCloud](https://soundcloud.com/).
    
2.  Open **Developer Tools → Network tab** → reload the page.
    
3.  Find requests to `api-v2.soundcloud.com` or `/you/sets`.
    
4.  Check the **Headers** → look for:
    

```
Authorization: OAuth <your-token-here>

```

5.  Copy the token and paste it into the Tunzy dashboard.
    

### 2️⃣ From Application / Storage (Cookies)

1.  Open **Developer Tools → Application / Storage → Cookies → soundcloud.com**
    
2.  Find the cookie named:
    

```
oauth_token

```

3.  Copy it into your dashboard.
    

> ⚠️ Keep this token private—it grants access to your account.

----------

## 💾 Data Persistence

All downloads, database, and metadata are stored in `/data`. Use a Docker volume to persist your library:

```bash
-v tunzy-data:/data

```

> Your library remains safe even if the container is removed.

----------

## 🔧 Ports

-   **Container port:** 8000
    
-   **Host port:** 18000
    

```bash
-p 18000:8000

```

----------
## 🏗 Built For Speed & Reliability

-   **FastAPI backend** – sync & download engine ⚡
    
-   **React dashboard** – manage your library visually 🖥️
    
-   **SQLite database** – track progress and metadata 🗄️
    
-   **FFmpeg** – streaming & audio processing 🎧
    
-   **Multi-stage Docker build** – tiny, optimized, ready to run 🐳
