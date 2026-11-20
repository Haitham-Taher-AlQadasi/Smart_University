
# Smart University — IoT Campus Network (Cisco Packet Tracer)

A Cisco Packet Tracer simulation of a **smart university campus**. It combines a routed campus network with an **Internet of Things (IoT)** layer that automates and monitors the classroom, laboratory, library, corridor and parking area from a central IoT server.


---

## Project Overview

The project shows how a university can use IoT devices and a segmented IP network to:

- Automate lighting and fans based on motion and temperature.
- Raise safety alerts (smoke detection and siren in the laboratory).
- Monitor outdoor areas (parking cameras, wind, water drain, garage door).
- Manage and control all smart devices remotely through a central IoT server, a laptop, and a smartphone.

---

## Campus Zones & Smart Devices

| Zone | Smart devices |
|------|---------------|
| **Classroom** | Light, Motion Detector, Temperature Monitor, Fan |
| **Laboratory** | Smoke Detector, Siren, Motion Detector, Light |
| **Library** | Light, Motion Detector, Fan |
| **Corridor** | Light, Motion Detector, Webcam |
| **Parking area / Park** | Light, Motion Detector, Webcam, Wind Detector, Water Drain, Garage Door |
| **Extra IoT nodes** | Water Sensor and Temperature Sensor connected through an SBC (single-board computer) |

---

## Network Architecture

Two Cisco **2911** routers connect the campus segments, with a **2960** switch, a wireless home gateway acting as the **Campus Gateway**, and an IoT/services server.

| Network | Purpose | Key devices |
|---------|---------|-------------|
| `192.168.1.0/24` | Campus IoT wireless network | Campus Gateway (`192.168.1.2`), smart devices |
| `192.168.2.0/24` | Server network | Main server (`192.168.2.2`), Laptop (`192.168.2.3`) |
| `192.168.3.0/24` | Inter-router link | Router0 (`192.168.3.1`) ↔ Router1 (`192.168.3.2`) |
| `192.168.4.0/24` | Secondary IoT network | Router1 (`192.168.4.1`), SBC with water/temperature sensors |

**Routing:** static routes between the two routers (`192.168.4.0/24` via Router0, and `192.168.1.0/24`, `192.168.2.0/24` via Router1).

**DHCP:** configured on the routers with separate pools per network, all pointing to the local DNS server.

**Wireless:** the Campus Gateway provides Wi-Fi to the IoT devices; a cell tower, central office server, cable modem and cloud simulate external/mobile connectivity for the smartphone.

---

## Server Services (Server0 – `192.168.2.2`)

- **IoT Server** — device registration and remote monitoring/control of all smart devices
- **DNS** — local domain name resolution (`haith.com`)
- **HTTP**, **DHCP**, **Email** (SMTP/POP3), **FTP**, **NTP**, **Syslog**

---

## Equipment Summary

- 2 × Cisco 2911 routers
- 1 × Cisco 2960-24TT switch
- 1 × Campus Gateway (wireless home gateway)
- 1 × Server, 1 × Laptop, 1 × Smartphone
- 1 × SBC (single-board computer)
- Cable modem, cloud, cell tower, central office server
- ~25 IoT components (lights, fans, sensors, cameras, siren, garage door, etc.)
- 35 devices and 12 links in total

---

## How to Run

1. Install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) (version **9.0 or later** recommended).
2. Clone or download this repository.
3. Open `Smart_University_3.pkt` in Packet Tracer.
4. Wait for the links to turn green, then:
   - Open the **IoT Server** web page from the laptop or smartphone to view and control the devices.
   - Trigger the motion detectors, temperature and smoke sensors to see the automation in action.

---

## Learning Objectives

- Designing a multi-subnet network with static routing and DHCP.
- Deploying and registering IoT devices on an IoT server.
- Building condition-based automation (motion → light, temperature → fan, smoke → siren).
- Integrating wired, wireless and cellular connectivity in one topology.


