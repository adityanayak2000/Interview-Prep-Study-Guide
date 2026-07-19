# Computer Networks (router)
**Software / Product track** · Med–High weight at networking-adjacent roles (Cisco, Netskope, Sophos); appears in some IBM/product rounds.

## Why it matters
OSI/TCP-IP stack questions, HTTP vs TCP, DNS, and debugging “why is my API slow” in product rounds. Semiconductor filter is lighter here than OS/C — still know L3/L4 cold for CN-heavy companies.

## Concept map
_Paraphrased interview skeleton aligned with [notescs CN notes](https://github.com/notescs/notes/blob/main/Computer-Networks-for-Interviews/README.md) + Boss Sheet._

### Layers
| Model | Layers to own |
|---|---|
| **OSI** | L1 Physical · L2 Data link · L3 Network · L4 Transport · (+ session/presentation rarely grilled) · L7 Application |
| **TCP/IP** | Link · Internet · Transport · Application |

### Transport — TCP vs UDP
| | TCP | UDP |
|---|---|---|
| Connection | Handshake (3-way) + teardown | Connectionless |
| Delivery | Reliable, ordered byte stream | Best-effort datagrams |
| Control | Flow + congestion control | App handles |
| Use | HTTP(S), SSH, most APIs | DNS query, games, VoIP, telemetry |

**TCP must-knows:** seq/ack (seq # = byte-stream position of first byte; ack = next expected byte, cumulative), RTT/RTO estimate (`EstimatedRTT = 0.875·EstimatedRTT + 0.125·SampleRTT`, `RTO = EstimatedRTT + 4·DevRTT`, doubling after each timeout; retransmitted segments are excluded from RTT sampling — retransmission-ambiguity problem), flow control (`rwnd` shrinks toward 0 as the receiver's buffer fills; if it hits zero, the sender keeps probing with 1-byte segments so the receiver is forced to eventually reveal a reopened window — otherwise the connection would deadlock), congestion (slow start / AIMD high level), multiplexing via ports.  
**UDP must-knows:** checksum, no congestion by itself — good when latency > reliability or app has own recovery.

### Application favorites
- **HTTP** — request/response over TCP (usually); **stateless**; verbs; status codes (2xx/3xx/4xx/5xx); HTTP/1.1 keep-alive vs HTTP/2 multiplexing awareness.  
- **HTTPS** — TLS handshake wraps TCP; confidentiality + integrity.  
- **DNS** — hierarchical name → IP; recursive vs iterative; usually UDP/53 (TCP for large/zone).  
- **FTP / SMTP / IMAP/POP** — know “control vs data” (FTP) and mail transfer vs access at 1-liner depth.

### Network / link (interview depth)
- IP addressing/subnetting, forwarding vs routing (high level).  
- ARP (IP→MAC on LAN).  
- Ethernet framing / MTU; fragmentation (avoid in modern design).  
- NAT and private ranges — why servers need public or port-forwarding.

### Sockets mental model
`socket` → `bind`/`listen`/`accept` (server) or `connect` (client) → `send`/`recv` → `close`.  
AF_INET stream = TCP; datagram = UDP. See also YC TCP sockets article via [Contents](https://yc-kuo.medium.com/contents-e8eedc905fa).

### Debugging oral
“API slow” → DNS? TCP handshake RTT? TLS? Application? Loss/retransmission? Server queue? CDN?

## Practice direction
- Trace a packet: browser → DNS → TCP → TLS → HTTP → app.  
- Diff TCP vs UDP with one production example each.  
- Explain congestion vs flow control in one sentence each.

## Boss Sheet
[CN Boss Sheet](https://drive.google.com/file/d/1maLFnmWgjgJyCd6cQ4CHIlVbLIMRMaAm/view)

## Resource Panel
- [CN Quick Notes](https://drive.google.com/file/d/1OymHd6cW-KQ4L36DVCEeD2OUdknXQBwY/view)
- [Blue Team Networking](https://drive.google.com/file/d/12dJ0VPDdLkFtnkjHkMEBxcixqERr37IP/view)
- [CN GitHub Notes (notescs)](https://github.com/notescs/notes/blob/main/Computer-Networks-for-Interviews/README.md)
- [CN Video Course](https://www.youtube.com/playlist?list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi)
- [TCP/UDP Deep Dive](https://www.youtube.com/playlist?list=PLIFyRwBY_4bS-PQZoF0UySdG0sH9VA0bn)
- [YC TCP sockets article](https://yc-kuo.medium.com/hands-on-tcp-sockets-with-c-vim-on-ubuntu-0bee398abb94) · [full YC roadmap](YC_Cpp_OS_Concurrency_Roadmap.md)
- Interview Prep §CN: [🎯 Interview Prep](../../🎯%20Interview%20Prep%20Resources.md)  
- Related: [OS](OS.md) · [Systems Interview](Systems_Interview.md) · [00_INDEX](../00_INDEX.md)
