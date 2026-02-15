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
    Run `docker compose build --no-cache` 
    Run `docker compose up -d`. (docker-compose.yml and Dockerfile MUST be in same dir)
    Connect clients to your host's IP on UDP port 30100.
    (If using UFW (and you should) run `ufw allow 30100/udp')

Requirements

    Docker and Docker Compose installed.
    Sufficient resources (e.g., 4GB RAM, multi-core CPU).
    Internet access for Steam updates.

Warning:

    Not an issue. The error is not an error but a warning that the console is non-interactive.
    ```
    wreckfest-server-1  | Exception in thread Thread-1 (__loop):
    wreckfest-server-1  | Traceback (most recent call last):
    wreckfest-server-1  |   File "/usr/lib/python3.11/threading.py", line 1038, in _bootstrap_inner
    wreckfest-server-1  |     self.run()
    wreckfest-server-1  |   File "/usr/lib/python3.11/threading.py", line 975, in run
    wreckfest-server-1  |     self._target(*self._args, **self._kwargs)
    wreckfest-server-1  |   File "/home/steam/wrapper/lib/ConsoleWriter.py", line 36, in __loop
    wreckfest-server-1  |     userInput = input()
    wreckfest-server-1  |                 ^^^^^^^
    wreckfest-server-1  | EOFError: EOF when reading a line
    ```

Inspired by https://hub.docker.com/r/nvitaterna/wreckfest2-docker-server -- check the base image for updates. 
Enjoy racing! 🏎️
