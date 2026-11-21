
# Active-Directory-Home-Lab #

# This Active Directory project is a work in progress and will be updated as I continue building it.
To practice and demonstrate fundamental systems administration skills, I built a virtualized Windows domain environment from scratch. With a Windows Server 2022 domain controller that additionally offers DHCP and NAT routing for a separate internal network, the lab simulates a small business network (`itcorp.com`). It demonstrates fundamental IT administration abilities, including group policy configuration, user account management, and fundamental troubleshooting methods, all of which are intended to mimic real-world situations.

<img width="761" height="879" alt="Home Lab Diagram drawio" src="https://github.com/user-attachments/assets/afb05c61-ef2f-4a1b-84a3-c54e3c895e81" />


<details>
<summary>
  
 # VirtualBox - Server 2022 & Windows 11 Setup
</summary>

# 1. Download and install VirtualBox.
  - To start, visit the [VirtualBox website](https://www.virtualbox.org/) and download the latest version.
  - Follow the installation wizard to complete the setup.

# 2. Download the Windows Server 2022 & Windows 11 ISO
 - To download the Windows Server 2022 ISO, go to the [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022) and search for "Windows Server 2022."
 - To download the Windows 11 ISO, go to the [Microsoft Software Download Page](https://www.microsoft.com/en-us/software-download/windows11).

# What is an ISO file?
An ISO file is an uncompressed, sector-by-sector digital replica of optical discs (CDs, DVDs, or Blu-rays) that serve as virtual installation media for virtual machines. In this use scenario, I'm mounting these ISO files and booting from them using VirtualBox virtualization software, much like you would with a real PC, laptop, or disk.

</details>
