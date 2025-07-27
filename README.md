# 🚀 Portal - A Real-Time P2P Video Chat Application

Portal is a lightweight, real-time video calling application built from the ground up. It allows users to connect directly with each other in a peer-to-peer (P2P) fashion, ensuring low latency and private communication.

<img width="1915" height="957" alt="Screenshot 2025-07-27 140406" src="https://github.com/user-attachments/assets/a76d77e3-32e4-4a69-b4ba-db1d9e60ea79" />
<img width="1919" height="920" alt="Screenshot 2025-07-27 140447" src="https://github.com/user-attachments/assets/7c699028-b65d-471c-a028-d787e7cad0e1" />



**Live Demo (Temporary):** (https://52cbde54fff9.ngrok-free.app)

---

### ## Key Features

- **✅ Real-Time Video & Audio Streaming:** Crystal clear, low-latency communication.
- **🔗 Peer-to-Peer Connection:** Video data flows directly between users, not through the server.
- **👤 Dynamic User List:** See who's online and available to call.
- **📞 Simple UI:** An intuitive, single-click interface to initiate and end calls.

---

### ## The Technology & Its Advantages

This project's architecture was chosen specifically for performance, scalability, and privacy.

#### **1. WebRTC (Web Real-Time Communication)**
WebRTC is the core technology that enables direct, in-browser communication.

* **How it's used:** WebRTC's `RTCPeerConnection` API is used to establish a direct link between two browsers. It handles the complex process of streaming audio and video, navigating network firewalls (NAT traversal) using **STUN servers** and **ICE candidates**, and securing the data.

* **Advantage over Peers:**
    * **Ultra-Low Latency:** Traditional video apps route video through a central server (`User A -> Server -> User B`), adding significant delay. WebRTC creates a direct P2P connection, so data travels the shortest possible path, which is critical for natural conversation.
    * **Cost-Effective & Scalable:** Because the heavy video/audio data is not processed by our server, the server costs are incredibly low. Our server only needs to handle lightweight signaling messages, making the architecture highly scalable.
    * **Privacy & Security:** All WebRTC streams are encrypted end-to-end (via SRTP). Since the media doesn't pass through a third-party server, it's inherently more private.

#### **2. Node.js & Socket.IO (The Signaling Server)**
While WebRTC handles the direct call, it needs a way for users to find each other first. This is where our signaling server comes in.

* **How it's used:** A lightweight **Node.js** and **Express** server uses **Socket.IO** to manage a real-time signaling channel. It allows users to announce their presence, send "offers" to call another user, and exchange the network information (ICE candidates) needed to establish the WebRTC connection.

    * **Socket.IO** is used over plain WebSockets because it provides helpful abstractions like "rooms" and, crucially, has fallbacks (like HTTP long-polling) to ensure a connection can be made even on restrictive networks where WebSockets might be blocked.

---

### ## Getting Started (Local Setup)

1.  **Clone the repository:**
    ```bash
    git clone [your-repo-link]
    ```
2.  **Install dependencies:**
    ```bash
    npm install
    ```
3.  **Start the server:**
    ```bash
    npm start
    ```
4.  Open your browser and navigate to `http://localhost:9000`.
