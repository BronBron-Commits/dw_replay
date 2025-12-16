dw_replay

Minimal DeltaWorlds authentication handshake replay client.

This project is not a full client and not an SDK reimplementation.
Its only purpose is to reproduce the exact network handshake used by the official DeltaWorlds client so the protocol can be observed, logged, and iterated on safely.

What this does

Connects to the DeltaWorlds authentication server on port 6671

Sends raw protocol packets captured from a real client

Receives and dumps server responses byte-for-byte

Confirms correct packet framing and sequencing by receiving valid RX data

This proves that:

The socket setup is correct

Packet headers and lengths are correct

Compression boundaries are correct

The server accepts the client as protocol-valid

What this is not

Not a viewer

Not a bot

Not a login bypass

Not a decryption exploit

Not a production client

No credentials are used.
No worlds are joined.
No gameplay occurs.

Why this exists

DeltaWorlds networking is a state machine.
The protocol only advances when the client behaves exactly as expected.

The fastest way to understand it is:

Capture a real handshake

Replay it exactly

Observe server responses

Replace pieces gradually with generated data

This repository represents step two of that process.

Build instructions (Windows)

Requirements:

Visual Studio Developer Command Prompt

Winsock library (ws2_32.lib)

From the repository root:

cl src\main.c /Fe:build\dw_replay.exe ws2_32.lib

Run:

build\dw_replay.exe

Expected output:

Server responses of 107 bytes, 315 bytes, and larger packets

Hex dumps that match captured traffic from a real client

Current status

TCP handshake complete

CLIENT_HELLO sent

SERVER_INFO received

Key exchange packets observed

Compressed payloads verified

Not yet implemented:

Session key derivation

Encrypted payload decoding

Login phase transition

Legal and ethical note

This project is for protocol research and interoperability.
No private keys are extracted.
No encryption is broken.
No authentication is bypassed.

If you operate or develop a DeltaWorlds-compatible server or client, this work helps document the protocol behavior.

Author

BronBron-Commits
https://github.com/BronBron-Commits

Reverse engineering for understanding, not exploitation.
