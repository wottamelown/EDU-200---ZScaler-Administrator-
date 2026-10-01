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

Then we will create a user group so that we could assign the user roles and permissions. 

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/ad103a44-b7d3-42c0-bf93-922b798354cd" />

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/5c39f79c-2a5a-47a1-bf09-24610e6125a7" />

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/733f05dc-a175-4513-8c9b-39ecf87e6507" />

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/78abe6b3-027c-4a98-ac82-d9a6271e7c68" />

Then we will create a Global Admin user named Bev Carey and assign the Global Admin Group. 

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/47e9c353-0520-4a48-8069-f77084b9be61" />

Now 

Task 2.3: Add Administrative and Service Entitlements
In this task, we will assign administrative entitlements and service entitlements to users Joe and Bev.
1. Assign Administrative Entitlement for ZIA (Helpdesk L1):
a. From the Experience Center Dashboard, navigate to Administration > Admin Management > Role Based Access
Control > Administrative Entitlements.
b. Click on Zscaler Internet Access.

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/168ed2d1-ef20-4de0-a331-7428861f2463" />

Here we have given the entitlement as "Executive Insights App" which is somehow read only access. 

Now we will give the helpdesk L1 group access to ZDX, which is dashboard or analytics access with features like Network Monitoring. 

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/1f92800f-4a44-4654-abfc-c7721356ac57" />

Here we can see the admin console of JOE with read only access to analytics. 

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/018cca19-d587-4092-ab68-594618d811a6" />

Task 3.1: Configure Traffic Forwarding Options
In this task, we will configure traffic forwarding so that all users send traffic, regardless of protocol to Zscaler.

The purpose of this is to forward all the traffic using ZScaler best practice forwarding option. Once the client connector is connnected then it will use this infrastructure policy. 

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/5766f880-fe09-4bd9-94cc-3f7b0f0d3d8b" />


<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/a3130951-213e-42dd-8165-0e5cf6b41c10" />

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/f564d869-0df4-41c0-a021-f489a0d9559b" />

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/3b9bab47-25bf-43b6-85bb-58aab9b24fd7" />

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/a2acd292-2b3c-443a-bc82-5d270960d392" />

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/0ba4cd44-d1e5-4663-bcbf-04b96f129d87" />

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/a9e984f6-16b6-40da-9ab2-b39c3b0952d8" />


















