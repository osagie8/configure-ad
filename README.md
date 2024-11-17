<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Overview A
Deployment and Configuration Steps</h2>

- Step 1
    - Make an Azure Account
- Step 2
    - Deploy two virtual machines
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

- First, lets nagivate to the Azure portal. Here we can view the Azure services they provide us. From here we select on __Resource Groups__.

![alt text](/MyScreenshots/SCR-20241117-dimr-1.png)

- Then we select create resource group.

![alt text](/MyScreenshots/SCR-20241117-disb.png)

- Give the Resource group a name. Im going to be calling it Networkplayground because I plan to test some networking protocols out.

- Then select Review + Create to deploy the resource group.

![alt text](/MyScreenshots/SCR-20241117-diyu.png)

- Now that our Resource group is created, navigate back to the portal. From here go to __Virtual Machines__.

![alt text](/MyScreenshots/SCR-20241117-exmw.png)

- Create a Virtual Machine.

![alt text](/MyScreenshots/SCR-20241117-djqw.png)

- Here is how the Windows VM is configured.
    - Select the RG recently created to make a VM inside of it.
    - Create a VM name, im calling my VM "WindowsVM"
    - I selected (US) West US 2. Use whatever region works for you.
    - Select Windows 10 Pro for the Image
    - Create a Admin user and password.(We will need to later on to sign into VM using this.)
    - Click the checkbox
![alt text](/MyScreenshots/SCR-20241117-dkls.png)

- Goto the networking tab in Azure, and crete a new virtual network by clicking on create new and selecting on 

![alt text](/MyScreenshots/SCR-20241117-dkyw.png)


