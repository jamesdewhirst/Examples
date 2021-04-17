## Week 16 Homework Submission File: Penetration Testing 1
#### Step 1: Google Dorking
- Using Google, can you identify who the Chief Executive Officer of Altoro Mutual is:
	- Karl Fitzgerald
- How can this information be helpful to an attacker:
	- Social engineering and Whale Phishing	

#### Step 2: DNS and Domain Discovery
Enter the IP address for `demo.testfire.net` into Domain Dossier and answer the following questions based on the results:
  1. Where is the company located: Sunnyvale, California
  2. What is the NetRange IP address: 65.61.137.64 - 65.61.137.127
  3. What is the company they use to store their infrastructure: Rackspace Backbone Engineering
  4. What is the IP address of the DNS server: 65.61.137.117
#### Step 3: Shodan
What open ports and running services did Shodan find:
- 80, 443, 8080
- Apache Tomcat/Coyote JSP engine
#### Step 4: Recon-ng
- Install the Recon module `xssed`.
	- `marketplace install xssed`
	- https://github.com/jamesdewhirst/Examples/blob/main/Homework/Screen%20Shot%202021-04-15%20at%208.10.49%20AM.png
- Set the source to `demo.testfire.net`. 
	- `modules load recon/domains-vulnerabilities/xssed`
- Run the module. 
	- `run` OR `execute`
- Is Altoro Mutual vulnerable to XSS:
	- Yes, it has the unfixed status.
### Step 5: Zenmap
Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:
- Command for Zenmap to run a service scan against the Metasploitable machine:
	- `nmap -sV -T4 192.168.0.10` 
- Bonus command to output results into a new text file named `zenmapscan.txt`:
	- `nmap -sV -T4 192.169.0.10 -oN zenmapscan.txt`
- Zenmap vulnerability script command: 
	- `nmap -oN zenmapscan2.txt --script smb -enum -shares 192.169.0.10`
- Once you have identified this vulnerability, answer the following questions for your client:
  1. What is the vulnerability:
	- \\192.168.0.10IPC$:
		- Anonymous access: READ/WRITE
	- \\192.168.0.10/tmp:
		- Anonymous access: READ/WRITE
  2. Why is it dangerous:
	- This allows anyone to have READ/WRITE access
  3. What mitigation strategies can you recommendations for the client to protect their server:
	- Change permissions to reflect <none> rather than READ/WRITE
