# Vaultwarden without Docker
[Vaultwarden](https://github.com/dani-garcia/vaultwarden) is an open source unofficial Bitwarden compatible server written in Rust. It works great, but the developers distribute it as a docker image. It seemed overkill to have docker running around it. 

This repo contains the binaries extracted directly from [docker images](https://hub.docker.com/r/vaultwarden/server).

## Installation

#### Dependencies
```bash
sudo apt-get install libpq-dev libmariadb-dev openssl
```

#### Installing binaries
Choose a binary appropriate for your CPU architecture from [releases](https://github.com/C10udburst/vaultwarden-no-docker/releases/tag/latest).

#### Installing web interface
Download and extract it to `web-vault` the web interface from [here](https://github.com/dani-garcia/bw_web_builds/releases/latest).

#### Folder setup
This is how your installation dir should look like
```
.
├── data
├── vaultwarden
└── web-vault
    ├── 404
    ├── app
    ├── connectors
    ├── fonts
    ├── images
    ├── locales
    └── script
```

#### Configuring ports
By default vaultwarden listens on `127.0.0.1` on port `8000`. You can change that with `ROCKET_ADDRESS` and `ROCKET_PORT` variables.

#### Nginx setup (optional)
If you wish to run vaultwarden behind nginx proxy, look at the [vaultwarden wiki](https://github.com/dani-garcia/vaultwarden/wiki/Proxy-examples), but keep in mind that the default port is `8000`.

#### Creating a service
Create a `/etc/systemd/system/vaultwarden.service` file. Look at [the example config](./vaultwarden.ini) to see how to configure it.

Afterwards enable it with
```bash
sudo systemctl enable --now vaultwarden.service
```