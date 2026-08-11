# C Event-Driven Chat System

A high-performance **Multi-User Chat System** written in **C**, built on a **Single-Threaded Event-Driven Architecture** using `poll()`.

---

## Project Concept

Instead of creating a dedicated `Thread` for every connected client (Thread-per-client model)—which incurs significant memory overhead and thread synchronization complexities—this system operates using a **Single-Threaded Model**.

The server monitors all network sockets concurrently using **I/O Multiplexing**. It remains in an idle state (0% CPU usage) until a network event occurs (a new connection or an incoming message), processes the event instantly, and resumes listening.

---

## Key Features

* **Resource Efficient:** Single-threaded design for both server and clients, ensuring minimal memory footprint and zero CPU wasting.
* **Chat History:** Automatically records the last 50 messages and delivers them to newly joined clients upon entrance.
* **Active User List:** Real-time generation and broadcasting of connected users.
* **Connection Lifecycle Handling:** Automatically broadcasts notifications when users join or disconnect.

---

## Technologies & Libraries

* `<poll.h>` - Handles I/O Multiplexing and synchronous event monitoring.
* `<sys/socket.h>` / `<arpa/inet.h>` - Manages TCP/IP network sockets and data transmission.
* `<unistd.h>` - Handles system file descriptors and socket closing.

---

## How to Run

### 1. Compile and Run the Server:
```bash
gcc server_poll.c -o server
./server