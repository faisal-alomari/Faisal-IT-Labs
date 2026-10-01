# Case 02: DNS Resolution Problem
## Problem
The internet connection is working, but websites cannot be accessed using domain names.
## Troubleshooting
### 1. Check Network Configuration
`ipconfig /all`
Verified the IP address, default gateway, and DNS server.
### 2. Test Internet Connectivity
`ping 8.8.8.8`
Result: Successful. This confirmed that external network connectivity was working.
### 3. Test DNS Resolution
`nslookup google.com`
Used to verify whether the configured DNS server could resolve domain names.
### 4. Test a Specific DNS Server
`nslookup google.com 8.8.8.8`
Result: Successful.
### 5. Simulate DNS Failure
`nslookup google.com 192.0.2.1`
Result:
`DNS request timed out.`
Internet connectivity was available, but name resolution failed when using a non-working DNS server.
## DNS Cache
View cached DNS records:
`ipconfig /displaydns`
Clear the DNS cache:
`ipconfig /flushdns`
## Diagnosis
If `ping 8.8.8.8` works but domain name resolution fails, the configured DNS server or connectivity to it should be investigated.
## Resolution
- Verify the configured DNS server.
- Test another known working DNS server.
- Correct the DNS configuration if necessary.
- Clear outdated DNS cache entries.
- Test name resolution again.
## Commands Used
- `ipconfig /all`
- `ping 8.8.8.8`
- `ping google.com`
- `nslookup google.com`
- `nslookup google.com 8.8.8.8`
- `nslookup google.com 192.0.2.1`
- `ipconfig /displaydns`
- `ipconfig /flushdns`
## What I Learned
- DNS resolves domain names to IP addresses.
- A successful ping to an IP does not confirm that DNS is working.
- `nslookup` can test the configured DNS server or a specific DNS server.
- A records point to IPv4 addresses, AAAA records to IPv6 addresses, and CNAME records to other hostnames.
- Windows can use IPv4 and IPv6 DNS.
- `ipconfig /flushdns` clears the local DNS cache.