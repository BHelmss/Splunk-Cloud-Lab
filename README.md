# Splunk Cloud Lab

## Objective

In this project, I will be taking advantage of of Splunk’s Cloud Platform free trial. I will create an account, ingest a new data set, analyze the data utilizing queries and search filters, and undergoing a short security practice scenario.

### Skills Learned

- Uploading Log Data for Ingestion
- Searching through indexed data with queries
- Utilizing filters within the Splunk search
- Simulating a security incident (SSH failed login)

### Tools Used

- Splunk for log ingestion and analysis

## Steps
1 Set up Splunk Cloud Free Trial and login

  - 1.1 After validating my email address and creating an account, I recieved this email.
    ![image](https://github.com/user-attachments/assets/464312fa-78c6-475e-8e58-d5b95c883233)


  - 1.2 The URL brought me to the login page which I could use the temporary credentials to login. After using these credentials, I was prompted to create a new password for the            free trial account.

    ![image](https://github.com/user-attachments/assets/c47f1476-a910-4cb8-b8b0-e731ce300351)


  - 1.3 I was then automatically directed to the Splunk dashboard.
    ![image](https://github.com/user-attachments/assets/e772f0f2-1326-4377-9792-7447454a6f44)


2 Add data to splunk

  - 2.1 I first downloaded the tutorial.zip that I will use for this lab.

  - 2.2 Then I clicked on the settings tab and selected add data. Here I selected the tutorial.zip and set the following settings.
    
    ![image](https://github.com/user-attachments/assets/a4340620-699d-4703-a067-dfb91698b227)

  - 2.3 Once Splunk has ingested the data it gave me this confirmation.
    
    ![image](https://github.com/user-attachments/assets/85994e49-a114-4a44-92e8-fb0963c428e1)


3 Performing a basic search

  - 3.1 Now that the data has been ingested I can go back to the main dashboard and select search and reporting. Here I will conduct the first search query of index=”main”.
      Meaning: This query is specifying which index of data to search within. Here, it is searching the main index which is the default index used by splunk when data is ingested.

    ![image](https://github.com/user-attachments/assets/70842b3d-2d34-42d5-9760-f4d01fcc5023)


4 Evaluate the fields

  - 4.1 Splunk attaches fields to each event when data is indexed. These fields are all searchable to make finding specific information easier. I will first search by host. There 
      are 5 hosts included in the data I will first filter for the mail server host. I selected the host filter in the bottom left and selected the mailsv filter. It automatically        added the filter to the query line.

      ![image](https://github.com/user-attachments/assets/5148803a-1e40-4fee-9c5b-5759461d28e9)


  - 4.2 I can also filter by the source, which are the name of the files in which the event origiantes. Here I am filtering for the mail server security log.
    
      ![image](https://github.com/user-attachments/assets/0887aab6-7b3f-4867-8364-baa9cbe1cecd)



5 Security scenario

  - 5.1 Let’s say that I was tasked with exploring any failed SSH logins for the root account on the mail server. I would first need to narrow the search specifically to the mail           server host and then searches for the keyword fail with the wildcard ‘*’. This will essentially search the main index for any events involving the mail server host. It
        then searches for any occurrence of fail (the wildcard will also search include words like failed and failure). Finally, the root keyword will search for any events that            follow all of the previous criteria and involves the root user.

      ![image](https://github.com/user-attachments/assets/c5348dc7-2fc7-485b-b9cd-77e4d8adc56a)


  - 5.2 As seen above there are over 300 events that match this criteria (all-time). Below I highlight a few of the entries. Here we can see the entire log entry which involves             things like timestamp, hostname, source IP, action, and ports. This many failed attempts in a short time from multiple Ip addresses is definitely a red flag and could be a          sign of a potential incident.
    
      ![image](https://github.com/user-attachments/assets/d1e43da3-c8cd-4ea6-8cff-ec05771e01f8)
