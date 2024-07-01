# Setting Up a Honeypot in Microsoft Azure



![Banner](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/6d3ace39-dbbe-43fc-8aad-fdd636ead33c)
<br />
<br />

To kick off my **Azure Honeynet project**, we must first set up the **Virtual Machines (VMs)** we'll use.

Virtual machines are like computers in the cloud, and they'll form the foundation of our Honeynet.

Here are the steps we'll take in **Microsoft Azure**:

<br />
<br />


## 1️⃣ Sign in to the Azure Portal

The first step is to log into your **Azure Account**.

If you don't have an account yet, **[you can create one here.](https://portal.azure.com)**

<br />
<br />


## 2️⃣ Create a Virtual Machine:

Once you're in the **Azure Portal**, navigate to the "***Virtual machines***" section. 
  
![azure portal](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/7fb3a3c7-300f-4a6c-be99-08385d652a40)

<br />
<br />
  
Click on "***Create***", then "***Azure virtual machine***" ➜ This is where we'll set up our new VM.
  
 
![VM create](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/55672c37-2314-4acf-8380-c4db6f2dc475)
  
<br />
<br />
  
  
## 3️⃣ Configure the Virtual Machine's Settings:
  
### *Subscription and Resource Group:*

- We'll select our **Azure subscription** and **Resource group** ➜ Which is a way to group and manage resources in Azure.
- For the purpose of the project, I already created a **Resource group** called ```RG-Cyber-Lab2``` 

  
### *Virtual Machine Name:*

- For the purpose of this project, I have named this **VM** ```Lab-HoneyNet```

### *Region:*

- For the purpose of this project, I have chosen the **Region** ```(US) East US 2```
  
### *Availability Options:*

- Being that the only purpose of this **Virtual Machine** will be to act as a **Honeypot**, we do not require any form of availability, so I selected ```No infrastructure redundancy required```

### *Image:*

- Select ```Windows 10 Pro, version 21H2 - x64 Gen2```
  
  ![VM create](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/6552ee36-48ad-4019-9c4f-091e5bccc828)

### *Networking:*

- When creating the **Virtual network**, we will be leaving it to the **default** settings.
- For the purpose of this lab, I called mine ```Lab-VNet```.
  
  ![netowkr](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/d1fae176-6879-4199-b0be-f56e8d2d437b)
  
<br />
<br />
  
 
## 4️⃣ NSG/Inbound Security Rule Configuration:
 
### *Navigate to the Network Security Group (NSG):*

- In the Azure portal, search for 'Network Security Groups' in the search bar at the top.
- Once there, select the NSG associated with your virtual machine.
  
### *Create an inbound security rule:*

- Inside the NSG, you'll find a section for "**Inbound security rules**".
- This is where we control what kind of traffic is allowed to reach our VM.
- Click on "***Add***" to create a "**new rule**".

### *Configure the rule:*

- We'll be prompted to input some details about our new rule.
  
### *Source:*

- This defines where the incoming traffic is coming from.
  
  - We can set this to ```Any``` to allow traffic from any location.
  
### *Source port ranges:*

- This specifies the ports on the source (the computer initiating the connection) that are allowed.

  - Again, we can set this to ```*``` or ```Any``` to allow all ports.

### *Destination:*

- This defines where the traffic is going to.

  - Since we want the traffic to reach our VM, we can set this to ```Any```.
  
### *Destination port ranges:*

- This specifies the ports on our VM that are allowed to receive traffic.

  - We can set this to ```*``` or ```Any``` to open all ports.
  
### *Priority:*

- Setting priorities in Network Security Groups (NSGs) is an essential step.
- The priority determines the order in which rules are applied.
- Rules with lower priority numbers are processed before rules with higher priority numbers because the lower the number, the higher the priority.

  - For the purpose of this lab, I set the priority to ```300``` to ensure that this honeypot functions as intended!

### *Action:*

- We'll set this to ```Allow```, which means that traffic matching this rule will be allowed to reach our VM. 
  
 ![NSG](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/0bf17e13-1f81-42ac-8692-dbf3bbbdf893)

  
### *Review & Create:*

- After configuring all the details we need for this inbound rule, click "***Add***" to **Create the Rule**.
 
  
<br />
<br />
  

# Conclusion

By **Creating our VMs** and **Open Inbound Security Rules**, we're essentially leaving the front door of our VM wide open.

This is generally not something you'd do in a real production environment, as it would make your system extremely vulnerable to attacks.

However, in the context of our honeynet, it's exactly what we want to do!

This allows us to **Attract Potential Attackers** and **Observe their Actions in a Controlled Environment**.

  
<br />
<br />
  
 
 
