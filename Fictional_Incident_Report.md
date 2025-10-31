# Activity Incident Report: Analyze network attacks

| Section 1: Identify the type of attack that may have caused this  network interruption |
| :---- |
| One explanation for the website’s connection timeout error message is a DoS attack. The logs show that the web server stops responding after it is overloaded with SYN packet requests. This event could be a type of DoS attack called SYN flooding.  |

| Section 2: Explain how the attack is causing the website malfunction |
| :---- |
| When website visitors attempt to connect to the web server, a standard three-way handshake occurs using the TCP protocol. This handshake consists of: **SYN** — The client sends a SYN packet to initiate a connection. **SYN-ACK** — The server responds with a SYN-ACK packet, acknowledging the request and reserving resources. **ACK** — The client replies with an ACK packet, completing the handshake and establishing the connection. In a SYN flood attack, a malicious actor sends a large volume of SYN packets without completing the handshake. This causes the server to allocate resources for each half-open connection, eventually exhausting its capacity to handle legitimate requests. As a result, genuine users experience connection timeouts and degraded service availability. **Evidence Details** The source IP address `203.0.113.0` appears repeatedly in the server logs during the attack window. This address initiates numerous TCP connection attempts via SYN packets, but no corresponding ACK or HTTP traffic follows — indicating the connections were never completed. The high volume and rapid frequency of these incomplete SYN requests, all occurring within seconds, are consistent with the characteristics of a SYN flood attack. This behavior suggests an intentional attempt to overwhelm the server’s TCP stack and deny service to legitimate users.  |

