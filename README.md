Task 1 – Local Network Port Scanning

Objective:
The goal of this task was to scan my local network using Nmap to find devices that are connected and check which ports are open. This helps understand what services are running and if anything might be risky from a security point of view.

Tools Used:

- Nmap 7.97 – for scanning devices and ports
- Operating System: Windows 11

What I Did:

1. Found my IP address using ipconfig (Windows)
2. Based on that, I scanned my full local network range: 192.168.1.0/24
3. Used the following Nmap command:
   nmap -sS 192.168.1.0/24 -oN scan_results.txt
4. Waited for the scan to finish and then checked the results in the output file.

Key Findings:
Active Devices Found:

| IP Address   | MAC Vendor / Device        | Open Ports                   | Notes                         |
| ------------ | -------------------------- | ---------------------------- | ----------------------------- |
| 192.168.1.1  | Taicang T&W (Router)       | 80, 443                      | Router login page open        |
| 192.168.1.3  | Imilab Tech (IoT?)         | None                         | All ports closed              |
| 192.168.1.4  | Unknown                    | None                         | Possibly a smart device       |
| 192.168.1.5  | Unknown (PC?)              | 135, 139, 445, 1521, 3306    | Windows + Oracle & MySQL open |
| 192.168.1.7  | Earda (Smart device?)      | 8008, 8009, 8443, 9000, 9080 | Web interfaces open           |
| 192.168.1.11 | Gaoshengda (Smart device?) | Same as above                | Likely a similar smart device |
| 192.168.1.14 | Unknown                    | None                         | All ports closed              |
| 192.168.1.23 | Possibly iPhone            | 49152, 62078                 | iTunes/iPhone sync port open  |

What This Tells Me:

- Devices like 192.168.1.5 have a lot of important ports open, including databases (MySQL, Oracle) and SMB services. This can be risky if not properly secured.
- The router (192.168.1.1) has its web interface open on ports 80 and 443. That’s normal, but should be restricted to local access only.
- Some smart devices are running services like 8008, 9000, and 8443, which could be entry points if not updated or protected.

What I Learned:

- How to use Nmap to scan a network and discover devices
- What open ports can reveal about what a device is doing
- Why it's important to monitor services and close unnecessary ports
- This kind of basic scanning is useful both for defense and for understanding how attackers might look at a network
