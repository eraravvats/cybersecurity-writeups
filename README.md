# Networking Fundamentals Notes

# What is a LAN?

LAN (Local Area Network) = a network of devices connected within a small geographical area.

Examples:

* Home WiFi
* School lab
* Office network

LAN usually:

* uses private IP addresses
* communicates locally
* uses routers/switches

---

# Components of LAN

## Devices

Examples:

* Phones
* Laptops
* PCs
* Printers

Every device has:

* IP Address → logical identity
* MAC Address → physical identity

---

## Router

Main job:

* connects different networks together
* usually connects LAN to internet

Functions:

* routing
* NAT
* default gateway
* packet forwarding

Works on:

* Layer 3 (Network Layer)

Mental Model:

* traffic manager between networks

---

## Switch

Main job:

* connects devices inside same LAN

Functions:

* uses MAC addresses
* sends frames only to correct device
* maintains MAC table

Works on:

* Layer 2 (Data Link Layer)

Mental Model:

* local delivery manager

---

## Access Point

* wireless version of switch
* allows WiFi communication

---

# Transmission Methods

## Wired

* Ethernet cables

## Wireless

* WiFi signals

---

# Network Topologies

Topology = arrangement of devices in network.

Defines:

* structure
* data flow
* reliability
* efficiency

---

## Star Topology

All devices connected to central router/switch.

### Pros

* fast
* easy management

### Cons

* central device failure kills network

---

## Bus Topology

All devices connected to one backbone cable.

### Pros

* cheap
* simple

### Cons

* backbone failure kills network

---

## Ring Topology

Devices connected in circular loop.

### Pros

* orderly data flow

### Cons

* one break affects entire network

---

## Mesh Topology

Every device connected to multiple devices.

### Pros

* highly reliable

### Cons

* expensive
* complex

---

# IP Address

IP Address = logical address of a device.

Used for:

* identifying device/network
* routing data

Example:
192.168.1.5

---

# MAC Address

MAC Address = physical hardware address of device.

Used for:

* local delivery inside LAN

Example:
00:1A:2B:3C:4D:5E

---

# Difference Between IP and MAC

## IP Address

* logical address
* used across networks
* changes based on network
* works on Layer 3

## MAC Address

* physical hardware address
* used inside LAN
* usually permanent
* works on Layer 2

Mental Model:

* IP = neighborhood/building address
* MAC = exact house/door

---

# Public vs Private IP

## Private IP

Used inside LAN.

Ranges:

* 10.x.x.x
* 172.16.x.x – 172.31.x.x
* 192.168.x.x

Not directly reachable from internet.

---

## Public IP

Visible on internet.
Assigned by ISP.

Used for communication across internet.

---

# NAT (Network Address Translation)

NAT allows many private devices to share one public IP.

Example:

* Phone
* Laptop
* TV

all share:

* one public IP

Router translates private ↔ public communication.

---

# Subnetting

Subnetting = dividing a large network into smaller networks.

Purpose:

* better organization
* better security
* less congestion
* easier management

---

# CIDR Notation

CIDR tells:

* how much of IP belongs to network
* how much belongs to hosts

Example:
192.168.1.0/24

/24 means:

* first 24 bits = network
* remaining 8 bits = hosts

---

# Subnet Mask

Subnet mask separates:

* network part
* host part

Example:
/24 = 255.255.255.0

---

# Common CIDR Examples

## /24

Subnet Mask:
255.255.255.0

Hosts:
256 total
254 usable

---

## /26

Subnet Mask:
255.255.255.192

Hosts:
64 total
62 usable

---

# Formula

## Total Hosts

2^(host bits)

## Usable Hosts

2^(host bits) - 2

Why minus 2?
Because:

* network address reserved
* broadcast address reserved

---

# Network Address

First address of subnet.

Represents:

* entire network

Cannot be assigned to device.

Example:
192.168.1.0

---

# Broadcast Address

Last address of subnet.

Used to send data to all devices in subnet.

Cannot be assigned to device.

Example:
192.168.1.255

---

# Host Range

Usable device addresses between:

* network address
* broadcast address

Example:
192.168.1.1 – 192.168.1.254

---

# ARP (Address Resolution Protocol)

ARP finds MAC address using IP address.

Question:
"Who has this IP?"

Flow:

1. Device broadcasts ARP request
2. Target device replies with MAC
3. Device stores result in ARP table

Works on:

* Layer 2 (Data Link)

Mental Model:

* IP known
* MAC needed for local delivery

---

# DHCP (Dynamic Host Configuration Protocol)

DHCP automatically assigns IP addresses.

Without DHCP:

* IPs must be assigned manually

DHCP assigns:

* IP address
* subnet mask
* default gateway
* DNS server

---

# DHCP Process (DORA)

## Discover

Client searches for DHCP server.

## Offer

Server offers IP.

## Request

Client requests offered IP.

## Acknowledge

Server confirms assignment.

---

# OSI Model

OSI = conceptual model showing how data moves through network.

Purpose:

* standardization
* easier troubleshooting
* structured communication

---

# OSI Layers

## Layer 7 — Application

User interaction layer.

Examples:

* HTTP
* DNS
* SMTP

Functions:

* web requests
* email
* DNS resolution

---

## Layer 6 — Presentation

Handles:

* encryption
* formatting
* compression

Example:

* HTTPS encryption

---

## Layer 5 — Session

Creates and manages sessions between devices.

Functions:

* establish session
* maintain session
* terminate session

---

## Layer 4 — Transport

Handles:

* reliable delivery
* segmentation
* error checking

Protocols:

* TCP
* UDP

---

## TCP

Reliable communication.

Features:

* ordered delivery
* retransmission
* error checking

Used for:

* websites
* downloads

---

## UDP

Fast communication.

Features:

* no guarantee
* no retransmission
* low latency

Used for:

* gaming
* streaming

---

# TCP Three-Way Handshake

Used to establish TCP connection.

## Step 1 — SYN

Client requests connection.

## Step 2 — SYN-ACK

Server acknowledges and agrees.

## Step 3 — ACK

Client confirms.

Connection established.

---

# Layer 3 — Network

Handles:

* IP addressing
* routing
* path selection

Uses:

* IP addresses

---

# Layer 2 — Data Link

Handles:

* local delivery
* MAC addressing
* frame delivery

Uses:

* MAC addresses

---

# Layer 1 — Physical

Handles:

* physical transmission of bits/signals

Mediums:

* Ethernet
* fiber optics
* WiFi signals

---

# Encapsulation

Process of adding information at each OSI layer.

Flow:
Data
→ Segment
→ Packet
→ Frame
→ Bits

---

# Decapsulation

Reverse process on receiver side.

Removes:

* MAC info
* IP info
* transport info

until original data is reconstructed.

---

# Segments, Packets, Frames

## Segment

Transport layer data unit.

## Packet

Network layer data unit.
Contains IP header.

## Frame

Data Link layer data unit.
Contains MAC header.

## Bits

Physical layer signals.

---

# Packet Headers

## TTL (Time To Live)

Prevents infinite looping.

Each router decreases TTL by 1.
When TTL = 0:

* packet dropped

---

## Checksum

Used for error detection.

If corrupted:

* packet discarded

---

## Protocol Field

Indicates:

* TCP
* UDP

---

# Frame Headers

## Source MAC

Sender device.

## Destination MAC

Next local device.

## FCS (Frame Check Sequence)

Checks frame errors.

---

# DNS (Domain Name System)

Converts domain names into IP addresses.

Example:
google.com → 142.x.x.x

Process:

1. User enters domain
2. DNS request sent
3. DNS server returns IP
4. Communication starts

Works at:

* Application Layer

---

# Default Gateway

Default gateway = router IP used to leave local network.

When destination outside LAN:

* device sends data to router first.

---

# How Communication Happens

## Same LAN

1. Device checks destination IP
2. Uses ARP to get MAC
3. Sends frame directly

---

## Outside LAN

1. Device gets destination IP
2. Sends data to default gateway/router
3. Router forwards across internet

---

# Why MAC Changes But IP Stays Same

## IP

Represents final destination.
Stays same end-to-end.

## MAC

Represents next local hop.
Changes at every router/hop.

---

# TCP/IP Model

Real-world networking model.

Layers:

* Application
* Transport
* Internet
* Network Access

---

# Port

Port = logical communication endpoint/service.

Example:

* HTTP → Port 80
* HTTPS → Port 443
* SSH → Port 22

Mental Model:

* IP = building
* Port = room/service

---

# Port Forwarding

Allows router to forward incoming traffic to specific internal device.

Example:
PublicIP:25565
→ 192.168.1.5:25565

Purpose:

* hosting servers
* gaming
* remote access

---

# Firewall

Security system controlling traffic.

Checks:

* IP
* port
* protocol

Types:

* Network Firewall
* Host Firewall
* Stateful Firewall

Purpose:

* allow/block traffic
* reduce attack surface

---

# VPN (Virtual Private Network)

Creates encrypted tunnel between user and VPN server.

Functions:

* encrypt traffic
* hide public IP

Flow:
User
→ VPN Tunnel
→ VPN Server
→ Internet

VPN protects traffic from local observers.

---

# Router vs Switch

## Router

* connects different networks
* uses IP
* Layer 3

## Switch

* connects devices in same LAN
* uses MAC
* Layer 2

---

# Layer 3 Switch

Advanced switch with routing abilities.

Uses:

* MAC + IP
* inter-VLAN routing

Works on:

* Layer 2 + Layer 3

---

# VLAN (Virtual LAN)

Logical separation of devices into multiple virtual networks.

Example:

* VLAN 10 → HR
* VLAN 20 → Finance

Benefits:

* security
* organization
* reduced broadcast traffic

Devices in different VLANs:

* cannot directly communicate
* require Layer 3 device/router

---

# Key Networking Flow Summary

User enters website
→ DNS resolves domain to IP
→ TCP handshake establishes connection
→ Data segmented
→ IP added (packet)
→ MAC added (frame)
→ Bits transmitted
→ Router forwards across internet
→ Destination receives and decapsulates data
