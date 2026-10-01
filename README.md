# EDU-200---ZScaler-Administrator

EDU200 = ZScaler Administrator

-- First we onboard the users.
-- Then we need to identify what users would be given access to what resources. 

We will start working on quite a few labs. But the topology will remain same below. 

<img width="2528" height="1392" alt="image" src="https://github.com/user-attachments/assets/1b9bc0e8-f4d0-4603-b0bc-8e13cfadc713" />

Windows Client PC
o Name - Corp: Client PC
o The Client PC is joined to Active Directory patraining.safemarch.com.
o Username | Password: student | Admin-123!

Windows Server
o Name - Corp: Win Svr
o Provides local directory services through Active Directory.
o Hosts the Active Directory domain patraining.safemarch.com, to which the Corp: Client PC is joined.
o Runs HTTP/HTTPS Intranet applications and file services.
o Functions as the DNS server for hosts in the data center.
o Username | Password: administrator | Admin-123!

App Connectors
o Names - Corp: App Connector
o It's a Red Hat Enterprise 9.4 VM, pre-deployed in the network to simulate the results of having previously
instantiated the OVA/OVF file to deploy the VM with the App Connector RPM already installed.
o Username | Password: admin | zscaler

This is how the Zscaler Admin Portal Looks like 

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/42265493-2b0a-42da-b744-8f7c8e667d60" />

Now, 

The first step to setup the tenant is to create departments. 

here we have created one support and one IT department. 

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/0806ffcf-111d-437d-82b3-62c227b6bd16" />

Then we will create a user group
