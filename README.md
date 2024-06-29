# Setting Up a Honeypot in Microsoft Azure



![Banner](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/6d3ace39-dbbe-43fc-8aad-fdd636ead33c)
<br />
<br />

To kick off my Azure Honeynet project, we must first set up the virtual machines (VMs) we'll use.

Virtual machines are like computers in the cloud, and they'll form the foundation of our honeynet.

Here are the steps we'll take in Microsoft Azure:

<br />
<br />


## 1️⃣ Sign in to the Azure portal

The first step is to log into your Azure account.

If you don't have an account yet, **[you'll need to create one!](https://portal.azure.com)**

<br />
<br />


## 2️⃣ Create a virtual machine:

Once you're in the Azure portal, navigate to the 'Virtual machines' section. 
  
![azure portal](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/8148e2f5-ce75-4722-be5d-0b05c3abb68c)

<br />
<br />
  
Click on 'Create', then 'Virtual machine'. This is where we'll set up our new VM!
  
 
![VM create](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/9baa9f3a-0a06-4caf-8a44-cc9271841fe2)
  
<br />
<br />
  
  
## 3️⃣ Configure the VM settings:
  
### Subscription and resource group:

- We'll select our Azure subscription and resource group (Which is way to group and manage resources in Azure!).
- For the purpose of the project, I already created created a resource group called ```RG-Cyber-Lab2``` 

  
### Virtual Machine Name:

- For the purpose of this project, I am going to name this VM, ```Lab-HoneyNet```

### Region:

- For the purpose of this project, I am going to choose the region, ```(US) East US 2```
  
### Availability Options:

- Being that the only purpose of this machine will be to act as a Honeypot, we do not require any form of availability, so I selected ```No infrastructure redundancy required```

### Image:

- Select ```Windows 10 Pro, version 21H2 - x64 Gen2```
  
  ![VM create](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/94169790-533a-4bdf-b264-ef258a66e94a)

### Networking:

- When creating the virtual network, we will be leaving it to the default settings.
- For the purpose of this lab, I called mine ```Lab-VNet```.
  
  ![netowkr](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/623a346c-d0dd-48b2-b25e-a639253d5cb2)
  
<br />
<br />
  
 
## 4️⃣ NSG/Inbound Security Rule Configuration:
 
### Navigate to the Network Security Group (NSG):

- In the Azure portal, search for 'Network Security Groups' in the search bar at the top.
- Once there, select the NSG associated with your virtual machine.
  
### Create an inbound security rule:

- Inside the NSG, you'll find a section for 'Inbound security rules'.
- This is where we control what kind of traffic is allowed to reach our VM.
- Click on 'Add' to create a new rule.

### Configure the rule:

- We'll be prompted to input some details about our new rule.
  
### Source:

- This defines where the incoming traffic is coming from.
- We can set this to ```Any``` to allow traffic from any location.
  
### Source port ranges:

- This specifies the ports on the source (the computer initiating the connection) that are allowed.
- Again, we can set this to ```*``` or ```Any``` to allow all ports.

### Destination:

- This defines where the traffic is going to.
- Since we want the traffic to reach our VM, we can set this to ```Any```.
  
### Destination port ranges:

- This specifies the ports on our VM that are allowed to receive traffic.
- We can set this to ```*``` or ```Any``` to open all ports.
  
### Priority:

- Setting priorities in Network Security Groups (NSGs) is an essential step.
- The priority determines the order in which rules are applied.
- Rules with lower priority numbers are processed before rules with higher priority numbers because the lower the number, the higher the priority.
- For the purpose of this lab, I set the priority to ```300``` to ensure that this honeypot functions as intended!

### Action:

- We'll set this to ```Allow```, which means that traffic matching this rule will be allowed to reach our VM. 
  
 ![NSG](https://github.com/franciscovfonseca/Setting-Up-Vulnerable-VMs-in-Azure/assets/172988970/a2ae6d5b-bad7-4be2-ab79-c9ca14daee2d)

  
### Review & Create:

- After i've input and configured all the details we need for this inbound rule, click 'Add' to create the rule.
 
  
<br />
<br />
  

# Conclusion

By creating our VMs and open inbound security rules, we're essentially leaving the front door of our VM wide open.

This is generally not something you'd do in a real production environment, as it would make your system extremely vulnerable to attacks.

However, in the context of our honeynet, it's exactly what we want to do!

This allows us to attract potential attackers and observe their actions in a controlled environment.

  
<br />
<br />
  
 
 
