# P7 Network Packet Loss Incident

## Incident Description

This lab simulates a network packet loss issue on a Linux server.

Packet loss can cause unstable connections, slow application responses, and intermittent failures.

## Environment

Ubuntu Server (VirtualBox)

## Symptoms

- Intermittent connectivity
- Packet loss during ping tests
- Increased latency

## Tools Used

ping  
tc (traffic control)  
ip  

## Summary

Packet loss was simulated using Linux traffic control (tc netem).

The issue was identified using ping tests and network queue inspection, and resolved by removing the traffic control rule.
