## Unit 19 Homework: Protecting VSI from Future Attacks

### Scenario

We set up a SOC and monitored attacks from JobeCorp. Here, we are designing mitigation strategies to protect VSI from future attacks. 

---

### System Requirements 

To preform the analysis we used the Splunk app located in our Ubuntu VM.

---

### Logs

The following logs were used to analyze the data.
- Windows Logs = resources/windows_server.logs.csv
- Windows Attach Logs = resources/windows_server_attack_logs.csv
- Apache Webserver Logs = resources/apache_logs.txt
- Apache Webserver Attack Logs = resources/apache_attack_logs.txt

---

### Part 1: Windows Server Attack

Note: This is a public-facing windows server that VSI employees access.
 
#### Question 1
- Several users were impacted during the attack on March 25th.

![](https://github.com/jamesdewhirst/Examples/blob/main/Homework/Images/19-SIEMs-2/20210506_00001.png)

- Based on the attack signatures, what mitigations would you recommend to protect each user account? Provide global mitigations that the whole company can use and individual mitigations that are specific to each user.

![](https://github.com/jamesdewhirst/Examples/blob/main/Homework/Images/19-SIEMs-2/20210506_00002.png)
![](https://github.com/jamesdewhirst/Examples/blob/main/Homework/Images/19-SIEMs-2/20210506_00003.png)

- Recomended Local User Mitigations
   - We found user `k` credentials were used the most
     - We are going to change his user k's user name and password.
     - We are also going to increase the frequency that passwords need to be changed.
     - Users will need to increase password strength using a combination of capital letters, numbers as well as special characters.
     - A password manager is also recommended to keep users from writing down passwords.
- Recomended Global Mitigations
   - Users will be using a VPN (Virtual Private Network) for access
   - Multi-Factor Authentication will be implimented
   - User will also be given a physical login token to increase security
  
#### Question 2
- VSI has insider information that JobeCorp attempted to target users by sending "Bad Logins" to lock out every user.
- What sort of mitigation could you use to protect against this?

- Users will be using a Physical Login Token
- A time based lockout will be implimented which will log all users out one hour after they login

---

### Part 2: Apache Webserver Attack:

#### Question 1
- Based on the geographic map, we recommend a firewall rule that the networking team should implement.
  - Block all incoming HTTP traffic where the source IP comes from the country of Ukraine.

![](https://github.com/jamesdewhirst/Examples/blob/main/Homework/Images/19-SIEMs-2/20210506_00004.png)
![](https://github.com/jamesdewhirst/Examples/blob/main/Homework/Images/19-SIEMs-2/20210506_00005.png)
![](https://github.com/jamesdewhirst/Examples/blob/main/Homework/Images/19-SIEMs-2/20210506_00006.png)
  
#### Question 2

- VSI has insider information that JobeCorp will launch the same webserver attack but use a different IP each time in order to avoid being stopped by the rule you just created.

- The following are screenshots os rules that we can create to protect VSI from attacks againts their webserber.   - More than just a location lets go ahead and block the following verzion of browser from access: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.2; SV1; .NET CLR 2.0.50727987787; InfoPath.1)
  
![](https://github.com/jamesdewhirst/Examples/blob/main/Homework/Images/19-SIEMs-2/20210506_00007.png)
![](https://github.com/jamesdewhirst/Examples/blob/main/Homework/Images/19-SIEMs-2/20210506_00008.png)
![](https://github.com/jamesdewhirst/Examples/blob/main/Homework/Images/19-SIEMs-2/20210506_00009.png)
