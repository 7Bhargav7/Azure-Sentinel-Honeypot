# Azure Sentinel Honeypot 

## Overview  
This project uses Azure Sentinel SIEM to detect and monitor live RDP brute-force attacks on a virtual machine honeypot.  

## Tools & Technologies  
- Microsoft Azure Sentinel  
- Azure Virtual Machines  
- PowerShell Scripting  
- Geolocation API
(https://ipgeolocation.io/)  

## Steps  

1. Create the Virtual Machine(VM) on the Azure portal
2. Allow all Traffic in the VM firewall
   - Create a Custom network security group with inbound rules open to simulate vulnerabilities by allowing all diffrent types of internet traffic into our virtual machine 
3. Configure Log analytics workspace (LAW)
   - To ingest windows event logs from the VM to the log analytics workspace to further aid Microsoft sentinel to connect to this workspace and display geodata on the map
4. Enable log-collection for the VM
   - Go to Microsoft defender for the cloud
   - under Environment settings for defender plans turn on the plan for "Servers" and save it
   - under Data collection select "All events" and save it
5. Connect log analytics workspace(LAW) to the virtual machine
   - Go to LAW and navigate to the created workspace and under the workspace go to Virtual machines and select connect and establish a connection of VM to LAW
6. Setting up Microsoft sentinel(SIEM for this project)
   - Go to Mircrosoft sentinel and add it to LAW
7. Turn off Windows firewall for the VM
   - temporarily disable firewall to increase honey pot visibility
   - ping the host machine to the VM to check if the VM is completely exposed to inbound traffic
8. Write/Download a Powershell Script to fetch attacker Geolocation data
   - use geolocation.io or (similar ip lookup services) and get API key to implement in Powershell Script
9. Bring Custom log in LAW in Azure portal
   - Navigate to LAW in the portal and select Tables under the created LAW and create a custom log (MMA-based)
   - Now to obtain the log from VM, Navigate to the path where the log is saved and copy the log data from VM and paste it on Notepad and save it on host system
   - upload the log file 
   - provide the log path and wait for the custom log to be created 
10. Use Kusto Query Language (KQL) to extract geolocation data directly from logs.
11. Visualize Data on Azure Sentinel Map
   - Go to Workbooks in Azure Sentinel.
   - Create a new Custom Workbook.
   - Add a Map visualization widget
   - Under Map settings set the metric label and metric value as per the KQL query fields
## Screenshots   
![image](https://github.com/user-attachments/assets/b6c7dac8-c2e9-4054-a467-a770a6e77536)
- Here the metric label and metric value is set as label and event_count respectively



## How to Use  
1. Clone this repository:  
   ```bash
   git clone https://github.com/yourusername/azure-sentinel-honeypot.git
