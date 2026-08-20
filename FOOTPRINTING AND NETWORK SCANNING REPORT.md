FOOTPRINTING AND NETWORK SCANNING REPORT Week 2 Practical Assessment — Networkwalks 

Pentester Name: Jevaughn Stewart 

Program / Batch: B082-Networkwalks 

Date: August 18, 2026 

Modules Completed: W2-PM1 (Multiple Kali Tools), W2-PM5 (Zenmap Scanning) 

# 1. Liability Disclaimer 

All activities documented in this report were performed only within an authorized training environment or on systems I own personally. This report is for educational and coursework purposes. Unauthorized use of the techniques described is prohibited and may be unlawful. Responsibility for any misuse remains with the individual applying the information. 

# 2. Introduction 

This Week 2 practical exercise documents two core activities: public footprinting of the networkwalks.com domain using Kali Linux tools, and local network discovery using Zenmap on a personal LAN. The aim was to demonstrate how public data and basic scanning reveal environmental details important to a security assessment. 

# 3. Tools and Environment 

Operating Environments: 

Kali Linux (reconnaissance tools and Zenmap scan) Tools Used: 

|**Tool**|**Purpose**|
|---|---|
|**WHOIS**|Domain registration and nameserver<br>information|
|**WhatWeb**|Website technology fingerprinting|
|**Nslookup**|DNS resolution|
|**curl -I**|HTTP header inspection|
|**wafw00f**|WAF detection|
|**Dnsrecon**|DNS record enumeration|
|**Zenmap (Nmap**|Local network discovery and topology|
|**GUI)**|export|



# 4. Methodology 

# 4.1 Footprinting & Reconnaissance 

The domain networkwalks.com was reviewed using multiple reconnaissance tools in Kali Linux. Each tool contributed a different type of publicly accessible information, helping build a broader picture of the target environment. 

- WHOIS was used to collect registration-related information and identify associated nameservers. 

- WhatWeb was used to detect technologies in use by the target website, including content management indicators and plugin exposure. 

- Nslookup was used to resolve the domain to its IP address. 

- Curl -I was used to inspect HTTP response headers and observe exposed technical metadata. 

- Wafw00f was used to determine whether firewall-related protections appeared to be in place. 

- Dnsrecon was used to enumerate visible DNS records such as NS, MX, SPF, TXT, and other service-related entries. 

# 4.2 Network Scanning with Zenmap 

A second exercise was completed on a personal local network using Zenmap. The purpose of this activity was to identify active hosts within the subnet and capture addressing information for basic network visibility. 

The process included the following steps: 

1. Reviewing local network settings using ipconfig in 

   - Windows 

2. Identifying the subnet range used by the system 

3. Entering the subnet into Zenmap 

4. Running a Ping Scan to identify live systems 

5. Recording discovered IP and MAC address information 

6. Opening Zenmap’s Topology view to visualize the network layout 

7. Saving the resulting topology output for evidence 

Host values shown during the exercise included: 

10.0.0.1 

- 10.0.0.2 

10.0.0.3 

# 10.0.0.99 

5. Risk Analysis / Impact 

|Finding|Evidence /<br>Observation|Potential<br>Impact|Risk Level|
|---|---|---|---|
|Exposure of web<br>technology details|CMS and plugins<br>detected by<br>WhatWeb|Could help<br>attackers<br>identify<br>vulnerabilities|Medium|
|Identification of server<br>IP address|Domain resolved<br>via nslookup|Discloses<br>hosting<br>location|Low|
|Exposure of HTTP<br>metadata|Headers retrieved<br>by curl<br>including /wp-<br>json/ endpoint|Facilitates<br>system<br>fingerprinting|Low|
|Detection of WAF<br>technology|ModSecurity<br>identified by<br>wafw00f|Reveals<br>security<br>infrastructure|Low|
|Visibility of DNS<br>infrastructure|DNS records<br>enumerated by<br>dnsrecon|Enables<br>infrastructure<br>mapping|Medium|
|Discovery of multiple<br>active hosts on LAN|Active devices<br>found by Zenmap|May indicate<br>presence of<br>unmanaged<br>devices|Medium|



# I. Exposure of Web Technology Details Explanation: 

The use of tools like WhatWeb revealed the specific content management system (CMS) and plugins that the target website is using. This information is valuable because attackers can use it to identify known 

vulnerabilities associated with those technologies. If the CMS or plugins are outdated or have known security flaws, attackers might exploit them to compromise the site. 

# II. Identification of Server IP Address Explanation: 

By resolving the domain name using nslookup, the server’s IP address becomes known. This reveals the physical or cloud location of the hosting server. While this alone is not highly sensitive, it can help attackers narrow down their attack surface or launch targeted attacks such as denial-ofservice (DoS) against that IP. 

# III. Exposure of HTTP Metadata 

Explanation: 

Inspecting HTTP headers with curl showed metadata including endpoints like /wp-json/. HTTP headers can reveal server software versions, security policies, and other technical details. This metadata helps attackers fingerprint 

the system, allowing them to tailor attacks based on the server’s characteristics or discover API endpoints that might be vulnerable. 

# IV. Detection of WAF Technology Explanation: 

The tool wafw00f detected the presence of a Web Application Firewall (WAF), specifically ModSecurity. Knowing that a WAF is in place informs attackers about the security measures protecting the web application. While a WAF can block many attacks, attackers might also try to find ways to bypass or evade it. 

# V. Visibility of DNS Infrastructure 

Explanation: 

Using dnsrecon to enumerate DNS records exposed details about the domain’s DNS setup, such as nameservers, mail servers, and SPF records. This information helps attackers map the infrastructure supporting the domain, which can be used for social engineering, phishing, or identifying additional attack vectors. 

- VI. Discovery of Multiple Active Hosts on LAN Explanation: 

Zenmap scanning on the local network found several active devices. This could indicate the presence of unmanaged or unknown devices that might pose security risks. Unmanaged devices may have outdated software, weak security settings, or could be rogue devices introduced by attackers to gain network access. 

# 6. Recommendations 

- Limit public exposure of platform/version information. 

- Keep CMS, plugins, and server software updated. 

- Harden HTTP response headers to reduce information leakage. 

- Audit and prune DNS records regularly. 

- Maintain and tune WAF protections. 

- Run scheduled internal discovery scans and reconcile with asset inventory. 

- Investigate and document any unexpected devices. 

- Ensure all testing remains authorized and in-scope. 

# 7. Conclusion
This exercise emphasized how initial information gathering and host discovery provides valuable situational awareness before deeper testing. Findings are informational; further authorized assessment would be required to validate vulnerabilities.


# 8. Evidence collected


# 9. Report Information 

Prepared by: Jevaughn Stewart 

Program: Cybersecurity Program at Networkwalks Week: 02 

Report Type: Practical Lab Documentation 

