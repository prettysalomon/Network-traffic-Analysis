<h1>Network Traffic Analysis using tcpdump log files!</h1>

<h2>Scenario</h2>

You are a cybersecurity analyst working at a company that specializes in providing IT services for clients. Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load. 

You are tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, you attempt to visit the website and you also receive the error “destination port unreachable.” To troubleshoot the issue, you load your network analyzer tool, tcpdump, and attempt to load the webpage again. To load the webpage, your browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this is part of the DNS protocol. Your browser then uses this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage  The analyzer shows that when you send UDP packets to the DNS server, you receive ICMP packets containing the error message: “udp port 53 unreachable.”

In the tcpdump log, you find the following information:


 ![image](https://github.com/user-attachments/assets/1c61e849-c014-40a1-a8c2-cba554324bbc)

 


<h2>Project Description</h2>

-This project focuses on analyzing and troubleshooting a network connectivity issue affecting a client’s website, www.yummyrecipesforme.com , which has been reported as inaccessible by several customers.

-This is done using data from a network protocol analyzer tool called tcpdump.

<h2>Summary of Problem found in Tcpdump log</h2>

The analysis of the captured tcpdump log reveals that the root cause of the issue preventing users from accessing the website www.yummyrecipesforme.com is a failure in the DNS resolution process. 

As part of the DNS protocol, the UDP protocol was used to contact the DNS server to retrieve the IP address for the domain name of www.yummyrecipesforme.com. 

The ICMP protocol was used to respond with an error message, indicating issues contacting the DNS server. 

The UDP message going from the browser to the DNS server is shown in the first two lines of every log event. 

The ICMP error response from the DNS server to the browser is displayed in the third and fourth lines of every log event with the error message, “udp port 53 unreachable.” 

Since port 53 is associated with DNS protocol traffic, we know this is an issue with the DNS server. 

Issues with performing the DNS protocol are further evident because the plus sign after the query identification number 35084 indicates flags with the UDP message and the “A?” symbol indicates flags with performing DNS protocol operations. 

Due to the ICMP error response message about port 53, it is highly likely that the DNS server is not responding. This assumption is further supported by the flags associated with the outgoing UDP message and domain name retrieval.

<h2>Analysis of the data</h2>

The incident occurred at 1:24 p.m and Customers notified the organization that they received the message “destination port unreachable” when they attempted to visit the website www.yummyrecipesforme.com. The cybersecurity team providing IT services to their client organization are currently investigating the issue so customers can access the website again. While investigating using tcpdump , the resulting log files ,DNS port 53 was found unreachable. The next step is to identify whether the DNS server is down or traffic to port 53 is blocked by the firewall. 

Based on the findings, the most likely cause of the issue is DNS server unavailability or misconfiguration, preventing users from resolving the website's domain name. This could be due to:

*Successful Denial of Service attack 

*Routing misconfigurations leading to packet loss.

By addressing these areas, the goal is to restore normal website access and prevent future disruptions.

<h2>Solutions to implement</h2>

To address the issue, the following actions should be taken:

1-Verify DNS Server Status: Check if the DNS server is operational and accessible.

2-Firewall and Network Rules Review: Inspect firewall rules and access control lists to ensure DNS traffic is not blocked.

3-Alternate DNS Testing: Configure an alternate DNS provider (e.g., Google DNS 8.8.8.8) to verify if the issue persists.

4-Traceroute Analysis: Perform a traceroute to diagnose network connectivity issues.

5-Consult Hosting Provider: Engage with the hosting provider to determine if there are ongoing outages or maintenance activities affecting the DNS server.






