# LUCKY13 Exploit

This repository contains a proof-of-concept (POC) exploit for the LUCKY13 vulnerability (CVE-2013-0169), which is a timing attack against certain implementations of the CBC (Cipher Block Chaining) mode of operation in cryptographic systems. The exploit aims to decrypt a target token by leveraging the timing differences in responses based on padding validation.

## Prerequisites

Before running the exploit, ensure you have the following:

- Python 3.x installed on your machine.
- The `requests` library. 

## How It Works

The exploit works by:

    Creating a Payload: It generates a payload that includes a prefix of known bytes and a guess for the byte being tested.
    Timing the Response: It sends the payload as a cookie to the target server and measures the time taken for the server to respond. A valid padding will typically result in a shorter response time.
    Decrypting the Token: By iterating through all possible byte values (0-255) and recording the response times, the script identifies the byte that results in the shortest response time, indicating a valid padding.
    Building the Known Bytes: The script builds the decrypted token byte by byte, starting from the last byte and working backwards
