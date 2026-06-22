# network-traffic-monitoring-lab
Network Traffic Monitoring Lab

A hands-on lab demonstrating network traffic capture and analysis using Wireshark and Nmap in a home network environment. The lab focuses on identifying common attacker reconnaissance and credential-exposure patterns and mapping them to the MITRE ATT&CK framework.

Objective

Capture and analyze live network traffic to identify suspicious or insecure behavior, including:


Port scanning activity
Unencrypted (plaintext) credential transmission
DNS query traffic


Tools Used


Wireshark – packet capture and analysis
Nmap – active port scanning
nslookup – DNS query generation
MITRE ATT&CK Framework – technique mapping


Lab Setup


Started a live packet capture in Wireshark on the active network interface.
Ran an Nmap SYN scan against the local router to generate scan traffic.
Submitted a test login form over plain HTTP (http://demo.testfire.net/login.jsp) to capture unencrypted credentials in transit.
Issued a manual DNS lookup for a non-existent domain to observe DNS query behavior.
Stopped the capture and saved it as a .pcapng file for analysis.


Findings Summary

#ActivityEvidenceMITRE ATT&CK Technique1Port scan against local router (ports 23, 53, 80, 443 probed)screenshots/01_nmap_scan_results.png, screenshots/02_wireshark_port_scan_syn_packets.pngT1046 – Network Service Scanning2Plaintext credentials sent via HTTP POSTscreenshots/03_wireshark_http_post_plaintext_credentials.pngT1040 – Network Sniffing / T1557 – Adversary-in-the-Middle3DNS query for an unresolvable/suspicious-looking domainscreenshots/04_terminal_nslookup_query.png, screenshots/05_wireshark_dns_query_capture.png

(Structure)
network-traffic-monitoring-lab/
├── README.md
├── report.md
└── screenshots/
    ├── 01_nmap_scan_results.png
    ├── 02_wireshark_port_scan_syn_packets.png
    ├── 03_wireshark_http_post_plaintext_credentials.png
    ├── 04_terminal_nslookup_query.png
    └── 05_wireshark_dns_query_capture.png

Disclaimer

All scanning and traffic generation in this lab were performed against systems owned by the author (home router) or against a publicly available, intentionally vulnerable test application (demo.testfire.net) designed for security training and education. No unauthorized systems were accessed.
