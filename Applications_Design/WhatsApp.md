# Chat Based Application - WhatsApp

## Functional Requirements

### Module Level Thinking
    - Auth
    - Chat
    - Calling
    - Notifications

### Feature Level Thinking
    1. Auth
        - QR based web login
        - OTP based login
        - SSO

    2. Chat
        - one-to-one communication
        - group chats
        - chat history
        - searching users or chat history
        - media support
            - images
            - audio

    3. Calling
        - audio support
        - video support

    4. Notifications
        - push notifications
        - Send, delivered & read recipts
        - show last seen
        - show online status
        - show typing status

## Non-Functional Requirements

    - mobile first or desktop first
    - responsiveness
    - optimization (network, asset)
    - security
    - realtime
    - offline support
    - PWA
    - caching
    - localization
    - internationalization
    - versioning
    - CI / CD
    - Testing

## Communication Protocols
    - Polling
    - Long Polling
    - Server Sent Events (SSE)
    - WebSockets


Chat apps like whatsapp use WebSocket because it allows real-time, two-way communication over a single connection. It lets the server instantly push messages to users without repeated requests, making it fast and efficient for live messaging.

## Communication flow

When User1 sends a message to User2 in a chat application, the message is first transmitted from User1's device to the server using a real-time communication protocol like WebSocket. The server receives this message, processes it, and may store it in a database for future retrieval. Next, the server checks if User2 is currently online by identifying their active connection. If User2 is connected, the server immediately forwards the message to their device, where it appears in their chat window in real time. If User2 is offline, the server holds the message and ensures it is delivered once they reconnect. This seamless flow ensures quick, reliable, and synchronized communication between users.

## Tracking online status, typing indicator and last seen

Online status, last seen, and typing indicators are tracked using real-time communication (like WebSocket) and a fast data store (like Redis). Online status is tracked using heartbeat signals sent by the client to the server at regular intervals over a WebSocket connection. As long as the server receives these heartbeats, the user is considered online. If heartbeats stop (e.g., user closes the app or loses connection), the server marks the user as offline and stores the last seen time. Typing indicators are sent as separate real-time events, and all status updates are broadcasted to relevant users instantly.

## QR based login 

In QR-based login, the browser first establishes a WebSocket connection with the server and receives a unique session ID (sent as a "hello" message). Meanwhile, the user logs into the mobile app via Facebook and obtains an access token. When the user scans the QR code (which contains the session ID), the mobile app sends both the session ID and Facebook access token to the server. The server verifies it and then sends the access token to the browser over the WebSocket, completing the login process.


More detail

WhatsApp Web QR login works through secure device pairing using WebSockets and cryptographic key exchange. When you open WhatsApp Web, the browser connects to the server via WebSocket and receives a QR code containing a unique session ID and public key. When the QR is scanned by the mobile app (where the user is already logged in), the app verifies the request, encrypts data using its private key, and sends it back to the server. The server then relays this to the browser, completing a secure handshake. Once verified, the browser is linked as a trusted device, and chats sync in real time with end-to-end encryption.

## Encryption and Decryption

When two users start a chat, WhatsApp generates a pair of encryption keys for each device: a public key (shared) and a private key (kept secret on the device). When you send a message, your app encrypts it using the recipient’s public key, so only their device—with the matching private key—can decrypt it. These keys are exchanged securely using a protocol called Signal Protocol, which also provides forward secrecy (each message uses a temporary session key). The WhatsApp servers act only as a delivery system for the encrypted messages—they cannot read or access the content. Even WhatsApp itself can’t decrypt messages, making the conversation completely private between the two devices.


### Symmetric Encryption
    - Uses one key for both encryption and decryption.
    - Both sender and receiver must share the same secret key.
    - 🔄 Fast and efficient, but key sharing is risky.
    - 🧠 Example: You lock and unlock a box with the same key.

### Asymmetric Encryption
    - Uses two keys: a public key (shared with anyone) and a private key (kept secret).
    - Sender encrypts using the recipient’s public key; only the recipient can decrypt with their private key.
    - More secure for communication, but slower than symmetric.
    - Example: Anyone can lock a box using your public lock, but only you can unlock it with your private key.

Whatsapp uses asymmetric encryption to exchange a secure session key, then uses symmetric encryption for actual message exchange (for speed).

