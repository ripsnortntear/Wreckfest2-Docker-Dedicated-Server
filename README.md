Wreckfest 2 Docker Server

Run a headless Wreckfest 2 dedicated server in Docker using Wine for seamless Linux compatibility. 
This project provides an easy-to-deploy setup based on the nvitaterna/wreckfest2-docker-server:console image,
with fixes for display issues, logging, and configuration persistence.

Features

    Headless Operation: Uses Xvfb for virtual display, eliminating GUI requirements.
    Persistent Storage: Mounts volumes for configs, logs, and game files.
    Steam Integration: Automatic updates via SteamCMD.
    Customizable: Supports environment variables and config files for server settings (e.g., event loops, max players).
    Cross-Platform: Runs on any Docker-supported host (Linux, Windows, macOS).

Quick Start

    Clone this repo and navigate to the directory.
    Create host directories: `mkdir -p config logs wf2-server`. (copy your wreckfest2 game files to wf2-server folder)
    Add your server_config.scnf and event_loop.becl and default_loop.becl files to ./config.
    Run `docker compose up -d`. (docker-compose.yml and Dockerfile MUST be in same dir)
    Connect clients to your host's IP on UDP port 30100. (also shows up in server list)
    (If using UFW (and you should) run `ufw allow 30100/udp')

Requirements

    Docker and Docker Compose installed.
    Sufficient resources (e.g., 4GB RAM, multi-core CPU).
    Internet access for Steam updates.

Interactive Console Mode:

    Use docker compose attach wreckfest-server after the server has started.
    Use help to see commands

Inspired by https://hub.docker.com/r/nvitaterna/wreckfest2-docker-server -- check the base image for updates. 
Enjoy racing! 🏎️
