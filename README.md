Cisco Packet Tracer – Ping Troubleshooting

Overview

This lab demonstrates a systematic approach to troubleshooting failed ping tests in Cisco Packet Tracer. The troubleshooting process follows the OSI model by checking physical connectivity, local network configuration, IP addressing, ARP resolution, and packet flow using Simulation Mode.

Objective

- Identify common causes of ping failures.
- Troubleshoot connectivity using a bottom-up approach.
- Verify the local TCP/IP stack using loopback testing.
- Verify IPv4 configuration using "ipconfig /all".
- Check ARP entries using "arp -a".
- Analyze ARP and ICMP packets using Packet Tracer Simulation Mode.
- Identify the point where a packet is dropped.

Troubleshooting Workflow

Physical Link
      ↓
Interface / Adapter
      ↓
IP Configuration
      ↓
Loopback Test
      ↓
Own-IP Test
      ↓
Subnet Verification
      ↓
ARP Verification
      ↓
Simulation Mode
      ↓
Packet Drop Analysis

Common Problems

1. Mismatched Subnet or Subnet Mask

Hosts may be configured on different networks.

Example:

PC0: 192.168.10.25 /24
PC1: 192.168.20.26 /24

Without a router, these hosts cannot communicate directly.

Check the configuration using:

ipconfig /all

2. Missing or Incorrect Default Gateway

A default gateway is required when communication involves a different network.

Verify the gateway using:

ipconfig /all

3. Duplicate IP Address

Two devices using the same IPv4 address can cause connectivity problems and ARP conflicts.

Check the ARP table:

arp -a

4. STP Convergence

An amber switch link may indicate that the switch is processing Spanning Tree Protocol states.

Wait for convergence or use Packet Tracer's Fast Forward Time option.

5. Cable or Interface Problems

Red links can indicate a physical connection problem, incorrect cabling, or a disabled interface.

For router interfaces, use:

show ip interface brief

6. ARP Resolution

Before sending an IPv4 packet on a local network, the device may need to resolve the destination IP address to a MAC address.

Check the ARP table using:

arp -a

Verification Tests

Loopback Test

ping 127.0.0.1

This verifies the local TCP/IP stack.

Own-IP Test

ping 192.168.10.25

Replace the address with the IPv4 address configured on the PC.

This helps verify the local interface and IPv4 configuration.

IP Configuration

ipconfig /all

Verify:

- IPv4 address
- Subnet mask
- Default gateway
- Network adapter information

Simulation Mode

Packet Tracer Simulation Mode is used to observe packet movement and identify where communication fails.

Steps:

1. Change Realtime to Simulation.
2. Open Edit Filters.
3. Enable ARP and ICMP.
4. Run the ping test.
5. Select Capture/Forward.
6. Observe the packet as it moves through the topology.
7. Select a packet marked with a red X.
8. Examine the In Layers and Out Layers tabs.
9. Identify the reason for the packet drop.

Screenshots

The following screenshots document the troubleshooting process:

01-physical-link-status.png
02-pc0-ip-configuration.png
03-ipconfig-all.png
04-loopback-test.png
05-own-ip-ping.png
06-arp-table.png
07-simulation-arp-icmp.png
08-packet-drop-analysis.png

Commands Used

ipconfig /all
ping 127.0.0.1
ping <PC-IP>
arp -a

For router-based troubleshooting:

show ip interface brief

Result

The lab demonstrates a structured method for identifying ping failures by progressively checking physical connectivity, interface configuration, IPv4 parameters, ARP resolution, and packet flow. Packet Tracer Simulation Mode provides additional visibility into the exact stage at which a packet is dropped.

Tools

- Cisco Packet Tracer
- Command Prompt
- IPv4
- ARP
- ICMP
- OSI Model
