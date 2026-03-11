# Runbook: Network Latency Investigation

## Step 1 Verify Network Connectivity

Test connectivity to an external host.

ping -c 5 8.8.8.8

Check baseline latency.

---

## Step 2 Identify Network Interface

Inspect available network interfaces.

ip a

Identify the active interface (e.g., enp0s3).

---

## Step 3 Inspect Traffic Control Configuration

Check if traffic control rules are applied.

tc qdisc show

Look for delay rules such as:

netem delay 200ms

---

## Step 4 Identify Root Cause

Network latency may be introduced by a traffic control rule applied to the network interface.

Example rule:

sudo tc qdisc add dev enp0s3 root netem delay 200ms

---

## Step 5 Resolve the Issue

Remove the traffic control rule.

sudo tc qdisc del dev enp0s3 root

---

## Step 6 Verify Recovery

Test connectivity again.

ping -c 5 8.8.8.8

Expected result:

Normal latency (~10–20 ms).
