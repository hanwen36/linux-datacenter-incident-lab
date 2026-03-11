# P8 Network Latency Incident

## Incident Description

This lab simulates a network latency issue on a Linux server.

Network latency can cause slow application response times even when connectivity is still available.

## Environment

Ubuntu Server (VirtualBox)

## Symptoms

- Slow network responses
- Increased ping latency
- Application performance degradation

## Tools Used

ping  
ip  
tc (traffic control)

## Summary

Network latency was simulated using Linux traffic control (`tc netem`) by adding a 200ms delay to the network interface.

The issue was identified through increased ping response times and inspection of the traffic control queue discipline.

Removing the traffic control rule restored normal network performance.

## Skills Demonstrated

Linux network troubleshooting  
Latency analysis  
Traffic control simulation  
Connectivity verification
