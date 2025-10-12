# Twitch Drops Miner – Docker Edition 🐳

> Dockerized version of [DevilXD’s Twitch Drops Miner](https://github.com/DevilXD/TwitchDropsMiner), with zero-UI overhead and everything you need to AFK farm Twitch drops from inside a container.

---

### ✅ Synced with Upstream

This Docker project includes **all the latest updates** from [`DevilXD/TwitchDropsMiner`](https://github.com/DevilXD/TwitchDropsMiner).

Upstream commits are regularly merged, and new Docker images are built and published automatically — so you're always running the most current version, just containerized.

---

## 📌 Purpose

This container wraps **Twitch Drops Miner**, the well-loved desktop drop farming tool by [DevilXD](https://github.com/DevilXD/TwitchDropsMiner), to make it effortless to run on **servers, VPSs, NAS setups, headless devices**, or anything else that supports Docker.

It's entirely streamless — no video or audio is fetched — so you save bandwidth while still progressing active Twitch drop campaigns ✅

You just log in with your Twitch account, choose which games you want drops from, and let it run.

---

## 🔗 Links

- 🌐 Website: [twitchdropsminer.com](https://twitchdropsminer.com)
- 🧑‍💻 Github: [TwitchDropsMiner](https://nokodo.net/github/twitchdropsminer)
- 🐙 Original Project: [github.com/DevilXD/TwitchDropsMiner](https://github.com/DevilXD/TwitchDropsMiner)
- 🐳 Docker Hub: [`nokodo/twitchdropsminer`](https://nokodo.net/dockerhub/twitchdropsminer)
- 💻 Powered by: [nokodo](https://nokodo.net)

---

## 🧰 Usage (Quickstart with Docker Compose)

```yaml
services:
  twitchdropsminer:
    container_name: twitchdropsminer
    image: nokodo/twitchdropsminer:latest
    restart: on-failure
    pull_policy: always
    user: "568:568"
    ports:
      - "5800:5800"
    environment:
      - DARK_MODE=1
      - USER_ID=568
      - GROUP_ID=568
    volumes:
      - ./config:/config
      - cache:/cache

volumes:
  cache:
```

Then run:

```bash
docker compose up -d
```

Your container will start the miner with a web interface accessible at `http://localhost:5800`.

On first launch, you'll be prompted to log in using the Twitch device-code flow. Simply follow the instructions shown in the web interface.

---

## 🔒 Login & Account Linking

You need to have your Twitch account linked to the games you want drops for:  
👉 [https://www.twitch.tv/drops/campaigns](https://www.twitch.tv/drops/campaigns)

This container keeps your login persistent via a `cookies.jar` file inside your mounted `./config` folder.

**⚠️ Do not share your cookies file. It can be used to access your Twitch account.**

---

## ⚙️ Features

These are inherited directly from the base project:

- ✅ Streamless drop progress (bandwidth-friendly)
- ✅ Smart priority/exclusion system per game
- ✅ Always picks the best stream for each campaign
- ✅ Auto-restarts drop progress as new campaigns go live
- ✅ Up to 199 streams tracked via sharded websocket
- ✅ Runs completely headless – no GUI needed

---

## 🧠 Credits

All core mining logic and functionality comes from [DevilXD/TwitchDropsMiner](https://github.com/DevilXD/TwitchDropsMiner).

The Docker implementation and containerization work is based on [fireph/TwitchDropsMiner](https://github.com/fireph/TwitchDropsMiner).

This repo combines both efforts to provide a **Docker-focused build** that runs efficiently in headless environments 💖

Massive shoutout to:

- [@DevilXD](https://github.com/DevilXD) for the original application and ongoing development
- [@fireph](https://github.com/fireph) for the Alpine/Docker adaptation
- All translators, maintainers, and contributors 🙏

If you want to support the original author — [Buy Me A Coffee](https://www.buymeacoffee.com/DevilXD) / [Patreon](https://www.patreon.com/bePatron?u=26937862)

---

## ⚠️ Disclaimer

This image is unofficial and unaffiliated with Twitch.  
It simply automates what a real user could do — no scraping, spoofing, or abuse is involved.

Still: use at your own risk.
