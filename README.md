 Smart Firewall with Deep Packet Inspection (DPI)
Overview

Smart Firewall with DPI is a C++-based network security system that analyzes network traffic at a deeper level by inspecting packet contents (payload), not just headers.

It processes PCAP files, identifies applications using techniques like SNI extraction, and applies intelligent filtering rules to block or allow traffic.

 Features
Deep Packet Inspection (DPI)
Application Detection (YouTube, Facebook, etc.)
 Block traffic based on:
Application
Domain name
IP address

 Traffic analysis and reporting
 Rule-based filtering (rules.txt)
 Multi-threaded processing (high performance)
 Flow tracking using Five-Tuple
 
 How It Works
 
Reads network packets from a .pcap file
Parses different layers:
Ethernet
IP
TCP/UDP
Extracts payload data
Identifies application using:
TLS SNI (for HTTPS)
HTTP Host header
Applies filtering rules
Outputs:
Filtered packets
Traffic report


Project Structure
Smart Firewall with DPI/
│
├── Packet_analyzer-main/
│   ├── src/            # Source files
│   ├── include/        # Header files
│   ├── test_dpi.pcap   # Sample input
│   ├── rules.txt       # Custom rules
│   └── README.md
 Requirements
C++17 or later
Linux / WSL (recommended)
g++ compiler
 Build & Run
Compile:
g++ -std=c++17 -O2 -I include -o dpi_simple \
src/main_working.cpp \
src/pcap_reader.cpp \
src/packet_parser.cpp \
src/sni_extractor.cpp \
src/types.cpp
Run:
./dpi_simple test_dpi.pcap output.pcap

 Rules Configuration

Edit rules.txt:

block youtube
block facebook
block instagram

Sample Output

Total Packets Processed
Forwarded vs Dropped
Application-wise traffic
Detected domains (SNI)

Key Concepts Used

Deep Packet Inspection (DPI)
Network Protocol Parsing
Five-Tuple Flow Tracking
TLS Handshake & SNI Extraction
Multi-threading (Producer-Consumer)
System Programming (C++)

 Limitations
 
Cannot inspect encrypted payload beyond TLS handshake
Works on offline PCAP files (not real-time yet)

 Future Improvements
 
Real-time packet capture
GUI Dashboard
AI-based traffic classification
Bandwidth throttling
Support for HTTP/3 (QUIC)

Author
Harish Gupta

This project was built for learning and understanding network security and system-level programming concepts.
