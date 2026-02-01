---
title: "TCP Working: 3-Way Handshake & Reliable Communication"
datePublished: Sun Feb 01 2026 10:54:46 GMT+0000 (Coordinated Universal Time)
cuid: cml3mj8lz000702l44vsw3qii
slug: tcp-working-3-way-handshake-and-reliable-communication
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1769935911189/bd2e2386-60d2-4f7e-9824-f67867845576.png
tags: stackoverflow, akamai, geeksforgeeks, chaicode

---

## **When Data Has No Rules: A Recipe for Chaos**

Imagine trying to send a puzzle to a friend, but the pieces arrive in random order—or worse, some pieces never arrive at all. You'd end up with an incomplete, jumbled mess. This is exactly what happens when data travels across the internet without rules or protocols.

Without protocols, packets of data can get lost in transit, arrive out of sequence, or become corrupted by electronic interference. Your email might arrive with missing paragraphs, your video call would freeze constantly, and downloaded files would be unusable. The internet as we know it simply wouldn't function.

## **Enter TCP: The Traffic Controller of the Internet**

Transmission Control Protocol (TCP) is the foundational protocol that brings order to this potential chaos. Operating at the Transport Layer, TCP acts like a meticulous traffic controller, ensuring that data packets reach their destination reliably, in the correct order, and without errors.

TCP is connection-oriented, meaning it establishes a dedicated communication channel before any data flows. Think of it like making a phone call: before you can talk, both parties must pick up and confirm they're ready to communicate.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769936116742/f69002b4-bf50-4ab2-9ef3-4e41a9774eb5.png align="center")

## **The TCP 3-Way Handshake: Your Connection's Secret Handshake**

Before any data can flow reliably between two computers, they need to introduce themselves and agree on the rules of communication. This is where the **TCP 3-Way Handshake** comes in—a quick, three-step conversation that establishes a reliable connection.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769936343241/21908965-db50-4b95-b436-4485908a402a.png align="center")

%[https://youtu.be/PWyeEdVCXzg?si=n3qH2AzPpXvhob83] 

### **Step 1: SYN (Client Says Hello)**

The **client** (your web browser, for example) wants to connect to a **server** (like [google.com](http://google.com)). It sends a packet with the `SYN` flag set to 1.

This packet contains a critical piece of information: the **Initial Sequence Number (ISN)**—let's say it's **1000**. This number is randomly chosen and marks the starting point for numbering all the data bytes the client will send.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769938153111/6206b8d1-7093-478f-8179-973f7979715e.png align="center")

### **Step 2: SYN-ACK (Server Responds)**

The server receives the client's `SYN` and responds with both `SYN` and `ACK` flags set—hence the name `SYN-ACK`.

The server does two things:

1. **Acknowledges** the client's sequence number by setting the **Acknowledgment Number** to **1001** (client's ISN + 1). This tells the client: "I received your hello, and I'm ready for byte 1001 next."
    
2. **Sends its own ISN**—let's say **5000**—in the **Sequence Number** field. This is the server's starting point for data.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769938664105/ceab1e14-1016-4280-aa0b-850846c8320f.png align="center")

### **Step 3: ACK (Client Confirms)**

Finally, the client sends a `ACK` packet back to the server. The **Acknowledgment Number** is set to **5001** (server's ISN + 1).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769938854532/74488b32-7579-45c6-bade-bcfc38e247cb.png align="center")

### **Visual: TCP 3-Way Handshake Flow**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769939002209/7bd9d501-84be-48a5-8127-c52d42a12863.png align="center")

%[https://youtu.be/GyOhz8PWxY4] 

## **How TCP Transfers Data Reliably**

Once the connection handshake completes, the real work begins: transferring your data. But TCP doesn't just throw packets into the void and hope they arrive. It employs five key mechanisms to ensure every byte reaches its destination intact and in order.

### **1\. Sequence Numbers: Keeping Everything in Order**

Imagine sending a 1,000-piece puzzle to a friend, but the pieces arrive in random boxes over several days. How would they know which piece goes where?

TCP solves this by numbering every byte of data. When you send a message, TCP breaks it into segments and assigns each segment a **sequence number** based on the position of its first byte in the overall stream.

For example, if segment 1 contains bytes 1-1000, its sequence number is 1. Segment 2 (bytes 1001-2000) has sequence number 1001. Even if segment 2 arrives before segment 1 due to network routing, the receiver can use these numbers to reassemble your data in the correct order.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769940892744/efaa8faf-5d9c-43ee-9318-20a5b1d14ee4.png align="center")

### **2\. Acknowledgments: Confirming Receipt**

Sequence numbers tell the receiver what arrived. **Acknowledgment numbers** (ACKs) tell the sender what was successfully received.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769941139491/2293c951-9a72-4cf4-aa3a-5bf8a6ac10ba.png align="center")

### **3\. Retransmission: Handling Packet Loss**

Networks are imperfect. Packets get lost due to congestion, hardware failures, or interference. TCP detects and recovers from loss using two methods:

**Timeout-Based Retransmission:** When TCP sends a segment, it starts a timer. If no ACK arrives before the timeout, it assumes the packet was lost and retransmits it.

**Fast Retransmit (Duplicate ACKs):** If the receiver gets segments 1, 2, 4, and 5 (skipping 3), it sends duplicate ACKs for segment 2 each time. After receiving three duplicate ACKs, the sender immediately retransmits segment 3 without waiting for the timeout—much faster recovery.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769941577511/c5626bac-7514-4c04-9c20-83e729d19218.png align="center")

### **4\. Sliding Window: Flow Control**

Imagine trying to fill a glass with a firehose—water everywhere! TCP's **sliding window** prevents this by letting the receiver control how much data the sender can transmit.

The receiver advertises a "window size" indicating available buffer space. The sender can only transmit that many unacknowledged bytes. As the receiver processes data and frees buffer space, the window "slides" forward, allowing more transmission.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769941797836/ada5682a-fd98-4a9a-a1b0-f80a3a439fdb.png align="center")

%[https://youtu.be/0NjTP016B-I] 

### **5\. Checksums: Error Detection**

Even if a packet arrives, its contents might be corrupted. TCP includes a **checksum**—a mathematical fingerprint of the data. The receiver recalculates this value; if it doesn't match, the segment is discarded and will be retransmitted.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769942496369/82f9ac6e-d171-425d-9a0b-ae0d03974dc7.png align="center")

### **Why TIME\_WAIT Exists**

The `TIME_WAIT` The state prevents confusion if packets arrive late from the old connection. It's like waiting a moment after hanging up to ensure no final words were missed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769942631862/aa226c3f-773b-4c66-bb5e-d2339ee06db8.png align="center")

### **The Complete TCP Journey**

From birth to retirement, a TCP connection follows this lifecycle:

1. **CLOSED** → Initial state
    
2. **3-Way Handshake** (SYN, SYN-ACK, ACK) → Connection established
    
3. **ESTABLISHED** → Data transfer occurs
    
4. **4-Way Handshake** (FIN, ACK, FIN, ACK) → Connection terminated
    
5. **CLOSED** → Back to the starting point.
    

## **Wrapping Up: TCP's Reliability Promise**

TCP transforms the chaotic internet into a reliable communication channel through:

* **3-way handshake** for synchronized connection setup
    
* **Sequence numbers** ensuring correct order
    
* **Acknowledgments** confirming delivery
    
* **Retransmissions** recover lost packets
    
* **Flow control** preventing overwhelm
    
* **4-way handshake** for graceful closure
    

[SOURCES...](https://www.goanywhere.com/blog/http-vs-tcp-whats-the-difference)