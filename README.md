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

- The Virtual machine has been created. Wait for the Virtual Machine to finish deploying. This should take a couple of minutes.

![alt text](/MyScreenshots/SCR-20241117-dlli.png)

- Navigate back to the Azure portal. Lets create a Linux VM to connect to. Select Virtual Machines. And select create.

![alt text](/MyScreenshots/SCR-20241117-dlqk.png)

- Here is how the Linux VM is configured.
    - Select the RG recently created to make a VM inside of it.
    - Create a VM name, im calling this VM "LinuxVM"
    - I selected (US) West US 2 again. Use whatever region works for you.
    - Select Ubuntu Server 24 for the Imageelect a size thats at lest 2 cpu cores
    - Change Authentication type to password
    - Create a Admin user and password.(We will need to later on to sign into VM using this.)
    
![alt text](/MyScreenshots/SCR-20241117-dmfd.png)

- Select the networking tab and make sure the virtual network is connected to the same virtual network as our Windows VM. In my case, I select WinVnet again. Then select Review + Create to create the VM.

![alt text](/MyScreenshots/SCR-20241117-dncg.png)

- The Virtual machine has been created. Wait for the Virtual Machine to finish deploying. This should take a couple of minutes.

![alt text](/MyScreenshots/SCR-20241117-dnle.png)

- Navigate to Azure Portal > Virtual Machines.
    

![alt text](/MyScreenshots/SCR-20241117-dnrc.png)

- We now have our Virtual Environment setup. Lets Remote Connect to the Windows machine.

- In order to do this please install the Windows App.

![alt text](/MyScreenshots/SCR-20241117-dnxl.png)

- Navigate to the "+" at the Top.

![alt text](/MyScreenshots/SCR-20241117-dobq.png)

- Select Add PC.

![alt text](/MyScreenshots/SCR-20241117-dofw.png)

- Copy the public IP address of the WindowsVM to the clipboard.

![alt text](/MyScreenshots/SCR-20241117-dnrc.png)

- Paste the IP address into the PC name. Make the freindly name of the VM to WindowsVM. Then select add.

![alt text](/MyScreenshots/SCR-20241117-door.png)

- The Windows VM has successfully been created. Select the Windows VM that was just made.

![alt text](/MyScreenshots/SCR-20241117-dort.png)

- Enter the username and password that was created when creating the WindowsVM

![alt text](/MyScreenshots/SCR-20241117-doxt.png)

- Then the app will grant access to the WindowsVM

![alt text](/MyScreenshots/SCR-20241117-dpsn.png)

- Now we want to test the connection between our Windows Machine and our Linux Machine in our virtual Network.

- First grab the Private IP Address from the Linux VM

![alt text](SCR-20241117-dqaz-1.png)

- Then Open PowerShell

![alt text](SCR-20241117-dqte.png)

- Type in the ping command followed by the private IP address of the Linux machine. I typed in ping 10.0.0.5

![alt text](SCR-20241117-dqxs.png)

- Powershell tells us that 10.0.0.5 is replying back which means it is in our virtual network.

- Another way to check that both machines are in the same network is by using ssh.

- Use the ssh command followed by the (usernameof linuxmachine)@(PrivateIPAddress). I used ssh labuser@10.0.0.5.

![alt text](SCR-20241117-druz.png)

- You will know that you have succesfully ssh into the linux when the 

![alt text](SCR-20241117-dsgc.png)

![alt text](SCR-20241117-dshp.png)

![alt text](SCR-20241117-dska.png)











