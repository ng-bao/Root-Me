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

## Question 4: Which tool was only used against the following extensions: 100,101,102,103, and 111?
With these extensions, we can see each of them has `REGISTER` requests with `Authorization` information except extension 100. It looks like a password `brute-force` attack, indicating that the attacker used `svcrack.py` in this situation. As for why extension 100 lacks `Authorization` packets, we suspect this extension does not require a password, so the tool didn`t send any Authorization packets.

Answer: `svcrack.py`

## Question 5: Which extension on the honeypot does NOT require authentication?
As mentioned in Q4, extension 100 is the only one didn't has `Authorization` packets when it was `brute-forced` by `svcrack`.

Answer: `100`

## Question 7: There is a trace for a real SIP client. What is the corresponding user-agent? (two words, once space in between)

## Questiom 8: Multiple real-world phone numbers were dialed. What was the most recent 11-digit number dialed from extension 101?
We can find the most recent number dialed by determining the most recent `INVITE` packet was sent by extension 101 at `2010-05-05 10:00:46.147670`
<img width="583" height="433" alt="image" src="https://github.com/user-attachments/assets/9b9080c6-c3c9-452e-9b63-f711bd0f875d" />

Answer: `00112524021`

## Question 10: Which codec does the RTP stream use? (3 words, 2 spaces in between)
We can identify the audio codec by checking `Telephony -> RTP -> RTP Streams`
<img width="1280" height="56" alt="image" src="https://github.com/user-attachments/assets/58c4efde-df0b-4eb7-bde2-b73167798912" />

In the `Payload` field, we can see the codec which the RTP steam use, then fill the answer following answer format.

Answer: `ITU-T G.711 PCMU`
