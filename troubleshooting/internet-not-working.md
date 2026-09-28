# Case 01: Internet Not Working
## Reported issue
The user cannot open websites.
## Questions to ask
- Is the issue on one device or multiple devices?
- Is the connection Wi-Fi or Ethernet?
- Do all websites fail?
## Troubleshooting steps
1. Check the physical or Wi-Fi connection.
2. Run `ipconfig /all` and identify the IP address, gateway, and DNS server.
3. Ping the default gateway.
4. Ping a public IP address.
5. Use `nslookup` to check name resolution.
## Findings
### Test 1 - Normal Connection
The network was tested while the device was connected.
- The device received a valid IP configuration from DHCP.
- The default gateway responded successfully.
- A public IP address responded successfully.
- DNS successfully resolved `google.com`.
### Test 2 - Simulated Network Failure
The network connection was intentionally disconnected to simulate an internet connectivity issue.
- The default gateway became unreachable.
- Ping to a public IP address failed.
- DNS name resolution failed.
- The ping command returned `Destination host unreachable`.
### Test 3 - Connection Restored
The network connection was restored.
- The device regained network connectivity.
- IP configuration was verified using `ipconfig /all`.
- The default gateway became reachable again.
- Internet and DNS connectivity were restored.
## Resolution
The simulated issue was resolved by restoring the network connection and verifying connectivity from the local network to the internet and DNS.
## What I learned
- Troubleshooting should follow a logical order: local connection → default gateway → internet → DNS.
- If the default gateway is unreachable, the local network connection should be investigated first.
- A successful packet count does not always mean connectivity is working. The actual ping response must be checked for errors such as `Destination host unreachable`.
- The same network device can provide multiple services such as DHCP, default gateway, and DNS.