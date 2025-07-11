# L.I.M.E
Lightweight In-Memory Engine 

# L.I.M.E. – Lightweight In-Memory Engine

**L.I.M.E. (Lightweight In-Memory Engine)** is a custom-built, minimal Redis-compatible key-value store developed from the ground up. This project aims to replicate the internal architecture and protocol-level behavior of Redis with a strong focus on correctness, performance, and modularity.

---

## 🧠 Project Overview

L.I.M.E. implements the foundational building blocks of a high-performance in-memory data store, including:

- A custom TCP server supporting multiple client connections
- Full parsing and serialization of the **RESP (REdis Serialization Protocol)**
- Efficient O(1) in-memory key-value operations
- Extensible command execution architecture

This repository serves as a hands-on exploration of systems programming, socket-level networking, protocol design, and the internal mechanics of distributed in-memory databases.

---

## ⚙️ Core Features

| Feature                    | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| 🔗 **TCP Server**         | Manages incoming socket connections and maintains persistent client sessions |
| 🧾 **RESP Protocol**       | Custom parser/encoder for Redis’ native text-based protocol (RESP v2)        |
| 🧠 **In-Memory Store**     | Hash map–backed key-value engine ensuring constant-time access               |
| 🧪 **Command Execution**   | Modular command dispatcher with support for `GET`, `SET`, and `DEL`         |
| 🧰 **Scalable Design**     | Built for easy extension with new commands and features                      |

---

## 🛠️ Technical Stack

| Layer        | Technology Used        |
|--------------|------------------------|
| Language     | [e.g., Rust / Go / Python / Node.js] |
| Network      | Raw TCP sockets        |
| Protocol     | RESP (REdis Serialization Protocol) |
| Storage      | Volatile in-memory hash map |

---

## 🧱 Architecture
            +------------------------------+
            |        redis-cli / netcat    |
            |      (External Client)       |
            +--------------+---------------+
                           |
                  RESP Protocol (TCP)
                           |
            +--------------v---------------+
            |       L.I.M.E. Server        |
            |  (TCP Socket Listener)       |
            +--------------+---------------+
                           |
                Parses RESP Commands
                           |
            +--------------v---------------+
            |     Protocol Parser Layer    |
            |  (RESP Decoder & Encoder)    |
            +--------------+---------------+
                           |
                 Generates Command Objects
                           |
            +--------------v---------------+
            |      Command Dispatcher      |
            |  (Handles SET, GET, DEL, ...)|
            +--------------+---------------+
                           |
                 Executes logic on data store
                           |
            +--------------v---------------+
            | In-Memory Key-Value Datastore|
            |   (e.g., HashMap or Dict)    |
            +--------------+---------------+
                           |
                Returns RESP-encoded result
                           |
            +--------------v---------------+
            |       Response Encoder       |
            +--------------+---------------+
                           |
                    TCP Stream Output
                           |
            +--------------v---------------+
            |       Client Receives        |
            +------------------------------+

