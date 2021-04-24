# GoodSecurity Penetration Test Report
### James Dewhirst
#### JamesDewhirst@GoodSecurity.com
Date of Report: 4/23/2021

### 1. High-Level Summary
GoodSecurity was tasked with performing an internal penetration test on GoodCorp’s CEO, Hans Gruber. An internal penetration test is a dedicated attack against internally connected systems. The goal of this test is to perform attacks similar to those of a hacker and attempt to infiltrate Hans’ computer to determine if it is at risk. GoodSecurity’s overall objective was to exploit any vulnerable software, find a secret recipe file on Hans’ computer, and report the findings back to GoodCorp.

The internal penetration test found several alarming vulnerabilities on Hans’ computer: When performing the attacks, GoodSecurity was able to gain access to his machine and find the secret recipe file by exploiting two programs with major vulnerabilities. The details of the attack are below.

### 2. Findings
- Machine IP:
  - 192.168.0.20
- Hostname:
  - MSEDGEWIN10
- Vulnerability Exploited:
  - `icecast`
- Vulnerability Explanation:
  - It allows access to the computer network to inject malicious code allowing a system takeover.  
- Severity:
  - 
- Proof of Concept:
  - ANSWER - This is where you show the steps you took. Show the client how you exploited the software services. Please include screenshots.  
  - There should be a separate finding for each vulnerability found.

### 3. Recommendations
What recommendations would you give to GoodCorp?
  - Update all software to the current versions to ensure all security patches are up to date.
  - Impliment more robust firewall rules
  - Impliment SSL certs on employee machines
  - Block all network traffic and only allow employees access via their specific DNS
