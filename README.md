# log-analysis-lab


<!--  -->

## Issue 1

**Log Entries:**

```plaintext
2023-02-17 09:34:09 127.0.0.1 127.0.0.1 TCP 3000 Allow 57289
```

**Description of log entries:** Localhost traffic on an unusual port (3000).

**Reason for concern:** Potential rogue process or misconfiguration.

**Potential impact:** Could indicate data exfiltration or unauthorized access.

**Possible explanations:** Misconfiguration, command and control attack, or legitimate service.


<!--  -->


## Issue 2

**Log Entries:**

```plaintext
2023-02-17 09:34:03 192.168.1.27 45.137.80.15 TCP 41284 Deny 48
```

**Description of log entries:** TCP connection attempted from internal host to external IP on a high port was desnied. 

**Reason for concern:** Outbound connection to unkown IP on a high port, non-standard port, which was block, could suggest an attempt to data exflitration or an attempt to the use of a backdoor 

**Potential impact:** Data leak

**Possible explanations:** Malware, or Misconfigured application


<!--  -->


## Issue 3 


**Log Entries:**

```plaintext
2023-02-17 09:38:24 192.168.1.72 111.221.29.254 TCP 443 Deny 0  
2023-02-17 09:38:31 192.168.1.72 111.221.29.254 TCP 443 Deny 0  
2023-02-17 09:38:39 192.168.1.72 111.221.29.254 TCP 443 Deny 0  
2023-02-17 09:38:46 192.168.1.72 111.221.29.254 TCP 443 Deny 0  
2023-02-17 09:38:53 192.168.1.72 111.221.29.254 TCP 443 Deny 0  
```

**Description of log entries:**  Multiple denied TCP connection attempts to the same external ip on port 443. Attempts denised by firewall. 

**Reason for concern:** The repeated attempts may indicate persistent or automated malicious behavior 

**Potential impact:** The internal host might be compromised and attempting to reach out to a C2 server. COuld also be a data exfiltration attempt. 

**Possible explanations:** Malware, automated script, misconfigured proxy 


<!--  -->


## Issue 4

**Log Entries:**

```plaintext
2023-02-17 09:34:14 192.168.1.49 216.109.119.63 TCP 25 Allow 7421
```

**Description of log entries:** Internal IP successfully initiated an outoboad connection to an external IP address on TCP pot 25. Port 25 is a port used for sending email via the SMTP protocol. The firewall allowed this connection, which is means data was transfered, when in it shouldn have been denied. 

**Reason for concern:** Port 25 is used for email relay  and is often blocked for outbound traffic to prevent spam. 

**Potential impact:** Spam, data breach, phishing, malware

**Possible explanations:** Misconfigured email client, malware sending spam (spambot), testing? (sometimes used for testing)


<!--  -->


## Issue 5

**Log Entries:**

```plaintext
2023-02-17 09:34:50 fdf8:f53b:82e4::53 fdf8:f53b:82e4:0:1652:14ff:fe0b:b71c TCP 22 Deny 0
```

**Description of log entries:** IPv6 traffic denied on port 22. Post 22 is for SSH connections. Connection was denied and blocked.

**Reason for concern:** SSH is often used for administrive access. If the system blocked the SSH attempt from one computer to another within the network, it might be a sign of sispecious activity.

**Potential impact:** Brute force SSH attack , secruity gap in IPv6 monitoring or authorized 
remote access attempt

**Possible explanations:** Misconfigured or unauthorized ssh client, IPv6 misconfiguration 


<!--  -->

## Issue 6

**Log Entries:**

```plaintext
2023-02-17 09:35:56 172.17.99.132 205.185.216.10 UDP 443 Deny 6340
```

**Description of log entries:** Outbound connection using UDP protocol on port 443 was denied. Even though the firewall denied the connection, it seems like 6340 bytes might have transmitted (partial data transfer).

**Reason for concern:** Seems like a unusual use of UDP on Port 443. 443 is is used for HTTPS not UDP. This port can also be used by malware or tunneling tools to hide traffic since 443 is usually seen as a safe port. 

**Potential impact:** Malware might be trying to connect with a C2 server, data exfiltration attempt

**Possible explanations:** Some malicious VPNs/tunnels use UDP to nypass netrok restricitions. 


<!--  -->

## Issue 7 

**Log Entries:**

```plaintext
2023-02-17 09:34:16 192.168.1.37 19.89.143.11 UDP 67 Allow 256
```

**Description of log entries:**  Log shows outbound UDP allowed on Port 67, which typically used for DHCP server responses, not for outbound client traffic.

**Reason for concern:** It's rare and potentially suspicious for sa device to send DHCP traffic to a public IP. Could indiciate a leak of DHCP requests. 

**Potential impact:** Data leakage, if internal network configurtion is exposed to enternal systems. Malware might be using DHCP protocols to probe. 

**Possible explanations:** Misconfigured firewall, spoofed pcket, unauthorized device attempting to communicate. 


<!--  -->

## Issue 8

**Log Entries:**

```plaintext
2023-02-17 09:36:07 192.168.1.61 217.23.2.15 TCP 21 Allow 3629
```

**Description of log entries:** Successful outbound connection over port 21, which is the default port for FTP and 3629 bytes of data was transfered.

**Reason for concern:** FTP is an insecure protocol, and is ofter disabled and replaced with SFTP. This means the FTP was most likely not disabled or replaced, allowing external connections to be made. 

**Potential impact:** Malware, Data Exflirtion > if FTP wad not disbaled, that means, that host could use FTP for data leakage. 

**Possible explanations:** Misconfiguration or older software, or maybe a user is testing and needs FTP access.

<!--  -->

## Issue 9

**Log Entries:**

```plaintext
2023-02-17 09:34:27 192.168.1.142 43.250.192.131 TCP 80 Allow 1203
```

**Description of log entries:** 

**Reason for concern:** 

**Potential impact:** 

**Possible explanations:** 

<!--  -->

## Issue 10

**Log Entries:**

```plaintext
2023-02-17 09:35:26 192.168.1.54 203.208.40.53 TCP 443 Allow 2749
```

**Description of log entries:** 

**Reason for concern:** 

**Potential impact:** 

**Possible explanations:** 



