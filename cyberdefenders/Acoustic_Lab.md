# Description
<img width="646" height="490" alt="image" src="https://github.com/user-attachments/assets/1aedae49-c7f6-42ff-93a6-f103cf9593f8" />

# Solve


## Question 1: What is the transport protocol being used?
in this lab, we need to explore the `RTP` protocol, so let`s check its definition.
> A protocol is designed to handle real-time traffic (like audio and video) of the Internet, is known as Real Time Transport Protocol (RTP). RTP must be used with `UDP`.

Answer: `UDP`

## Question 2: The attacker used a bunch of scanning tools that belong to the same suite. Provide the name of the suite.
In `log.txt`, we can see that almost all requests have the `User-Agent` field set to `friendly-scanner`. Looking this up online reveals that this User-Agent belongs to the `SIPVicious` suite.
> What is a user agent?
> 
> A user agent is a small piece of text that your web browser or script sends during an HTTP request to identify the client's software and operating system to the web server.

Answer: `SIPVicious`

## Question 3: What is the User-Agent of the victim system?
the first two packets in the `pcap`file that we were given are belong to the `SIP` protocol. The machine `172.25.105.43` sent a request to check the status of the victim machine that is `172.25.105.40` and the victim sent back a packet to verify the status, in this packet we can find the `user-agent` of the victim machine.

<img width="533" height="323" alt="image" src="https://github.com/user-attachments/assets/ecac8ca2-57f2-42b5-9eae-e97bfa909480" />

Answer: `Asterisk PBX 1.6.0.10-FONCORE-r40`
