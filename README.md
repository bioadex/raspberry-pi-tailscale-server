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

## Security Considerations

Do not expose internal Docker application ports unnecessarily.

Use Tailscale authentication and device access controls.

Keep Ubuntu Server and Raspberry Pi updated.

Use HTTPS for web applications.

Restrict access to the Nginx Proxy Manager administration interface.

Never publish API tokens, passwords, private keys or authentication credentials.

Avoid publishing private IP addresses, personal DNS records or sensitive network screenshots.

## Troubleshooting

Some of the challenges encountered during implementation included:

DNS resolution issues after reinstalling Tailscale.

Configuring persistent IP forwarding on Raspberry Pi.

Combining Exit Node functionality with subnet routing.

Accessing Ubuntu Server through its original LAN IP from remote devices.

Configuring private DNS and reverse proxy access.

Using whatmyip.com to check if the ip address change 

These issues were resolved by checking DNS configuration, enabling IP forwarding, advertising the appropriate Tailscale routes and configuring private DNS.

## Final Result

The completed infrastructure allows remote access to the home lab from a mobile phone or laptop.

The Raspberry Pi provides secure VPN connectivity, while Ubuntu Server hosts the applications and Nginx Proxy Manager provides convenient domain-based access.

This project demonstrates practical experience with Linux administration, networking, VPNs, Docker, reverse proxies and infrastructure security.

Future Improvements

Infrastructure automation using Ansible.

Monitoring using Prometheus and Grafana.

Automated backup and recovery.

Infrastructure deployment using Terraform.

Improved access control and security monitoring.

## Photo 
1. Verify IP address
<img width="1289" height="719" alt="image" src="https://github.com/user-attachments/assets/bf2c9431-b0aa-4fe2-bc94-9cdc34b240c7" />
2. Docker application
<img width="1881" height="940" alt="image" src="https://github.com/user-attachments/assets/cb30184a-90f8-4b2b-a5f4-51713878dd69" /> 
3. Nginx Proxy Manager 
<img width="1202" height="908" alt="image" src="https://github.com/user-attachments/assets/6bef44e9-85aa-4532-bfc6-5a7e3185d433" />
4. Tailscale Dashboard
<img width="1843" height="601" alt="image" src="https://github.com/user-attachments/assets/1b8f84cc-e5db-480b-bb53-8a058b3fa99d" />
5. Pihole 
<img width="1248" height="725" alt="image" src="https://github.com/user-attachments/assets/698c8c1b-53a7-4e6a-b3e9-19a56a003147" />
6.Monitoring
<img width="1891" height="940" alt="image" src="https://github.com/user-attachments/assets/bcef5bb6-3d96-4836-8190-00295ab1b46a" />






