# raspberry-pi-tailscale-server
# A secure remote-access server using Raspberry Pi, Tailscale, Ubuntu Server, Docker and Nginx Proxy Manager.

```text
raspberry-pi-tailscale-homelab/
│
├── README.md
│
├── docs/
│   ├── 01-architecture.md
│   ├── 02-raspberry-pi-setup.md
│   ├── 03-tailscale-exit-node.md
│   ├── 04-subnet-router.md
│   ├── 05-ubuntu-server-setup.md
│   ├── 06-nginx-proxy-manager.md
│   ├── 07-private-dns-and-https.md
│   └── 08-troubleshooting.md
│
├── diagrams/
│   └── network-architecture.png
│
├── screenshots/
│   ├── tailscale-devices.png
│   ├── exit-node.png
│   ├── nginx-proxy-manager.png
│   └── remote-access.png
│
└── LICENSE
```
# Project Overview 

This project demonstrates how I built a secure remote-access server using a Raspberry Pi, Tailscale VPN, Ubuntu Server, Docker and Nginx Proxy Manager.
The objective was to access and manage my home infrastructure remotely using a mobile phone or laptop without exposing my internal applications directly to the public internet.
The Raspberry Pi acts as both a Tailscale Exit Node and Subnet Router, allowing remote devices to access the home network and route internet traffic through the home internet connection.
Nginx Proxy Manager provides reverse proxy functionality, allowing access to self-hosted applications through domain names rather than IP addresses and port numbers.

# Architecture
# Network Design 

- Raspberry Pi: Tailscale Exit Node and Subnet Router.

- Ubuntu Server: Hosts Docker containers and self-hosted applications.

- Tailscale: Provides encrypted remote connectivity.

- Nginx Proxy Manager: Reverse proxy for internal applications.

- Private DNS: Resolves internal application domain names.

- Mobile Phone: Remote client connecting through Tailscale.

# Network Architecture Diagram 
```text
                REMOTE ACCESS
              Mobile Phone / Laptop
                       |
                  Mobile Data
                       |
                    Tailscale
                       |
              Raspberry Pi
          Exit Node + Subnet Router
                       |
                 Home Network
                       |
                Ubuntu Server
                       |
              Nginx Proxy Manager
                       |
        +--------------+--------------+
        |              |              |
    Portainer       Grafana        Nextcloud
        |              |              |
      Jellyfin      Other Docker Applications
```
# Technologies Used 

Technology                                Purpose

Raspberry Pi                              VPN gateway and subnet router

Ubuntu Server                             Home server infrastructure

Tailscale                                 Secure remote access

Docker                                    Application containerization

Docker Compose                            Container deployment

Nginx Proxy Manager                       Reverse proxy

Private DNS                               Internal domain resolution

SSH                                       Remote server administration
