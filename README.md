
# Active-Directory-Home-Lab #

# This Active Directory project is a work in progress and will be updated as I continue building it.
To practice and demonstrate fundamental systems administration skills, I built a virtualized Windows domain environment from scratch. With a Windows Server 2022 domain controller that additionally offers DHCP and NAT routing for a separate internal network, the lab simulates a small business network (`itcorp.com`). It demonstrates fundamental IT administration abilities, including group policy configuration, user account management, and fundamental troubleshooting methods, all of which are intended to mimic real-world situations.

<img width="761" height="879" alt="Home Lab Diagram drawio" src="https://github.com/user-attachments/assets/afb05c61-ef2f-4a1b-84a3-c54e3c895e81" />


<details>
<summary>
  
 # VirtualBox - Server 2022 & Windows 11 Setup
</summary>

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



























</details>
