# Azure Sentinel Honeypot 

## Overview  
This project uses Azure Sentinel SIEM to detect and monitor live RDP brute-force attacks on a virtual machine honeypot.  

## Tools & Technologies  
- Microsoft Azure Sentinel  
- Azure Virtual Machines  
- PowerShell Scripting  
- Geolocation API (https://ipgeolocation.io/)  

## Steps  
.Create the Virtual Machine(VM) on the Azure portal
.Allow all Traffic in the VM firewall
   - Create a Custom network security group with inbound rules open to simulate vulnerabilities by allowing all diffrent types of internet traffic into our virtual machine 
.Configure Log analytics workspace (LAW)
   - to ingest windows event logs from the VM to the log analytics workspace to further aid Azure sentinel to connect to this workspace and display geodata on the map
.Enable log-collection for the VM
   - Go to Microsoft defender for the cloud
   - under Environment settings for defender plans turn on the plan for "Servers" and save it
   - under Data collection select "All events" and save it
.Connect log analytics workspace(LAW) to the virtual machine
   - Go to LAW and navigate to the created workspace and under the workspace go to Virtual machines and select connect and establish a connection of VM to LAW





## Screenshots  
[Include screenshots here]  

## How to Use  
1. Clone this repository:  
   ```bash
   git clone https://github.com/yourusername/azure-sentinel-honeypot.git
