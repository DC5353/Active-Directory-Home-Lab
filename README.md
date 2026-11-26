
# Active-Directory-Home-Lab #

# This Active Directory project is a work in progress and will be updated as I continue building it.
To practice and demonstrate fundamental systems administration skills, I built a virtualized Windows domain environment from scratch using **VirtualBox**. With a **Windows Server 2022** domain controller that additionally offers DHCP and NAT routing for a separate internal network, the lab simulates a small business network (`itcorp.com`). It demonstrates fundamental IT administration abilities, including group policy configuration, user account management, and fundamental troubleshooting methods, all of which are intended to mimic real-world situations.

<img width="761" height="897" alt="Home Lab D drawio" src="https://github.com/user-attachments/assets/21b756f4-a5cf-420c-86ac-1559cae4447a" />


## VirtualBox - Initial Steps to Get Started
<details>
<summary>Start by downloading VirtualBox & Windows Server 2022 & Windows 11. Then configure the virtual machine hardware settings.</summary>

# 1. Download and install VirtualBox
  - To start, visit the [VirtualBox website](https://www.virtualbox.org/) and download the latest version.
  - Follow the installation wizard to complete the setup.

# 2. Download the Windows Server 2022 & Windows 11 ISO
 - To download the Windows Server 2022 ISO, go to the [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022) and search for "Windows Server 2022." For both, you will need to select your language, and I recommend saving both ISO files in a folder that is not in your Downloads folder.


<img width="1259" height="1272" alt="Windows Server 2022" src="https://github.com/user-attachments/assets/482817ee-2c10-4c8e-9b9e-27b9527cf118" />


 - To download the Windows 11 ISO, go to the [Microsoft Software Download Page](https://www.microsoft.com/en-us/software-download/windows11).

<img width="1263" height="684" alt="Windows 11 ISO" src="https://github.com/user-attachments/assets/166e8148-3405-4bdd-b30f-6670e701e15d" />


# What is an ISO file?
An ISO file is an uncompressed, sector-by-sector digital replica of optical discs (CDs, DVDs, or Blu-rays) that serve as virtual installation media for virtual machines. In this use scenario, I'm mounting these ISO files and booting from them using VirtualBox virtualization software, much like you would with a real PC, laptop, or disk.

# 3. Creating a new virtual machine
 - To start creating a new virtual machine, open VirtualBox and click `"New"`.

   <img width="1276" height="744" alt="VirtualBox Setup" src="https://github.com/user-attachments/assets/ca911927-1c76-4c53-8379-ed6bd0ecb857" />

 - Then, starting with **Virtual machine name and operating system**, name your VM after the ISO file you are using; for example, mine is `Windows Server 2022 DC1`. DC stands for Domain Controller; I plan on adding a 2nd controller later on. However, yours can be `Windows Server 2022`.
 - Select the Windows Server ISO image.
 - I unchecked `Proceed with Unattended Installation`, then pressed `Finish`.

<img width="803" height="551" alt="VM name" src="https://github.com/user-attachments/assets/5773c593-c61a-48e7-87de-bfcefbbff209" />

# 4. Configure Virtual Machine Hardware Settings
 - Before spinning up the VM, make sure it runs properly on your PC or Laptop.
 - Now click on the settings icon, and your Windows Server settings should appear.

<img width="1279" height="746" alt="Before Spin up" src="https://github.com/user-attachments/assets/d48346a1-2dca-40df-9ad5-354d535544fd" />

 - There are a lot of settings changes you can make to make your project easier for yourself, and I will walk you through them.

**General**
 - In the `General tab`, go to `Features` in Shared Clipboard & Drag-and-Drop, and set it to Bidirectional. This feature allows you to go back and forth between your PC/Laptop and the VM while being able to copy and paste & Drag-and-Drop files.

<img width="776" height="515" alt="VM Features" src="https://github.com/user-attachments/assets/ceb84d13-3db9-47b5-a6f1-8c40666ac492" />

**System**
 - In the `System tab`, go to `Motherboard` for the base memory increase for a smoother experience. 2048MB equals 2GB; double will be 4096MB, equaling 4GB, and so on. I will be allocating 4GB of RAM. Make sure your system can handle the load.

<img width="778" height="508" alt="System M" src="https://github.com/user-attachments/assets/d7aefc81-611c-4337-ac9b-a170d2a11411" />

- Still in the `System tab`, go to `Processor` to increase the number of CPUs for a smoother experience. I will be allocating 4 CPU cores. Again, make sure your system can handle the load.

<img width="774" height="509" alt="System P" src="https://github.com/user-attachments/assets/9affcde0-0e21-4ac1-9714-6b56c2f566ed" />

**Network**
 - Moving on to the `Network tab`, since the network adapter is already enabled on `Adapter 1`, go to `Adapter 2`, enable it, and attach an `internal Network` card.

 **Note** `- The lab uses an isolated internal network so the domain controller can provide DHCP and DNS without conflicting with my home network. Because that network has no direct route to the internet, I configured RAS/NAT on the domain controller. It translates client traffic from the internal NIC out through the Internet NIC, giving domain clients internet access while keeping them isolated.`

<img width="772" height="505" alt="Network A" src="https://github.com/user-attachments/assets/6e5d02ba-a934-42f9-b347-7b083e4acd26" />

 - Now press `OK` to save and finish.

</details>

## VirtualBox - Installing Windows Server 2022


<details>
<summary>Getting Windows Server 2022 Online.</summary>
  
 - Open VirtualBox, select the Server 2022 VM, and click `Start`.

<img width="1276" height="744" alt="Install S" src="https://github.com/user-attachments/assets/b642e96c-e249-427f-990b-2b33980e9778" />

 - Once the VM boots, set up your Language, time, currency format, and Input method, then click `Next`.

<img width="1017" height="847" alt="W 2022" src="https://github.com/user-attachments/assets/053157e7-afdd-41e6-b1d8-a059adbe1608" />

 - On the Windows setup screen, click `Install Now`.

<img width="1022" height="849" alt="iNSTALL N" src="https://github.com/user-attachments/assets/40b28306-201b-416d-8282-89ffc282c29b" />

 - On the next page, make sure to select `Desktop Experience`, then click `Next`.

<img width="1024" height="851" alt="Install desk" src="https://github.com/user-attachments/assets/a5920ffc-7e90-43c6-9914-8ff6c9019f0e" />

 - Accept the License terms, then click `Next`.

<img width="1024" height="849" alt="License" src="https://github.com/user-attachments/assets/7bbc6210-3588-4f87-8696-6ab132c9d436" />

 - On the next page, select `Custom Install`.

<img width="1025" height="848" alt="Install C" src="https://github.com/user-attachments/assets/0afda5ac-c607-4e5a-a35f-d939e358209d" />

 - On the Disk Allocation page, select the 50GB drive, then click `Next`.

<img width="1021" height="846" alt="Disk A" src="https://github.com/user-attachments/assets/a5a5c5d4-46ce-444e-9053-77baf7d95aab" />

Windows will then begin the installation process & restart itself.

<img width="1019" height="849" alt="install p" src="https://github.com/user-attachments/assets/acd5238d-8adf-41d5-808d-958c30c344de" />

 - Once prompted, enter a password. I recommend something easy and write it down somewhere just in case; after all, this is just a lab. Then click `Finish`.

<img width="1018" height="840" alt="C settings" src="https://github.com/user-attachments/assets/aced8d4e-be65-4d01-abc6-d21ebc7a868c" />

 - When at the Windows login screen, press Ctrl + Alt + Del, then enter the password to log in.

<img width="1020" height="856" alt="W login" src="https://github.com/user-attachments/assets/1059312b-94e3-4ce3-a09f-1907d0553b77" />

 - The VM is now ready! Just repeat the process to create a Windows 11 Virtual Machine.

<img width="1019" height="854" alt="Working Server" src="https://github.com/user-attachments/assets/85d3a03b-0c4b-49c4-bc51-ae2b8ef0c601" />

  </details>

 ## VirtualBox - Fixing Mouse Lag and Display Scaling Issues

<details>
<summary>Fixing Mouse Lag and Scaling Issues</summary>
  
  - While the virtual machine is running, you will notice mouse lag and improper display scaling.
  - Go to Devices in the VirtualBox menu and select `Insert Guest Additions CD image...`.

<img width="1019" height="849" alt="Insert G A CA image" src="https://github.com/user-attachments/assets/5089fc3b-421f-496c-82f7-e9686bd8531d" />


 - Within the VM, Open `File Explorer` and navigate to `This PC`.
 - Under `Devices and Drives`, open the `CD Drive (D:) VirtualBox Guest Additions`.

<img width="1023" height="846" alt="CD Drive" src="https://github.com/user-attachments/assets/e160686d-0af6-406c-add8-918901472bb8" />

 - Run `VBoxWindowsAdditions-amd64` and complete the installation steps. Make sure it is the `amd64` application. 

<img width="1021" height="845" alt="VGA" src="https://github.com/user-attachments/assets/0cfb5359-1c95-413e-b80e-a70880c8133e" />

 - The mouse will now move smoothly, and the display scaling adjusts correctly, allowing for a better user experience.

  </details>

## Active Directory Domain Services (AD DS)

The primary server function in Microsoft's Active Directory platform that offers directory services, authentication, and authorization for Windows domain networks is called Active Directory Domain Services (AD DS). It serves as a centralized, hierarchical database that stores access rights and security policies for network objects such as users, groups, machines, and devices. To add AD DS, use Server Manager to add the role, configure it as the principal domain controller, and set up the domain itcorp.com or your own domain name to install AD DS. In the lab setting, this stage lays the groundwork for centralized management and security.
  
<details>
<summary>Installing Active Directory Domain Services</summary>

 ## Changing the Server Name

The first step is to identify the server by changing its name.

  1. Start by navigating to `Settings` and clicking `About`, then select `Rename this PC`.

<img width="1413" height="999" alt="Settings PC" src="https://github.com/user-attachments/assets/eab8606f-70b4-473c-8813-5daa4e42317f" />

 2. Now change the server name; I will be using `ITCorp-DC1`, then click `Next`.

<img width="1416" height="988" alt="Name Change" src="https://github.com/user-attachments/assets/f65359de-897b-4753-9f81-6a3755b3df54" />

 3. Now restart to commit the name change after you log back in and verify the name has been successfully changed.  

<img width="1415" height="994" alt="Restart nsme" src="https://github.com/user-attachments/assets/959dd043-616e-461c-8cb4-d5e5cec76a1b" />

<img width="1413" height="995" alt="Succ N" src="https://github.com/user-attachments/assets/136345c0-48dc-408b-aa9f-7e8eceb5d94d" />

 ## Installing Services for the Server

 Launch Server Manager

 1. When you log in, Server Manager should automatically open; if not, navigate to the Windows `Start`, then `Server Manager`.

 2. In Server Manager, click `Manage`, then add `Roles and Features`.

<img width="1412" height="1000" alt="Rols   F" src="https://github.com/user-attachments/assets/345b7fd0-62e7-417c-bf82-16063dc74f13" />

3. An installation wizard will appear; click `Next`.

<img width="1408" height="996" alt="Begin" src="https://github.com/user-attachments/assets/00a1f08e-e6d7-4c59-bb3d-0a4809dcf38f" />

 4. Choose `Role-based or Feature-based Installation`, then click `Next`.

<img width="1413" height="990" alt="Type" src="https://github.com/user-attachments/assets/7e77aee6-3c39-49b3-bf8f-46d72e207eca" />

 5. Click `Select a server from the server pool` and click `Next`.

<img width="1410" height="992" alt="destin" src="https://github.com/user-attachments/assets/24c66e12-4286-41b0-9b0f-4682f1e71b9d" />

 6. For right now, select `Active Directory Domain Services`, click `Add Features`, then click `Next`. We will come back to add more as we finish one step at a time.

<img width="1415" height="1003" alt="ADDS +" src="https://github.com/user-attachments/assets/1d15f1cc-463b-43a9-a083-50b8a1026570" />

 7. On the `Features` tab, leave everything as is, then click `Next`.

 8. On the `AD DS` tab, click `Next`, then click `Install` on the Confirmation tab.

<img width="1409" height="995" alt="ADDS in" src="https://github.com/user-attachments/assets/b20eaaea-1f39-4a80-af35-93ab195bce2b" />

<img width="1412" height="967" alt="ADDS Confirm" src="https://github.com/user-attachments/assets/d843319f-0f8e-4ef8-84bb-c31c9d2a12aa" />

 9. After the installation is complete, click `Promote this server to a domain controller`.

<img width="1416" height="963" alt="Promote" src="https://github.com/user-attachments/assets/06b97fa9-07f0-454d-a632-16f92a211a86" />

 10. Add a New Forest: I'll be using ITCrop.com. Then click `Next`.

<img width="1413" height="970" alt="D forest" src="https://github.com/user-attachments/assets/ca36163b-e0c5-4dd7-93ba-4f2d2f1f850d" />

 11. Now enter a password. I recommend that you use the same one or a slightly different one; just have it down somewhere. Then click `Next`.

<img width="1411" height="966" alt="Pass DC" src="https://github.com/user-attachments/assets/ccf824c3-a303-4716-9030-dbe8713e25fc" />

12. DNS Options: Leave unchecked and click `Next`.

13.  NetBIOS Name: Leave as is and click `Next`.

14.  Paths Tab: Keep defaults and click `Next`.
   
15.  Review Tab: Click `Next`.

16.  Prerequisites Check: Click `Install`.

<img width="1415" height="965" alt="Prerequisites Check" src="https://github.com/user-attachments/assets/407a43ed-cde0-4f49-bb7e-1e7f5c335a0c" />

 17. Once the installation is complete, the VM will automatically restart.

</details>

 ## Configuring a Static IP

Configuring a static IP on the domain controller's internal NIC provides DNS, DHCP, and routing must keep a fixed address so clients can always locate it. A changing IP would break domain authentication, name resolution, and internet access for every client.

<details>
<summary>Configuring a Static IP for the DC</summary>

 1. To start, access the network adapters within the VM. On the Server Manager Dashboard, click `Local Server` then click one of the Ethernet adapters.

<img width="1458" height="969" alt="IPv4" src="https://github.com/user-attachments/assets/b9c2e66d-6c5d-473f-97dc-319383649d14" />














  
</details>




    
  














