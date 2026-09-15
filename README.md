# dhcp-office-network-packet-tracer
DHCP configuration and automatic IP address assignment using Cisco Packet Tracer
# DHCP Office Network – Cisco Packet Tracer

## Overview

This project demonstrates the configuration of a DHCP server for a small office network using Cisco Packet Tracer.

The goal is to automatically assign IPv4 addresses to client PCs instead of configuring each client manually.

## Network Topology

- 1 × Cisco 2911 Router
- 1 × Cisco 2960-24TT Switch
- 3 × PCs
- 1 × Server

Network structure:

**Router0 → Switch0 → PC0, PC1, PC2, Server0**

## IPv4 Addressing

| Device | IPv4 Address | Address Assignment | Default Gateway |
|---|---|---|---|
| Router0 | 192.168.1.1 | Static | — |
| Server0 | 192.168.1.20 | Static | 192.168.1.1 |
| PC0 | 192.168.1.100 | DHCP | 192.168.1.1 |
| PC1 | 192.168.1.101 | DHCP | 192.168.1.1 |
| PC2 | 192.168.1.102 | DHCP | 192.168.1.1 |

## DHCP Configuration

The DHCP service was configured on Server0.

### DHCP Pool

| Setting | Value |
|---|---|
| Pool Name | serverPool |
| Start IP Address | 192.168.1.100 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.1.1 |
| Maximum Users | 50 |

The server uses the static address **192.168.1.20** and provides DHCP services to the client PCs.

## Testing

The client PCs were switched from static IP configuration to DHCP.

DHCP was tested using:

- `ipconfig /release`
- `ipconfig /renew`
- `ipconfig`

The clients successfully received IP addresses from the DHCP pool.

### Connectivity Test

PC1 was assigned:

**192.168.1.101**

A ping test from PC1 to the default gateway was successful:

**PC1 → 192.168.1.1**

Result: **4 packets received, 0% packet loss.**

PC1 was also able to reach the server at:

**192.168.1.20**

## Troubleshooting

During the project, DHCP requests initially failed.

I checked the DHCP pool configuration and verified:

- DHCP service was enabled
- Default gateway was `192.168.1.1`
- DHCP start address was `192.168.1.100`
- Subnet mask was `255.255.255.0`
- Maximum users was `50`

After correcting the configuration, the PCs successfully received addresses through DHCP.

## Tools

- Cisco Packet Tracer
- DHCP
- IPv4
- ICMP / ping
- `ipconfig`

## What I Learned

Through this project I practiced configuring a DHCP server, creating a DHCP address pool, assigning IP addresses automatically and troubleshooting DHCP connectivity problems.

This project is part of my practical preparation for an Ausbildung as **Fachinformatikerin für Systemintegration (FISI)**.

## Project File

The Cisco Packet Tracer project file (`.pkt`) is included in this repository.
