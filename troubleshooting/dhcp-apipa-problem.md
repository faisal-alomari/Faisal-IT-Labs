# Case 03: DHCP / APIPA Problem
## Problem
A Windows computer is connected to the network but fails to obtain a valid IPv4 address from the DHCP server.
## Troubleshooting
### 1. Check Network Configuration
Run:
`ipconfig /all`
Check:
- DHCP status
- IPv4 address
- Subnet mask
- Default gateway
- DHCP server
- Lease information
A `169.254.x.x` address may indicate that Windows failed to obtain an IPv4 address from DHCP and assigned itself an APIPA address.
### 2. Release the DHCP Lease
Run:
`ipconfig /release`
The current DHCP-assigned IPv4 configuration is released.
### 3. Renew the DHCP Lease
Run:
`ipconfig /renew`
Windows requests IPv4 configuration from the DHCP server again.
### 4. Verify the Configuration
Run:
`ipconfig /all`
Verify that the computer received a valid IPv4 address, subnet mask, default gateway, and DHCP lease.
## DHCP Process
DHCP commonly uses the DORA process:
Discover → Offer → Request → Acknowledge
## Diagnosis
An APIPA address (`169.254.x.x`) indicates that the device could not obtain a valid IPv4 configuration from DHCP.
Possible causes include:
- DHCP server unavailable
- Network connectivity problem
- Incorrect VLAN configuration
- DHCP relay problem
## Resolution
Release and renew the DHCP lease and verify connectivity to the DHCP service.
## Commands Used
`ipconfig /all`
`ipconfig /release`
`ipconfig /renew`
## What I Learned
- How DHCP automatically provides IPv4 configuration.
- How to identify an APIPA address.
- How to release and renew a DHCP lease.
- The DHCP DORA process.
- An APIPA address does not always mean the DHCP server itself is down.