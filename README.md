# Security Incident Report

<h2>Description</h2>
This security incident report details an incident involving the compromise of the Hypertext Transfer Protocol (HTTP) during an investigation related to the website "yummyrecipesforme.com." The incident was initially flagged by a junior cybersecurity agent who noticed an unusual surge in traffic at a specific port. Subsequent analysis, combining techniques such as tcpdump and website access, uncovered a series of events indicating malicious activity. The report outlines the incident timeline, the network protocols involved, and provides recommendations for remediating one specific aspect of the identified threat. 
<br />


<h2>Languages and Utilities Used</h2>

- <b>HTTP</b> 
- <b>tcpdump</b>
- <b>website access</b> 
<h2>Environments Used </h2>

- <b>Windows</b> 
- <b>Azure sentinel</b>
  
<h2>Walk-through:</h2>

<p align="left">
  
| Section 1: Identify the network protocol involved in the incident  | 
| ------------- | 
| The incident impacted the Hypertext Transfer Protocol (HTTP). To investigate the issue, a combination of running tcpdump and accessing the website yummyrecipesforme.com was employed. This approach helped in identifying the problem and capturing crucial protocol and traffic data, as evidenced in the DNS & HTTP traffic log file. Notably, the analysis revealed that the malicious file was being transferred to users' computers through the HTTP protocol at the application layer.  |

| Section 2: Document the incident  | 
| ------------- | 
| The first four lines are requesting a DNS request. From (your.machine.52444) using port 52444 to (dns.google.domain) for the destination URL (yummyrecipesforme.com). Then the DNS server responds to the source computer with the IP address of the destination URL (203.0.113.22). 
The next two sections show the source computer sending a connection request (Flags [S]) from the source computer (your.machine.36086) using port 36086 directly to the destination (yummyrecipesforme.com.http). The reply shows the destination acknowledging the request of (Flags [S.]). The communication between the source and the intended destination continues for about 2 minutes.
Then, a  change happens in the logs at 14:20:32.204388. The traffic is routed from the source computer to the DNS server again using port .52444 (your.machine.52444 > dns.google.domain) to make another DNS resolution request to a new IP address (192.0.2.172) and URL **(greatrecipesforme.com.http).**
Next, The traffic changes the spoofed website (outgoing traffic: IP **your.machine.56378 > greatrecipesforme.com.http and incoming traffic: greatrecipesforme.com.http > IP your.machine.56378** ). Note that the port number (.56378) on the source computer has changed again when redirected to a new website.|

| Section 3: Recommend one remediation for brute force attacks | 
| ------------- | 
| We recommend to monitoring login attempts as that should help with brute-force attacks. The malicious user will be caught depending on how many log in attempts they have and be denied further access. By limit the amount of attempts we will deter further attacks. |
<br />
<br />

Summary:  <br/>
On May 20th, 2023, I received a high-traffic alert, leading to the discovery of a security incident impacting the HTTP protocol. The investigation involved DNS requests, connection requests, and a subsequent redirection to a suspicious website ("greatrecipesforme.com"). The incident revealed a sophisticated attack involving DNS manipulation and website redirection. This report serves to document the incident's timeline, provide insights into the network protocols used, and offers a remediation recommendation focusing on monitoring login attempts to mitigate the risk of brute force attacks. The collaboration of network analysis tools and the vigilance of the cybersecurity team played a crucial role in identifying and responding to the threat.
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
