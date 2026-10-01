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

Now we will use this forwarding profile in the policy

ii. Rule Order: 1
iii. Status: Enable
iv. Forwarding Profile: select the HandsOnLab profile created earlier.
v. Install Zscaler SSL Certificate: On
vi. User Groups: Select All.

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/68b726a1-a650-4f8f-ab5c-7d91fe7bc241" />

Now we can see finally our client connector started working. 

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/6f22c09e-6750-452e-bd79-a7d14bc53443" />

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/9d970161-41a4-4aa5-9ae1-90a3cdd213a2" />

Task 4.1: Test Non-Web Traffic with the Default Firewall Block
With Z-Tunnel 2.0, all traffic for all ports and protocols is sent to Zscaler for inspection. In this task, we will generate non-web
traffic from the Corp: Client PC to verify that it is blocked by the default Block/Drop rule.

1. Verify the Default Firewall Policy:
a. From the Experience Center Portal, go to Policies > Access Control > Firewall > Firewall Filtering Policy.
b. Confirm the following:
i. The Default Rule is set to Block/Drop.
ii. There are no other rules that would allow non-web traffic (refer to the example image).

ICMP and SSH traffic blocked in the previous task now needs to be permitted to pass. In this task, you will configure the
firewall policies to allow this traffic.
1. Create a Firewall Filtering Rule to allow ICMP and SSH:
a. From the Experience Center Portal go to Policies > Access Control > Firewall > Firewall Filtering Policy.
b. Click Add Firewall Filtering Rule.
c. Configure the rule:
i. Rule Order: 1
ii. Rule Status: Enabled (default)
iii. Rule Name: allow-outbound-icmp_ssh-student-any
●
[action]-[direction]-[services]-[source-scope]-[destination-scope]

<img width="2908" height="1532" alt="image" src="https://github.com/user-attachments/assets/a64464d6-0505-48a1-b39d-300d8cb807b3" />

Now we will block WhatsApp

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/be33d287-ab0b-44f4-ad3c-0cf171610ae3" />

Lab 5: Configure SSL Inspection Policies
Scenario: As the Zscaler administrator, we are tasked with enabling SSL/TLS inspection to monitor and enforce policies on
users' encrypted web traffic. Since most modern threats are hidden within HTTPS traffic, enabling SSL inspection provides
visibility into encrypted sessions and allows policies to be enforced effectively. We need to configure SSL inspection for all
destinations and define exemptions for trusted or privacy sensitive categories.


Objectives: By the end of this lab, we will:

Enable and configure SSL inspection policies for all encrypted traffic.
Verify Zscaler’s certificate installation on the Windows Corp: Client PC.
Analyze and resolve certificate pinning errors.
Analyze SSL inspection logs and identify inspection or bypass events.

Now we will create a SSL/TLS Policy so that we could inspect the traffic Deeply. 

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/bb093352-27bd-4229-9eb6-58527fe3d4ee" />

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/b774a332-63d1-45fd-80aa-9feafbcaea7e" />

Task 5.3: Review Certificate Pinning Errors
Certificate pinning is a client-side mechanism used to secure applications by verifying that the SSL certificate presented by
a backend server matches a trusted certificate hardcoded into the application. While this approach helps protect against
man-in-the-middle (MITM) attacks, it can also lead to SSL connection failures when the pinned certificate does not match
intercepting proxies, such as Zscaler's SSL inspection certificates. In this task, you will learn two common methods to resolve
certificate pinning errors in applications.

here we will allow threema so Threema app will not work for full inspection. 

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/7a45ccb6-fab7-48e9-89a6-1d6e36af23bd" />

Lab 6: Configure Content Filtering & Access Control
Scenario: As the Zscaler administrator, your goal is to improve users' browsing experience by ensuring they only access safe
and appropriate content. we will explore how Zscaler Internet Access (ZIA) enforces content filtering and access control to
protect against threats such as phishing, malware, and data leakage. You will also verify existing threat protection
configurations, analyze risk reports, and test policy behavior to assess how ZIA enforces organizational baselines for URL
filtering, content categories, and cloud application controls.
Objectives: By the end of this lab, we  will:

Explore ZIA’s threat protection configurations and analyze risk reporting.
Configure and validate a URL Filtering Policy to block risky websites (e.g.,gambling, adult, and shopping sites.
Test the effect of URL Filtering control on end-user experience.
Create and verify a Cloud App Control policy to allow access to specific apps (e.g., YouTube) while restricting others
in the same category.

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/5a4ba1f6-8726-4708-a4b1-fdb42403058e" />

Task 6.2: Configure Content Filtering Controls
In this task, we will create a URL Filtering Policy to block risky URL categories such as gambling, adult content, and video
streaming. we will also verify how content filtering controls work in ZIA to manage user access.


<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/814c9228-96c5-4fb2-b8ee-22e1d8fd65c5" />

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/3a78113a-2ee5-4691-bf19-d516e1a49c10" />

Task 6.4: Configure Cloud App Control
The Cloud App Control Policy provides granular control over how users access specific cloud applications and websites. In
this task, we will create a rule to allow access to YouTube while restricting other entertainment and recreation websites.

Here we will allow youtube but restrict some features of it. 

Lab 7: Configure DNS Security
Scenario: Safemarch aims to protect its users by blocking access to malicious domains and enforcing acceptable use
policies that prohibit access to gambling websites. As a Zscaler administrator, you will configure DNS security controls,
enforce these policies, and validate them using the DNS Insight logs.
Objectives: By the end of this lab, you will:
Configure an App Profile to ensure that all DNS traffic flows through the Zero Trust Exchange.
Create and test a DNS Control Policy to block gambling sites and ensure legitimate domains resolve correctly.
Verify the DNS Control Policy enforcement using DNS Insight Logs to confirm that gambling-related DNS requests are
being blocked.


Now we will go to our windows forwarding profile and add " * " as DNS inclusion so that all the DNS requests go to ZScaler. 

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/cbf83996-b593-4a3e-b815-5d9951adfaf2" />

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/673e3845-2019-4caa-9ad4-0ca551a90144" />

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/2a233ec1-c7f3-453f-834c-f95140eda8db" />

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/ade01514-25f0-464e-b972-7d6f7f26c148" />


Lab 8: Enforce Policy with Unified DLP across Multi-Channel
Scenario: In this lab you will configure and test policies to protect sensitive data in motion and at rest, ensuring compliance
with privacy regulations such as PCI-DSS (Payment Card Industry - Data Security Standard). Using Zscalers Unified DLP
policies, you will secure multi-channel data by analyzing endpoint and SaaS application security logs
Objectives: By the end of this lab you will:
Verify and enable SSL/TLS inspection for data traffic visibility and control.
Configure DLP Dictionaries, DLP Engines, and DLP Rules to detect and block sensitive data, such as credit card
information.
Test policy enforcement to validate that DLP rules block sensitive information in data transfers.

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/b53657ef-e2e0-4b0c-8f4d-21d8696f0264" />

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/92f1ae90-3562-4ad6-8a02-a33f7e94516a" />

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/42421b23-0dca-43fb-8b5b-37da2898c6b6" />

Lab 9: Provision ZPA Infrastructure
Scenario: Safemarch Corporation is preparing to launch internal applications and requires secure, policy-driven
connectivity without exposing those applications to the internet. As a Zscaler administrator, you will deploy and provision
ZPA App Connectors across data centers and cloud platforms. These App connectors provide encrypted connectivity
through the Zero Trust Exchange (ZTE) while keeping internal apps protected.
Objectives: By the end of this lab you will:
Deploy and provision an App Connector using a provisioning key and certificate.
Activate the App Connector, enabling secure communication with the ZPA infrastructure.
Validate the connection and ensure the App Connector is functioning correctly.

Now here we have Windows server which will basically connect to the on prem.

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/301633b9-847d-4a89-a05b-80798c9cef6a" />

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/dc4a587d-79c8-4f36-8a32-2e118987590f" />

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/a8ab3dbd-2a09-4df7-8d26-62c9ec5a82d5" />

Now We will add app connector keys. 

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/a6b79ed7-3c3c-4df8-9790-3acb7ce34bcd" />

now we will upload the txt file to the appconnector VM from our base VM windows server. using WINSCP. 

<img width="2908" height="1678" alt="image" src="https://github.com/user-attachments/assets/0ccc288f-9bb2-471c-a3ec-4c9edce38d0f" />






































