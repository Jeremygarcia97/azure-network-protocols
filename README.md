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
- Observer SSH Traffic
- Observer DHCP,DNS,RDP traffic
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

![image](https://github.com/user-attachments/assets/ec0201e2-d083-4a22-a673-cd16430cf424)
![image](https://github.com/user-attachments/assets/432d2da0-c475-4afc-bfbf-2f4a39297e9b)
![image](https://github.com/user-attachments/assets/058dee3c-1df5-4a81-b7eb-730fccb7ca4c)
![image](https://github.com/user-attachments/assets/04f24712-9527-44eb-ad4f-a4638d78f74e)


<p>
Step 7 Now will will block the ping by adding a firewall, First go into the linux vm on portal azure. click networking setting then inbound security rules and click add at the top. On thr rules go to destination port ranges an put a * inside, then on protocol click ICMPv4 and pirority put 290. When you go back to the see the pings on powershell it will say timed out and thats becasue of the firewall we had placed. In order to allow ICMP traffic again we have to go back into the liunx vm and clear the firewall we place, once that is completed we can go back to powershell on windows vm and see the traffic has statred again. To stop pinging press Control-c.
</p>
<br />

![image](https://github.com/user-attachments/assets/1421afa5-9fc3-4f7e-b7ec-90c4e5ce3a3c)
![image](https://github.com/user-attachments/assets/370f95e0-4498-4b2e-8131-8f2ae7c82f80)
![image](https://github.com/user-attachments/assets/8fad5852-bfd7-4e72-aa5a-7af89cfa4518)


<p>
Step 8 In order to see SSH traffic, you need to go to powershell while still on wireshark. Type ssh labuser@10.0.0.5 on the command line, it will ask you to put a password so type the password that you had put for your liunx vm you create, once that is comppleted it will bring up labuser@linux-vm meaning that you are connected to the linux vm. while on this command prompt, you can type id,hostname and you will see ssh traffic on the backend. When you are done exporing type exit it will closed the connection.  
</p>
<br />

![image](https://github.com/user-attachments/assets/f324c296-27cb-4a13-9c62-19e7882c689e)

<p>
To observed DHCP traffic go to wireshakr anf filter for DHCP, then go to powershell and on the cmd line type ipconfig /renew you might lose connection due to the fact that you are requesting a new IP address after its completed you should have a new IP address and are able to look onm wireshark to see DHCP traffic.
</p>
<br />

![image](https://github.com/user-attachments/assets/a9f2f5eb-de01-47cc-8258-102a05e356db)

<p>
For DNS traffic you can type nslookup disney.com on powershell cmd line and filter for dns traffic on wireshark you will see traffic happen on the backend when you typy in the command. .
</p>
<br />

![image](https://github.com/user-attachments/assets/17230b8e-8d6f-42f5-ae0c-a62c80edc049)

<p>
Type tcp.port==3389 on wireshark to filter for RDP traffic and once you press enter, what you will see is a constant spam of traiffc because RDP traffic is moving your mouse,typing on a keybord its just basically eveything you do on the computuer. That concludes this project on to the next one!!
</p>
<br />
