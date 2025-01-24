<h1>Network Traffic Analysis !</h1>

<h2>Scenario</h2>

You are a cybersecurity analyst working at a company that specializes in providing IT services for clients. Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load. 

You are tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, you attempt to visit the website and you also receive the error “destination port unreachable.” To troubleshoot the issue, you load your network analyzer tool, tcpdump, and attempt to load the webpage again. To load the webpage, your browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this is part of the DNS protocol. Your browser then uses this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage  The analyzer shows that when you send UDP packets to the DNS server, you receive ICMP packets containing the error message: “udp port 53 unreachable.”

In the tcpdump log, you find the following information:


 ![image](https://github.com/user-attachments/assets/1c61e849-c014-40a1-a8c2-cba554324bbc)

 


<h2>Project Description</h2>

-This project focuses on analyzing and troubleshooting a network connectivity issue affecting a client’s website, www.yummyrecipesforme.com , which has been reported as inaccessible by several customers.

-This is done using data from a network protocol analyzer tool called tcpdump.

<h2>Summary of Problem found in Tcpdump log</h2>

-The analysis of the captured tcpdump log reveals that the root cause of the issue preventing users from accessing the website www.yummyrecipesforme.com is a failure in the DNS resolution process. Specifically, the captured logs show that when the client browser attempts to resolve the domain name to an IP address by sending a UDP query to the DNS server on port 53, the server responds with an ICMP error message: "udp port 53 unreachable."

-This indicates that the DNS server is either down, misconfigured, or blocked, preventing successful resolution of the domain name. Without resolving the domain name to its corresponding IP address, the browser cannot initiate an HTTPS request to the web server, resulting in the "destination port unreachable" error message experienced by users.

<h2>Analysis of the data</h2>

1-Upon receiving reports from users, the cybersecurity team conducted an investigation and confirmed the issue. The following symptoms were observed:

  *Website visitors reported inability to access the site.
  
 *Attempts to load the website resulted in the “destination port unreachable” error message.Initial analysis suggested a potential issue with network connectivity.

2-The website remains inaccessible as DNS resolution fails, preventing clients from reaching the server. The issue persists despite multiple user attempts to access the site.

3-A network traffic analysis was conducted using tcpdump, which revealed the following key observations:


 *The browser sends a UDP request to the DNS server on port 53, attempting to resolve the domain name.
 
*The DNS server responds with an ICMP error message: “udp port 53 unreachable.”This indicates that the DNS server is either down, unreachable, or there is a network misconfiguration blocking access to port 53.

*The HTTPS request to the web server never initiates because the DNS resolution fails.

4-Based on the findings, the most likely cause of the issue is DNS server unavailability or misconfiguration, preventing users from resolving the website's domain name. This could be due to:

*DNS service failure or downtime.

*Firewall or network security settings blocking DNS traffic.

*Routing misconfigurations leading to packet loss.

By addressing these areas, the goal is to restore normal website access and prevent future disruptions.

<h2>Solution to implement</h2>

To address the issue, the following actions should be taken:

1-Verify DNS Server Status: Check if the DNS server is operational and accessible.

2-Firewall and Network Rules Review: Inspect firewall rules and access control lists to ensure DNS traffic is not blocked.

3-Alternate DNS Testing: Configure an alternate DNS provider (e.g., Google DNS 8.8.8.8) to verify if the issue persists.

4-Traceroute Analysis: Perform a traceroute to diagnose network connectivity issues.

5-Consult Hosting Provider: Engage with the hosting provider to determine if there are ongoing outages or maintenance activities affecting the DNS server.






