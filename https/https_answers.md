# HTTPS Analysis – CN Assignment 01

## Q7. What is the name of website?
The website is identified from the SNI (Server Name Indication) extension in the ClientHello.
**Website:** `v10.events.data.microsoft.com`

---


## Q8. Find the packet that contains the ClientHello message.
The ClientHello is found in **Packet No. 8** with SNI = `v10.events.data.microsoft.com`.

---

## Q9. List all the TLS extensions included in the ClientHello.
The ClientHello included the following TLS extensions:

- server_name v10.events.data.microsoft.com
- status_request 
- supported_groups 
- ec_point_formats
- signature_algorithms 
- session_ticket
- application_layer_protocol_negotiation 
- extended_master_secret 
- renegotiation_info

 ---

 ## Q10. Identify the ServerHello message. What cipher suite is chosen by the server
 The ServerHello is visible after the ClientHello.  
- **Cipher Suite chosen:** `TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 (0xc030)`  
- This means the connection uses TLS 1.2 with AES-256-GCM and SHA-384.

 ---

 
## Q11. Locate the Certificate message. Extract the server’s certificate information.
# TLS Handshake Certificate Analysis

Handshake Type: Certificate (11)
Certificates Length: 3617 bytes

Certificate #0 (Server Certificate)
-----------------------------------
Certificate Length: 2155 bytes
Issuer:
    CN: Microsoft Azure RSA TLS Issuing CA 08
    O: Microsoft Corporation
    C: US
Validity:
    Not Before: (UTC Time not available)
    Not After : (UTC Time not available)
Subject:
    CN: edge.microsoft.com
    O: Microsoft Corporation
    L: Redmond
    ST: WA
    C: US

Certificate #1 (Intermediate CA)
--------------------------------
Certificate Length: 1456 bytes
Issuer:
    CN: DigiCert Global Root G2
    OU: www.digicert.com
    O: DigiCert Inc
    C: US
Validity:
    Not Before: (UTC Time not available)
    Not After : (UTC Time not available)
Subject:
    CN: Microsoft Azure RSA TLS Issuing CA 08
    O: Microsoft Corporation
    C: US


---

## Q12. After the TLS handshake, identify the first encrypted application data packet. Why can’t you directly see the HTTP headers in this packet?
Content Type = 9 corresponds to Application Data in the TLS record layer.
The first Application Data packet indeed appears immediately after the handshake.
It contains the HTTP request/response, but it is encrypted, so Wireshark cannot show the headers unless you have the session keys.



