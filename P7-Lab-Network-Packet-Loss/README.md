# P7 Network Packet Loss Incident

## Scenario

A server experiences intermittent connectivity due to packet loss.

## Investigation

Initial connectivity test:

ping -c 5 8.8.8.8

Result: 0% packet loss

## Simulated Failure

Network packet loss was introduced using traffic control.

sudo tc qdisc add dev enp0s3 root netem loss 30%

## Verification

ping -c 20 8.8.8.8

Result:

25% packet loss observed.

## Resolution

Remove traffic control rule:

sudo tc qdisc del dev enp0s3 root

Connectivity restored.

## Lessons Learned

Packet loss can be diagnosed using ping and network queue inspection with tc.
