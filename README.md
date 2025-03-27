Final Summary: HTTPS Traffic Analysis with Wireshark
🚀 Objective
This project aimed to analyze an entire HTTPS session captured in Wireshark, starting from the DNS resolution to the full TCP & TLS handshake, followed by encrypted data transmission and proper connection termination.

Throughout this project, we meticulously tracked the flow of events to understand the precise order in which they occur. This method ensures that future Wireshark analyses will be structured, efficient, and meaningful.

📌 Step-by-Step Flow of Events
We followed the logical sequence of a web request using HTTPS, breaking down each critical phase:

1️⃣ DNS Resolution (Converting Domain to IP)
The client queried a DNS server to resolve the website name (weightlifting.com) into an IP address.

This process is necessary before establishing any network connection.

2️⃣ TCP Handshake (Establishing a Connection)
A three-way handshake was performed between the client (192.168.1.185) and the web server (199.59.243.228) on port 443 (HTTPS).

This process included:

SYN → SYN-ACK → ACK

A bidirectional connection was successfully established.

3️⃣ TLS Handshake (Establishing Secure Communication)
Client Hello: The client proposed supported TLS versions, cipher suites, and extensions.

Server Hello: The server selected TLS 1.3, a cipher suite (AES-GCM-SHA256), and a key exchange method (X25519).

Key Exchange: The client and server established a shared secret key using asymmetric encryption.

Finished Message: Both parties switched to symmetric encryption, securing all subsequent data.

4️⃣ Encrypted HTTPS Data Transmission
Once the TLS handshake was complete, actual HTTP data was exchanged, but it was fully encrypted within TLS packets.

These packets were identified as Application Data inside TLS 1.3 Record Layers.

5️⃣ Connection Termination (Graceful TCP Shutdown)
The server initiated the FIN-ACK to begin closing the connection.

The client acknowledged the request and responded with its own FIN-ACK.

The server then confirmed closure, marking the official end of communication.

🔑 Key Takeaways
✅ Flow Matters: Every network connection follows an orderly, structured process. Understanding this sequence allows accurate troubleshooting in Wireshark.
✅ Security Layers: TLS encryption secures HTTPS traffic, ensuring that data remains confidential and tamper-proof.
✅ Efficient Analysis: Recognizing Client Hello, Server Hello, Encrypted Data, and TCP FIN packets is crucial for evaluating secure web communications.
✅ Real-World Relevance: This project reflects real-world security analysis, applicable to network security monitoring, intrusion detection, and compliance audits.

🚀 Next Steps
This project provided a strong foundation in analyzing HTTPS traffic. Moving forward, we could explore:

Decrypting HTTPS traffic with session keys (if available).

Comparing TLS 1.3 vs. TLS 1.2 behaviors in Wireshark.

Identifying anomalies in encrypted web traffic (e.g., malicious activity, certificate mismatches).

