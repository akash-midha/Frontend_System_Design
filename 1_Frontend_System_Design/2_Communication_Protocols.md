# COMMUNICATION PROTOCOL

A communication protocol is a set of rules that define how data is exchanged between devices (like browser ↔ server).

In frontend context:
When browser (frontend) talks to a server, they need to agree on:
    - How to send data (text, JSON, binary)
    - When to send it
    - How to respond if something goes wrong

This is governed by protocols.


## 💡 Common Communication Protocols:

| Protocol      | Purpose                            |
| ------------- | ---------------------------------- |
| **HTTP**      | Most common for API requests       |
| **WebSocket** | Real-time two-way data transfer    |
| **SSE**       | Server pushes updates to client    |
| **FTP**       | File transfer                      |
| **TCP/IP**    | Backbone of internet communication |
| **HTTPS**     | Secure version of HTTP             |


## HTTP Polling

    - Client repeatedly asks server for updates (e.g., every 5 seconds).
    - Simple, but inefficient (lots of unnecessary requests).
    - 🧠 Think: "Anything new? Anything new? Anything new?"

## Long Polling

    - Client sends request, server holds the response until new data is available.
    - After getting data, client immediately sends next request.
    - More efficient than normal polling, but still HTTP-based.
    - 🧠 Think: "Tell me when something happens — I’ll wait."

## Server Sent Events (SSE)

    - Server pushes updates to client over a single HTTP connection.
    - One-way (server → client), good for notifications, live feeds.
    - Built-in support in browsers.
    - 🧠 Think: "Server keeps sending me updates when something changes."

## WebSockets

    - Full-duplex: real-time two-way communication (client ↔ server).
    - Persistent connection, super efficient.
    - Ideal for chat apps, gaming, collaboration tools.
    - 🧠 Think:"We’re always connected, can send messages both ways instantly."

| Protocol     | Direction       | Persistent?     | Real-time? | Use Case                  |
| ------------ | --------------- | --------------- | ---------- | ------------------------- |
| Polling      | Client → Server | ❌               | ❌          | Simple data fetch         |
| Long Polling | Client → Server | ❌ (but delayed) | ✅          | Chat-lite apps, fallback  |
| SSE          | Server → Client | ✅ (1-way)       | ✅          | Notifications, stock feed |
| WebSockets   | Bi-directional  | ✅               | ✅          | Chats, games, live collab |


## Socket.io

    - Socket.IO is a library built on top of WebSockets to make development easier, more reliable, and more feature-rich.
    - Easier than raw WebSocket, automatic connection.
    - It fails back to polling if needed.
    - Built in error handling
    - suitable for complex applications.


## GraphQL over HTTP / WebSockets

    - Ask for exactly what you need
    - Single endpoint (no multiple REST calls)
    - GraphQL is like ordering food from a menu 🧾 — you ask for exactly what you want, and the server delivers it — no more, no less.

## Difference in REST and GraphQL

REST - Representational State Transfer

| Aspect            | **REST **                              | **GraphQL**                            
| ----------------- | ------------------------------------- | -------------------------------------- |
| **Endpoints**     | Multiple endpoints for each resource  | Single endpoint for all data           |
| **Data Fetching** | Fixed data; may over/under-fetch      | Client specifies exactly what it needs |
| **Real-time**     | No built-in support (needs WebSocket) | Built-in support via **subscriptions** |








