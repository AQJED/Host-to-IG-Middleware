# Host to IG Middleware Project

## Overview
This project is a **middleware application** that facilitates communication between a **Host Computer** and an **Image Generator (IG)** by converting **CIGI 3.1** packets into **CIGI 3.3** packets.

## System Architecture
The middleware performs the following tasks:

1. **Capture CIGI Packets from Host Computer**  
   - The **Host Computer** sends **CIGI 3.1** packets.  
   - These packets are captured and processed.  

2. **Store Data in Shared Memory**  
   - The **CIGI 3.1 packets** are written into a **shared memory buffer**.  
   - Each packet is marked with a flag to indicate whether it is **ready to be processed**.  

3. **Read Data from Shared Memory**  
   - The middleware continuously checks for available packets in **shared memory**.  
   - Once a packet is ready, it is retrieved for processing.  

4. **Convert CIGI 3.1 to CIGI 3.3**  
   - The **CIGI 3.1 packet** is parsed using the **CIGI CCL** library.  
   - The corresponding **CIGI 3.3 packet** is constructed with updated parameters.  

5. **Send CIGI 3.3 Packets to IG**  
   - The converted **CIGI 3.3 packets** are sent to the **AECHLON IG** using **Boost.Asio** for **TCP/UDP communication**.  

## Libraries Used
The middleware is developed in **C++** using the following libraries:

1. **CIGI CCL** – Handling **CIGI packet structures** and conversions.  
2. **Boost** – Shared memory management and network communication.  

## Hardware and Software Requirements
- **Hardware:**  
  - **Host Computer** – Sends CIGI 3.1 packets.  
  - **Cisco Switch** – Connects the **Host** and **IG** to the middleware.  
  - **AECHLON Image Generator (IG)** – Receives CIGI 3.3 packets.  

- **Software:**  
  - **C++ Application (Middleware)** – No additional software tools or frameworks are used.  

## Key Features
- **Protocol Upgrade**: Converts **CIGI 3.1** packets to **CIGI 3.3**.  
- **Efficient Shared Memory Handling**: Uses **Boost.Interprocess** to manage **CIGI packet buffering**.  
- **Real-time Network Communication**: Uses **Boost.Asio** for **TCP/UDP transmission**.  

## Data Flow Diagram  

Host Computer (CIGI 3.1 Packets)  
↓  
Shared Memory (Boost)  
↓  
Middleware (CIGI 3.1 to CIGI 3.3 Conversion)  
↓  
Boost.Asio (CIGI Packet Transmission)  
↓  
AECHLON IG (CIGI 3.3 Packets Rendered)  

## Future Enhancements
- Support for **additional CIGI packet types**.  
- Improved performance for **high-frequency updates**.  
- Integration of **logging and debugging tools**.  

## Conclusion
This middleware **bridges the gap between Host and IG** by efficiently processing and upgrading **CIGI 3.1** packets into **CIGI 3.3** format. The solution is designed for **real-time simulation environments**, ensuring **seamless integration** with the AECHLON IG.  
