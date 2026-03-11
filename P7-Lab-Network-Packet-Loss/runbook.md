# Runbook: Network Packet Loss

## Step 1 Verify Network Connectivity

Check if the system can reach external hosts.

ping -c 5 8.8.8.8

---

## Step 2 Inspect Network Interface

Verify that the network interface is active.

ip a

---

## Step 3 Check Traffic Control Rules

Inspect traffic control configuration.

tc qdisc show dev enp0s3

Look for packet loss rules such as:

netem loss 30%

---

## Step 4 Identify Root Cause

Packet loss may be introduced by a traffic control rule using tc netem.

Example:

sudo tc qdisc add dev enp0s3 root netem loss 30%

---

## Step 5 Resolve Issue

Remove the traffic control rule.

sudo tc qdisc del dev enp0s3 root

---

## Step 6 Verify Resolution

Run connectivity tests again.

ping -c 20 8.8.8.8

Expected result:

0% packet loss
