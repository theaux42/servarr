# Servarr Stack

A simple, self-hosted Docker Compose stack for the “Servarr” ecosystem: a family of media management apps that automate discovering, downloading, and organizing **your own** media library. This setup routes all media-related traffic through a VPN container and keeps each service isolated behind that gateway.

## What’s in the stack?

Each service below plays a specific role in the workflow. All containers share the Gluetun network, so they are reachable through the ports mapped on that container.

- **Gluetun** — VPN client and network gateway (WireGuard/OpenVPN). Every other container uses its network to keep media traffic inside the VPN tunnel.
- **Jellyseerr** — Friendly request management UI so users can request movies/series, which are then sent to Radarr/Sonarr.
- **qBittorrent** — Download client used by the automation tools to fetch content.
- **Flaresolverr** — Helper for indexers behind Cloudflare challenges; used by Prowlarr when required.
- **Prowlarr** — Indexer manager that centralizes search providers and syncs them to Sonarr/Radarr.
- **Sonarr** — TV series manager that monitors, grabs, renames, and organizes episodes.
- **Radarr** — Movie manager that monitors, grabs, renames, and organizes films.
- **Ygege** — YGG/YggTorrent helper service that maintains authentication for compatible indexers.
- **Qui** — qBittorrent companion service used to connect and manage qBittorrent from the stack.

## Quick configuration

1. Copy `.env.exemple` to `.env` and fill in the required values (VPN, timezone, qBittorrent, and YGG credentials).
2. Start the stack:

```bash
docker compose up -d
```

## ⚠️ Legal & anti‑piracy notice

This stack is intended for **legal, personal use only** (e.g., managing media you own or are authorized to download). **Do not use it to infringe copyrights or access pirated content.** Piracy is illegal in many countries and can carry serious consequences. You are solely responsible for complying with local laws and the terms of the services you use. The maintainers of this repository do **not** condone piracy or unlawful use.
