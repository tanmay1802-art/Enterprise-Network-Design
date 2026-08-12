# Enterprise-Network-Design

Enterprise Network Design & Simulation (MACSATech)
This project documents the design and simulation of a multi-branch enterprise network for a fictional company, MACSATech. Built using Cisco Packet Tracer, the network connects four branches across Malaysia (Kuala Lumpur, Penang, Johor, and Kelantan) using a Ring topology for inter-branch connectivity and Star topologies within each branch.

Note: This is Version 1 of the project (Basic Static Routing). An upgraded Version 2 with advanced routing protocols will be added later.

🛠️ Tech Stack & Concepts
Simulation Tool: Cisco Packet Tracer
Routing: Static IP Routing (Ring Topology across 4 Routers)
Switching: Cisco 2960 Switches, VLAN 1 configuration
IP Addressing: Custom Subnetting (/24 for LANs, /30 for WAN serial links)
Infrastructure: Servers (DNS, FTP, Email, Web), IoT Devices (IP Cameras, ACs, RFID, IP Phones)
🏢 Branch Overview
The network is segmented into four branches, each containing specific departments:

Kuala Lumpur (KL) Branch: Server Room, Reception, HR, IT Department.
Penang Branch: Server Room, Reception, HR, IT Department.
Johor Branch: Server Room, Administration, HR, Reception.
Kelantan Branch: Server Room, Administration, HR, Reception.
📂 Project Structure
Version_1_Basic/: Contains the Packet Tracer simulation file (.pkt) and the project documentation (.pdf) for the 1st-semester submission.
🚀 How to View
Download the MACSATech_Network_v1.pkt file from the Version_1_Basic folder.
Open the file using Cisco Packet Tracer (version 8.0 or later recommended).
Hover over devices to check IP configurations, or open router CLI to view routing tables.
