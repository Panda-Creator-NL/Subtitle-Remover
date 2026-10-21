# 🍿 SUB-GONE (Unraid WebUI) 🎬

A powerful, lightweight WebUI to automatically scan and strip embedded (muxed/hardcoded) subtitle streams from your `.mkv` and `.mp4` media library directly on your Unraid server. Built with Python, Flask, Bash, and `FFmpeg`, this Docker container cleans up unwanted internal subtitles at lightning speed without re-encoding your video or audio tracks.

## ✨ Features
*   **Lossless & Lightning Fast Stripping:** Utilizes `ffprobe` and `ffmpeg` (`-c copy -sn`) under the hood to remove internal subtitle tracks without touching video or audio quality.
*   **Background Engine & Live Logs:** Start batch scanning and safely close your browser. The app runs independently in the background while providing a real-time live logbook upon reopening, plus the ability to stop the process at any time.
*   **Smart Folder Filtering:** Scans your target folder (e.g., `/media`) for `.mkv` and `.mp4` files while automatically skipping `Featurettes`, `Extras`, and `Trailers` directories.
*   **Safe File Handling & Unraid Permissions:** Processes videos via a temporary file first—if anything goes wrong, your original file remains untouched. Upon success, it automatically applies Unraid-friendly permissions (`chown 99:100` and `chmod 0666`).
*   **Discord Progress & Completion Alerts:** Connect your Discord Webhook to receive automatic progress updates every 100 processed files and a final notification when the entire scan is complete.
*   **Automatic UI Localization:** The WebUI and live log output automatically adapt to your browser's language (supports **Dutch** 🇳🇱 and **English** 🇬🇧 out of the box!).

## 💬 Support & Feedback
**Found a bug or have an idea?** If you have suggestions for new features or run into any issues while scanning your library, please let me know! You can reach out by creating an Issue on this GitHub repository, or use the **📩 Contact & Support** button directly in the WebUI (`https://pandaboynl-support-page.duckdns.org`). I am always looking to improve the app!

## 📦 Unraid Installation
1. Go to the **Apps** tab (Community Applications) in Unraid.
2. Search for **SUB-GONE**.
3. Click **Install**.
4. **Important:** Map your media share to `/media` and optionally fill in your `DISCORD_WEBHOOK` URL in the template settings. By default, this app uses port `5000`. If port `5000` is already in use on your server, please change the 'WebUI Port' (Host Port) during installation to another free port (e.g., `5005`).

## ☕ Support & Buy Me a Coffee 
This project is developed with passion in my free time. If you enjoy using SUB-GONE and want to help keep the app running, updated, and bug-free, please consider buying me a coffee!

👉 **Buy me a coffee via PayPal (PandaBoyNL)** [https://www.paypal.com/paypalme/PandaBoyNL](https://www.paypal.com/paypalme/PandaBoyNL)

Thank you for your support! ❤️

## 🛠️ Manual Docker Installation
If you prefer to run it via CLI:

```bash
docker run -d \
  --name sub-gone \
  -p 5000:5000 \
  -v /mnt/user/Media:/media \
  -e DISCORD_WEBHOOK="optional_discord_webhook_url" \
  pandaboynl/sub-gone:latest
```
