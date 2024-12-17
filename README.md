# *Azure Sentinel Honeypot*

## *Overview*  
This project uses *Azure Sentinel* SIEM to detect and monitor live *RDP brute-force attacks* on a virtual machine honeypot. The setup simulates vulnerabilities and showcases real-world attack patterns using geolocation data plotted on Sentinel maps.

---

## *Tools & Technologies*  
- *Microsoft Azure Sentinel*  
- *Azure Virtual Machines*  
- *PowerShell Scripting*  
- *Kusto Query Language (KQL)*  
- [Geolocation API](https://ipgeolocation.io/)  

---

## *Steps*  

1. *Create the Virtual Machine (VM) on the Azure portal*  
2. *Allow all Traffic in the VM firewall*  
   - Create a *Custom Network Security Group* (NSG) with inbound rules open to simulate vulnerabilities by allowing all types of traffic into the VM.  

3. *Configure Log Analytics Workspace (LAW)*  
   - LAW ingests Windows Event Logs from the VM to support Azure Sentinel in displaying geolocation data on the map.  

4. *Enable Log Collection for the VM*  
   - Navigate to *Microsoft Defender for Cloud*:  
     - Under *Environment Settings*, enable the plan for *"Servers"*.  
     - Under *Data Collection, select* *"All events"* and save the configuration.  

5. *Connect LAW to the Virtual Machine*  
   - Go to *LAW > Virtual Machines > Connect* and establish a connection between the VM and LAW.  

6. *Set Up Microsoft Sentinel*  
   - Add *Azure Sentinel* to the created Log Analytics Workspace (LAW).  

7. *Turn Off Windows Firewall for the VM*  
   - Temporarily disable the firewall to increase honeypot visibility.  
   - Validate the VM's exposure by testing its connectivity (e.g., ping).  

8. *Fetch Attacker Geolocation Data*  
   - Write or download the [Custom_Security_Log_Exporter.ps1](relative/path/to/file) PowerShell script.  
   - Use [Geolocation.io](https://ipgeolocation.io/) (or a similar IP lookup service) and include the API key in the script.  

9. *Bring Custom Logs into LAW*  
   - Navigate to *LAW > Tables* and create a *Custom Log (MMA-based)*.  
   - Copy the script output from the VM, save it as a log file, and upload it to LAW.  
   - Provide the log path and wait for the custom table creation.  

10. *Extract Geolocation Data Using KQL*  
   - Write queries in *Kusto Query Language* (KQL) to extract and analyze geolocation data.  
   - Example: [KQLQuery.kql](relative/path/to/file)  

11. *Visualize Data on Azure Sentinel Map*  
   - Navigate to *Workbooks* in Azure Sentinel.  
   - Create a new *Custom Workbook*.  
   - Add a *Map Visualization Widget*.  
   - Configure *Map Settings*:  
     - Set *Metric Label* and *Metric Value* based on the extracted KQL query fields.  

---

## *Screenshot*  
### *World Map of Incoming Attacks After 24 Hours*  
Built custom logs including geolocation data:  

![image](https://github.com/user-attachments/assets/b6c7dac8-c2e9-4054-a467-a770a6e77536)  
- Here, the *Metric Label* and *Metric Value* are set as label and event_count, respectively.  

---

## *Clone This Repository*  
   ```bash
   git clone https://github.com/7Bhargav7/Azure-Sentinel-Honeypot.git
