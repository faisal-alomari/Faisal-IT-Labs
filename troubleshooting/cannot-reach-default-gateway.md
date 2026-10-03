# Case 05: Cannot Reach Default Gateway
## Problem
A computer may have a valid IPv4 address but cannot reach the default gateway, causing loss of connectivity outside the local network.
## Troubleshooting
### 1. Check the Current IP Configuration
`ipconfig`
Verify the IPv4 address, subnet mask, and default gateway.
The computer received:
- IPv4 Address: `192.168.100.47`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.100.1`
### 2. Test the Default Gateway
`ping 192.168.100.1`
The default gateway responded successfully with `0%` packet loss.
### 3. Check the Neighbor Table
`Get-NetNeighbor -IPAddress 192.168.100.1`
The gateway appeared as `Reachable` with the MAC address:
`90-5E-44-83-20-73`
This confirmed that the computer could reach the gateway on the local network.
### 4. Test External Connectivity
`ping 8.8.8.8`
The public IP address responded successfully with `0%` packet loss.
This confirmed that connectivity beyond the default gateway was also working.
## Diagnosis
If a computer has a valid IPv4 address but cannot ping the default gateway, the problem is likely within the local network path.
Possible causes include:
- Incorrect default gateway
- Incorrect subnet configuration
- Network adapter problem
- Cable or Wi-Fi connectivity problem
- Switch port problem
- Incorrect VLAN configuration
- Gateway device unavailable
If the default gateway responds but a public IP address does not, the problem may exist beyond the local network, such as routing, NAT, firewall, WAN, or ISP connectivity.
A real gateway failure was not created during this lab to avoid interrupting the active network connection.
## Resolution
Verify the local network connection and confirm that the IPv4 address, subnet mask, and default gateway are configured correctly.
Check the network adapter, physical connection, switch or VLAN configuration, and gateway availability when necessary.
## Commands Used
`ipconfig`
`ping 192.168.100.1`
`Get-NetNeighbor -IPAddress 192.168.100.1`
`ping 8.8.8.8`
## What I Learned
- The default gateway provides access from the local network to other networks.
- A failed gateway ping can indicate a local network connectivity problem.
- A successful gateway ping helps confirm connectivity between the computer and the gateway.
- `Get-NetNeighbor` can verify the IPv4-to-MAC mapping of the gateway.
- If the gateway is reachable but a public IP is not, troubleshooting should continue beyond the local network.