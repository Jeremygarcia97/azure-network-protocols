# azure-network-protocols<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Resource Group 
- Create Virtual macchine for windows and linuxs
- Remote desktop into Vms
- Install & run wireshark
- Fliter for ICMP
- Test connections between vms
- Alter Network Security Group Settings
- Step 4
- Step 4
- Step 4
<h2>Actions and Observations</h2>

![image](https://github.com/user-attachments/assets/f56f2f12-fdc1-4b00-8f48-4e888b743c3c)

<p>
Step 1 create the Resource group.
</p>
<br />

![image](https://github.com/user-attachments/assets/b4a1df24-46fb-4366-bae0-08c3542b328f)


<p>
Step 2 Create Vm for windows, Put vm into the same resource group we had created in the first step and put in same region. Next create a username and password that you will remember and hit review + create at the bottom.
</p>
<br />

![image](https://github.com/user-attachments/assets/0fa8aaa2-24a3-4b29-8eff-4c3bf2ea5ec3)

<p>
The second vm will be a linux/ubuntu, the same as before put into the same resource group and same region. Create username and password and then hit review + create.
</p>
<br />

![image](https://github.com/user-attachments/assets/ab4c5e6a-d23e-4373-b772-e0f9a1f89d08)

<p>
To ensure that both vms have been create, go into resource group that you create and make sure that both vm are inside and running in the resource group.
</p>
<br />

![image](https://github.com/user-attachments/assets/77ef0392-5f0d-4fc2-86e5-2898a70a6dfd)
![image](https://github.com/user-attachments/assets/05305bce-9aec-4916-a396-532929c1bfec)


<p>
Stept 3 Connecting to windows vm using remote desktop is very easy. First you have to get the windows-vm public IP address by going into the virtual machine section on portal azure, copy the public IP address. To get into remote desktop on windows go down to the search bar and type in remote desktop. Put in the IP address,username and password then hit conect.
</p>
<br />

![image](https://github.com/user-attachments/assets/4b8a0964-4a70-44e0-8708-461502546f49)
![image](https://github.com/user-attachments/assets/c54dcd22-4343-465e-b545-caa96842955f)
![image](https://github.com/user-attachments/assets/806f0673-ac78-41df-8aff-c85de4e3d187)



<p>
Step 4 After you had remote desktop in the vitural machine, you are going to download an application call wireshark. Inside the VM not the regular computer you look up wireshark in web browser and click the first windows installer and start downloading the application. once downloaded go and find the application,click on it and highlight Enternet buy clicking it one then at the top left conner click the blue fin to start wireshark. 
</p>
<br />

![image](https://github.com/user-attachments/assets/dd8489f0-b028-4181-830d-dcaffab44c14)

<p>
Step 5 Filter for ICMP traffic but nothing is there.
</p>
<br />

![image](https://github.com/user-attachments/assets/4b8091de-bb3a-4786-a965-da9efaa2d224)
![image](https://github.com/user-attachments/assets/ee211830-895f-4297-9434-de7b0f086953)


<p>
Step 6 To test connection beteween VMs go to the linux vm on portal azure copy the private IP address, Go back to the windowns vm and in the search bar and type in windows powershell. Inside powershell we are going to ping the liunx vm by putting ping then the private IP address of the linux vm. we ping the liunx vm and going back to wireshark we will fliter for ICMP and see how many time we ping for connection.   
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
