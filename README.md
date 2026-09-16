# NETWORKWALKS-B083-WK1-PM1-CYBERSECURITY-LAB-SETUP

The goal of the project is to build and set an isolated lab focused on penetration testing and ethical hacking using VirtualBox and Kali Linux, where various cybersecurity concepts and tools can be practiced safely. It can be used for network scanning and reconnaissance, vulnerability assessment, web application security testing, traffic analysis, exploitation, privilege escalation and digital basic forensics.

The lab is configured on a private virtual network, allowing additional virtual machines to be added as targets for authorized security testing. 

INSTRUCTIONS:
1. Install VirtualBox
   - Download and install the latest recommended version of VirtualBox on your host machine
   - Install the VirtualBox Extension Pack (recommended for full functionality)
2. Set up Kali Linux
   - Create a new virtual machine in VurtualBox
   - Install Kali Linux as the attacking/hacker machine
   - Allocate appropriate CPU, RAM and disc resources.
3. Configure the Network
   - Set the network subnet to 10.0.0.0/24
   - Configure a NATNetwork using the same subnet: 10.0.0.0/24
4. Enable VM Integration Features
   - In the Virtual Machine settings, enable: Clipboard sharing and File drag and drop.
5. Configure Shared Folders
   - Enable Shared Folders in the VM settings
   - Share the /downloads folder from the host machine to the Kali VM.
6. Assign the Kali Linux IP Address
   - Set the Kali Linux IP Address to 10.0.0.0/24
7. Verify Internet Access
   - Confirm that Kali Linux has full Internet access (e.g., ping a public address or load a webpage)
  
SETUP PROCEDURE:

STEP 1: Install 7-Zip. It was installed to extract the Kali Linux virtual machine package, which distributed as a .7z archive. Tool used: 7-Zip
STEP 2: Install VirtualBox. It was installed to act as the hypervisor for the lab environment. Tool used: VirtualBox
STEP 3: Create The NAT Network. A dedicated NAT Network was created in Virtual Box.
        - Network Name: NATNetwork
        - IPv4 Prefix: 10.0.0.0/24
        - DHCP: Enabled
        - IPv6: Disabled
NOTE: A NATNetwork was selected because multiple virtual machines connected to the same NAT Network can communicate with another while also having outbound network connectivity. This will allow future attacker and target VMs to communicate withing the lab.
STEP 4: Import Kali Linux. The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.
STEP 5: Configure The Kali Linux Network. The Kali Linux network configuration was checked and configured with a consistent IPv4 address.
        - IP Address: 10.0.0.2
        - Subnet Mask: 255.255.255.0
        - Gateway: 10.0.0.1
        - DNS: 8.8.8.8
NOTE: A consistent IP address makes it easier to document the lab and reference the Kali machine in the future exercises.
STEP 6: Create a clean VM snapshot.

PROBLEMS ENCOUNTERED AND SOLUTIONS:

1. Kali Linux Has No Internet Access
   Solution: - Opened VirtualBox and selected Kali VM
             - Clicked Settings -> Network
             - Confirmed the adapter was attached to NAT Network (not the standard "NAT") and selected the correct network name (NATNetwork)
             - Inside Kali, i verified the DNS configuration by checking the /etc/resolv.conf file ensuring it contained a valid DNS server (8.8.8.8)
             - Restarted the network interface to apply the changes
Verification: I confirmed internet access was working by running 'ping -c 8.8.8.8'

2. Kali Linux IP Address Not Configured Correctly
   Solution: To resolve this, i manually configured the IP address using terminal commands inside Kali Linux. I used the following syntax to flush any incorrect addresses and assign the correct one:
             sudo ip addr flush dev eth0
             sudo ip addr add 10.0.0.2/24 dev eth0
             sudo ip link set eth0 up
   Verification: I verified the configuration was successful by running:
                 ip a show eth0

   RESULT:
   
The cybersecurity testing lab environment was successfully set up on the host machine. VirtualBox was installed as the hypervisor, and Kali Linux was imported and configured as the attacking machine. The network was configured using a NAT Network on the 10.0.0.2/24 subnet, with Kali Linux assigned a static IP address of 10.0.0.2/24 and verified to have full internet access. A clean VM snapshot was also created to preserve the initial lab.

WHAT I LEARNED:

1. NAT vs NAT Network. A NAT Network allows multiple VMs connected to the same virtual network to communicate with each other while also providing outbound internet connectivity, which is essential for building a multi-machine cybersecurity lab.
2. Virtual Machine Networking. VirtualBox virtual network adapters connect VMs to different types of networks, and how network configuration affects communication between machines.
3. Linux Network Configuration. Learned how to manually configure a static IP address in Kali Linux using terminal commands and how to verify the configuration.
4. Troubleshooting. I learned how to identify and resolve common lab setup issues, such as DNS configuration for internet access.

SOURCES:

1. Download and install 7-zip: https://7-zip.org/download.html
2. Download and install VirtualBox: https://virtualbox.org/wiki/Downloads
3. Download and import Kali Linux Virtual Machine in VirtualBox: https://kali.org/get-kali

Author: Aleksandra Rustamova, cybersecurity professional B083
LinkedIn: https://www.linkedin.com/in/alexandra-rustamova-631a1439a/
Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub


   
