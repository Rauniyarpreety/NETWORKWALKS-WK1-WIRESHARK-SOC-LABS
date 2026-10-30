# NetworkWalks Week 1 — Wireshark SOC Project Module (Extra)

**Program:** NetworkWalks Cybersecurity Internship  
**Module:** Week 1 — SOC Project Module, Wireshark (Extra)  
**Status:** Completed interactive lab activities

## Project overview

In this extra Week 1 project, I practiced the role of a Security Operations Center (SOC) analyst by examining simulated network traffic in Wireshark. The module includes **six browser-based SOC labs**, each containing **10 scenario-based objective questions** (60 questions in total). I used packet filters, protocol details, statistics, and TCP stream analysis to investigate suspicious activity and understand network communications.

The activities were completed in the NetworkWalks training labs using the traffic and scenarios provided by the instructor. This is a record of an authorized learning exercise, not an investigation of a real organization.

## Lab objectives and activities

| Lab | Scenario / focus | Wireshark analysis practiced |
|---|---|---|
| 3 — Identify the Attacker's IP | Investigate unusual connections to a web server | TCP SYN and SYN-ACK flags, RST-ACK responses, destination ports, source IPs, and signs of port scanning |
| 4 — Follow TCP Stream, Part 1 | Reconstruct a plaintext office chat | TCP Conversations, stream IDs, Follow TCP Stream, client/server directions |
| 5 — Follow TCP Stream, Part 2 | Find a hidden note in an intranet page | HTTP GET requests, HTML responses, TCP streams, and hidden HTML comments |
| 6 — HTTP Plain Text Credentials | Examine sign-in requests to an old staff portal | HTTP GET vs POST, form-encoded data, repeated login submissions, and exposure from unencrypted HTTP |
| 7 — Catch the Brute Force Attacker | Investigate repeated failed FTP sign-ins | FTP USER/PASS commands, `530` failures, server/client IPs, and login outcomes |
| 8 — Catch the Call Scammer | Investigate a VoIP call | SIP INVITE and call setup, RTP packets, codec details, and call reconstruction |

## Tools and features used

- Wireshark packet analysis interface in the NetworkWalks browser labs
- Display filters and packet-level protocol details
- **Statistics → Protocol Hierarchy** and **Statistics → Conversations**
- **Follow → TCP Stream**
- SIP signalling and RTP audio analysis features in the call lab

## Example analysis filters

These are examples of the analysis approaches used in the labs; the actual traffic must be inspected before interpreting results.

```wireshark
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

```wireshark
tcp.flags.syn == 1 && tcp.flags.ack == 1
```

```wireshark
http.request.method == "POST"
```

```wireshark
ftp.response.code == 530
```

```wireshark
sip
```

```wireshark
rtp
```

## Key lessons

- Packet flags and traffic patterns help distinguish a port scan from ordinary connections.
- Following a TCP stream can reveal application-layer information sent without encryption.
- HTTP form submissions and FTP authentication traffic illustrate why encrypted protocols matter.
- SIP sets up VoIP calls while RTP carries audio; protecting media with SRTP helps prevent interception.
- A SOC analyst should confirm findings from the packet evidence rather than guessing from a protocol name alone.

## Ethical scope

All analysis described here is based on the authorized NetworkWalks simulated lab environment. I did not scan or capture traffic from networks outside the training exercises.

## References

- [Wireshark documentation](https://www.wireshark.org/docs/)
- [NetworkWalks Labs, Quizes & Resources](https://networkwalks.com/wireshark/)
