# Steamed Wine [SteamCMD + WineHQ]

![PEON](https://github.com/the-peon-project/peon/blob/main/media/andre-kent-peon-turntable.jpeg)
Art by [André Kent - Artstation](https://www.artstation.com/artwork/W2E0RQ)
**This project owns no rights to the image above. Please link to the site and request them accordingly.**

[![Docker Pulls](https://img.shields.io/docker/pulls/umlatt/steamcmd-winehq.svg)](https://hub.docker.com/r/umlatt/steamcmd-winehq)
[![Docker Stars](https://img.shields.io/docker/stars/umlatt/steamcmd-winehq.svg)](https://hub.docker.com/r/umlatt/steamcmd-winehq)

## The Easy Game Server Manager

### Installation

> This can be deployed as a stand-alone container to run windows steam game servers. *Not yet tested in stand-alone mode (working as part of [Peon Project](https://github.com/the-peon-project/peon))

```bash
docker run -dit --name steamedwine -p [gameport_01]:[gameport_01] -p [gameport_02]:[gameport_02] -p [gameport_<n>]:[gameport_<n>] umlatt/steamcmd-winehq:latest
docker exec -it steamedwine bash
```

### [Peon Project](https://github.com/the-peon-project/peon)

An **OpenSource** project to assist gamers in self-deploying/managing game servers.\
Intended to be a one-stop-shop for game server deployment/management.\
If run on a public/paid cloud, it is architected to try to minimise costs (easy schedule/manage uptime vs downtime)\

### Peon SteamCMD + WineHQ

The [github](https://github.com/the-peon-project/peon-wartable/tree/master/containers/steamcmd-wine) repo for developing the container.

## State

> **INITIAL RELEASE**

Functionilty working as required (tested with VRising windows steam server)

## Version Info

Check [changelog](https://github.com/the-peon-project/peon-plans/blob/master/containers/steamcmd-wine/changelog.md) for more information

- Deployed with ``cm2network/steamcmd`` as a base image
- Added ``wine`` for windows emulation & ``xvfb`` for virtual console emulation (required for some wine apps when running in headless mode)

### Known Bugs

*N/A*

### Architecture/Rules

This is a base image for certain game servers that are not linux native. ``Use default [cm2network/steamcmd] if windows is not required (waaaaaaay more efficient))``

Source container provided by [Valve SteamCMD - Docker](https://developer.valvesoftware.com/wiki/SteamCMD#Docker)

### Feature Plan

#### *sprint 1.0.0*

- [x] Wine - Deploy windows game servers using wine

### Notes

#### When a **virtual** desktop is required by a WINE app

```bash
echo "Clean any existing /tmp/.X0-lock"
rm -rf /tmp/.X0-lock 2>&1
echo "Start Xvfb"
Xvfb :0 -screen 0 1024x768x16 &
echo "Start game server (Using 'DISPLAY=:0.0 ' as a prefix to wine)"
DISPLAY=:0.0 wine64 /path/to/gameserver/server_start.exe
```

## Support the Project

PEON is an open-source project that I am working on in my spare time (for fun).
However, if you still wish to say thanks, feel free to pick up a virtual coffee for me at Ko-fi.

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/K3K567ILJ)