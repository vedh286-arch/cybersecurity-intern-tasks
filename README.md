# Task 1: Scan Your Local Network for Open Ports

Cybersecurity Internship - Elevate Labs

## What I did
- Scanned the network 192.168.136.0/24 with Nmap using a TCP SYN scan:
  `nmap -sS -oN scan_results.txt 192.168.136.0/24`
- Noted the hosts and open ports, then researched the services and their risks.
- Captured a small SYN scan in Wireshark (on 127.0.0.1) to see the packets behind the scan.

## Results
- 2 hosts were up out of 256 addresses.
- 192.168.136.254: all 1000 ports filtered, no open ports.
- 192.168.136.1: 7 open ports - 135, 139, 445, 902, 912, 4343 and 4449.
- Ports 135, 139 and 445 are Windows services (RPC, NetBIOS and SMB). SMB (445) is the riskiest.
- Ports 902 and 912 are usually VMware services. Ports 4343 and 4449 could not be identified.

## Wireshark
- Ports 135 and 445 replied with SYN/ACK, so they are open.
- Port 8080 replied with RST/ACK, so it is closed.
- Nmap sent RST after each SYN/ACK, which is why it is called a half-open scan.

## Files
- `task 1 - paragraphs.docx` - full report
- `scan_results.txt` - Nmap scan output
- `nmap_scan_results.png` - screenshot of the scan results
- `nmap_syn_scan.pcapng` - Wireshark capture
- `wireshark_syn_probes.png`, `wireshark_open_ports.png`, `wireshark_rst_replies.png`, `wireshark_full_exchange.png` - Wireshark screenshots

## Tools
Nmap, Wireshark
