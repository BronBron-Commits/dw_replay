# dw_replay

Minimal DeltaWorlds authentication handshake replay client.

This project is not a full client and not an SDK reimplementation.
Its only goal is to reproduce the **exact network handshake**
used by the official DeltaWorlds client so the protocol can be
observed, logged, and iterated on safely.

---

## What This Does

- Connects to the DeltaWorlds auth server (port 6671)
- Sends raw protocol packets captured from a real client
- Receives and dumps server responses byte-for-byte
- Verifies that the handshake sequence is correct by observing RX traffic

This confirms:
- Socket setup is correct
- Packet framing is correct
- Compression/encryption boundaries are correct
- Server accepts the client as protocol-valid

---

## What This Is NOT

- Not a viewer
- Not a bot
- Not a login bypass
- Not a decryption exploit
- Not production-ready

No credentials are used.
No worlds are joined.
No gameplay occurs.

---

## Why This Exists

DeltaWorlds networking is a **state machine**, not magic.

The fastest way to understand it is:
1. Capture a real handshake
2. Replay it verbatim
3. Observe server behavior
4. Replace pieces incrementally with generated data

This repository is step **#2**.

---

## Build (Windows)

Requires:
- Visual Studio Developer Command Prompt
- Winsock (ws2_32.lib)

From the repo root:

