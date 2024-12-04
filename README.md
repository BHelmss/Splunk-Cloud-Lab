# Chronicle Phishing Lab

## Objective

In this lab, I will use Chronicle to invesitgate a security incident involving a phishing scenario. I am a security analyst at a financial services company. I receive an alert that an employee received a phishing email in their inbox. I review the alert and identify a suspicious domain name contained in the email's body: signin.office365x24.com. I need to determine whether any other employees have received phishing emails containing this domain and whether they have visited the domain. I will use Chronicle to investigate this domain

Lab from Google Certification.

### Skills Learned

- Accessing threat intelligence reports on domains
- Identifying assets that accessed malicious domains
- Evaluating HTTP Requests
- Identifying additional domains within an attack infrastructure
  
### Tools Used

- Chronicle SIEM

## Steps
1 Load Up Chronicle
   
  - 1.1 The data was already ingested into Chronicle since this project is through Google. Below I analyzed the different aspects of the homepage.
    
    ![image](https://github.com/user-attachments/assets/ffe09ad9-61c8-4d77-9fde-1a6f2a8d1f69)


2 Perform the domain search
   
  - 2.1 Now I will search for the domain that was included in the domain of the phishing email to see of other instances involving the domain in the network. The domain exists as           seen below.

    ![image](https://github.com/user-attachments/assets/77896dd4-f9d7-47ed-8380-97700fa569ee)


  - 2.2 After clicking the above domain link, I am brought to the domain view of Chronicle. I can view all of the following fields from this view:
    
    ![image](https://github.com/user-attachments/assets/f8f7bb7b-4e98-4158-b898-51abe8324e97)


      -VT CONTEXT: This section provides the VirusTotal information available for the domain.
    
      -WHOIS: This section provides a summary of information about the domain using WHOIS, a free and publicly available directory that includes information about registered domain       names, such as the name and contact information of the domain owner. In cybersecurity, this information is helpful in assessing a domain's reputation and determining the            origin of malicious websites.
    
      -Prevalence: This section provides a graph which outlines the historical prevalence of the domain. This can be helpful when you need to determine whether the domain has been        accessed previously. Usually, less prevalent domains may indicate a greater threat.
     
      -RESOLVED IPS: This insight card provides additional context about the domain, such as the IP address that maps to signin.office365x24.com, which is 40.100.174.34. Clicking          on this IP will run a new search for the IP address in Chronicle. Insight cards can be helpful in expanding the domain investigation and further investigating an indicator          to determine whether there is a broader compromise.
    
       -SIBLING DOMAINS: This insight card provides additional context about the domain. Sibling domains share a common top or parent domain. For example, here the sibling
       domain is listed as login.office365x24.com, which shares the same top domain office365x24.com with the domain you're investigating: signin.office365x24.com.
    
       -Click TIMELINE. This tab provides information about the events and interactions made with this domain. Click EXPAND ALL to reveal the details about the HTTP requests made          including GET and POST requests.  A GET request retrieves data from a server while a POST request submits data to a server.
    
       -Click ASSETS. This tab provides a list of the assets that have accessed the domain. 
    

3 Determine whether the domain is malicious
   
  - 3.1 Check the VT context and see that many security vendors have flagged this domain as a security threat.

    ![image](https://github.com/user-attachments/assets/f0b36d10-3941-4bf8-a571-627a18dba36b)



4 Investigate the affected assets and events
   
  - 4.1 In the hosts tab I can see which hosts accessed this domain. This would give me a lot of information on what assets could be damaged or compromised.
    
      ![image](https://github.com/user-attachments/assets/83d7829a-bd6b-420a-99b0-926db35c7177)


  - 4.2 The timeline displays a time based sequence of events involving this domain. If I select an event it will give me more information such as the type of http request such as    GET or POST. POST is particularly important because it means data was sent to the domain (could hint at a successful phishing attempt).
    
    ![image](https://github.com/user-attachments/assets/db9d63e1-d2d7-460c-bc95-f0ce691bacb6)


5 Investigate the resolved IP addresses
   
  - 5.1 We can see that this domain is most likely malicious, so it is important to see if this domain uses any other domains in its attack infrastructure. I can see below that two   IPs resolved to the domain name.

      ![image](https://github.com/user-attachments/assets/780bd5ee-6175-4ff7-bfc8-e14bf0795409)


  - 5.2 First I will view the 40.100.174.34 IP. In the domain section, I can see this IP also resolves to the signin.accounts-gooqle.com domain. This fake login domain has a typo     which could have been a give away for the assets affected by the phishing attack. I can also see the affected assets and timeline as seen below.
    
      ![image](https://github.com/user-attachments/assets/04ceeb58-f041-4f7f-b32d-9d8a68e4f419)
      ![image](https://github.com/user-attachments/assets/6628204c-d9c8-4286-ad77-d6bb08b6f3e9)
      ![image](https://github.com/user-attachments/assets/aa344707-5a89-4fbc-aa5e-697efd879173)




