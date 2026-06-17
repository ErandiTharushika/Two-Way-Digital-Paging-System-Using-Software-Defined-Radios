# Two-Way-Digital-Paging-System-Using-Software-Defined-Radios
A two-way digital paging system for short text messages with addressing and ACKs, focusing on reliable end-to-end delivery in noisy channels.

# 📡 EchoWave - SDR Wireless Messaging System

EchoWave is a **WhatsApp-like wireless messaging application** developed using **GNU Radio 3.10**, **Python**, and **bladeRF Software Defined Radios (SDRs)**. The project implements a complete end-to-end communication protocol that enables reliable real-time messaging between multiple users over a shared wireless channel.

---

## Team Members
- 230175U   Eranga W.A.O.
- 230566U Samarasekara S.M.R.R.
- 230195F   Gamage S.K.
- 230636K  Tharushika G.K.E.

## 🚀 Features

- 📡 QPSK modulation and demodulation for efficient wireless communication
- 👥 Supports up to **256 unique node addresses**
- 💬 Real-time messaging with a desktop GUI
- 📦 Packet framing with custom headers
- 🔢 Sequence numbering for packet ordering
- ✅ CRC-32 error detection and corrupted packet rejection
- 🔄 Reliable transmission using **Stop-and-Wait ARQ**
- 📨 ACK-based communication with timeout and retransmission
- ⏳ Binary exponential random backoff for collision recovery
- 📄 Automatic fragmentation and reassembly for long messages
- 🕒 Message timestamps and delivery status indicators
  - Sending
  - Sent
  - Failed

---

## 🏗 System Architecture

The project follows a layered communication architecture.

### Application Layer
- EchoWave GUI
- Real-time chat interface
- Message history and delivery status

### Transport Layer
- Packetization
- Sequence numbering
- Acknowledgment (ACK) handling

### Network Layer
- Node addressing
- Address filtering

### Data Link Layer
- CRC-32 error detection
- Pure ALOHA multiple access
- Stop-and-Wait ARQ
- Retransmission with exponential backoff

### Physical Layer
- Preamble insertion
- QPSK modulation/demodulation
- Timing and symbol synchronization

---

## 🛠 Technologies Used

- GNU Radio 3.10
- Python
- PyQt
- bladeRF SDR
- PMT (Polymorphic Types)
- QPSK Modulation

---

## 📂 Repository Structure

```
EchoWave-SDR-Messaging-System/
│
├── flowgraphs/
│   ├── Version 3 node.grc
│   └── Version 3 node.py
│
├── custom_blocks/
│   └── Python embedded blocks
│
├── images/
│   ├── flowgraph.png
│   ├── gui.png
│
└── README.md
```

---

## ⚙️ Communication Protocol

The system allows multiple SDR nodes to communicate over the same wireless channel.

Each transmitted packet includes:
- Source Address
- Destination Address
- Sequence Number
- Payload Length
- Payload Data
- CRC-32

After transmitting a packet, the sender waits for an acknowledgment (ACK). If an ACK is not received before the timeout expires, the sender assumes a collision or packet loss and retransmits the packet after a binary exponential random backoff interval.
