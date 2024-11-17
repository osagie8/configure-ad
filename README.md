<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

# On-premises Active Directory Deployed in the Cloud (Azure)
My outline of the implementation of on-premises Active Directory within Azure Virtual Machines.


#### Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

#### Operating Systems Used

- Windows Server 2022
- Windows 10 (21H2)
- Ubuntu Server 24.0

#### Overview of Deployment and Configuration Steps

- __Step 1__ - Make Resource Group
- __Step 2__ - Create Virtual Machines
- __Step 3__ - Remote Connect in Virtual Machine
- __Step 4__ - Ensure connection between virtual machines

#### Deployment and Configuration Steps

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

![alt text](/MyScreenshots/SCR-20241117-dqaz-1.png)

- Then Open PowerShell

![alt text](/MyScreenshots/SCR-20241117-dqte.png)

- Type in the ping command followed by the private IP address of the Linux machine. I typed in ping 10.0.0.5

![alt text](/MyScreenshots/SCR-20241117-dqxs.png)

- Powershell tells us that 10.0.0.5 is replying back which means it is in our virtual network.

- Another way to check that both machines are in the same network is by using ssh.

- Use the ssh command followed by the (usernameof linuxmachine)@(PrivateIPAddress). I used ssh labuser@10.0.0.5.

![alt text](/MyScreenshots/SCR-20241117-druz.png)

- You will know that you have succesfully ssh into the linux when the CLI shows the linux machine.

![alt text](/MyScreenshots/SCR-20241117-dsgc.png)

![alt text](/MyScreenshots/SCR-20241117-dshp.png)

- To end the lab firt exit out of the ssh. Then navigate to our Azure Portal > Virtual machines> and select Stop on both machines to save resources.

![alt text](/MyScreenshots/SCR-20241117-dska.png)











