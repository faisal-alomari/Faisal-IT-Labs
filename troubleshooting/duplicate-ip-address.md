# Case 04: Duplicate IP Address
## Problem
A computer may experience unstable or lost network connectivity when two devices on the same network use the same IPv4 address.
## Troubleshooting
### 1. Check the Current IP Configuration
`ipconfig`
Verify the IPv4 address, subnet mask, and default gateway.
### 2. Test an IP Address
`ping 192.168.100.50`
The address did not respond and returned:
`Destination host unreachable`
### 3. Check the ARP Table
`arp -a`
Check whether the IPv4 address is associated with a MAC address.
### 4. Check the Neighbor Table
`Get-NetNeighbor -AddressFamily IPv4`
The address `192.168.100.50` appeared as `Unreachable` with no valid MAC address.
Another device at `192.168.100.25` appeared as `Reachable` with the MAC address `B6-B5-6A-67-0D-52`.
### 5. Verify the Reachable Device
`ping 192.168.100.25`
`Get-NetNeighbor -IPAddress 192.168.100.25`
The device responded successfully and its IPv4-to-MAC mapping was confirmed.
## Diagnosis
A duplicate IP occurs when two devices on the same network use the same IPv4 address.
This may cause unstable connectivity because the same IPv4 address can be associated with different MAC addresses.
A real duplicate IP was not created during this lab to avoid disrupting another device on the network.
## Resolution
Identify the devices using the duplicate address and correct the IP configuration.
Use DHCP when appropriate or assign a unique static IP address that does not conflict with another device.
## Commands Used
`ipconfig`
`ping 192.168.100.50`
`arp -a`
`Get-NetNeighbor -AddressFamily IPv4`
`ping 192.168.100.25`
`Get-NetNeighbor -IPAddress 192.168.100.25`
## What I Learned
- Duplicate IP addresses can cause unstable or lost network connectivity.
- ARP maps IPv4 addresses to MAC addresses on the local network.
- `arp -a` displays cached IPv4-to-MAC mappings.
- `Get-NetNeighbor` can show states such as `Reachable`, `Stale`, and `Unreachable`.
- A failed ping alone does not guarantee that an IP address is unused.