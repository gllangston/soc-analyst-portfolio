
# Spearphishing Investigation with Malicious Attachment

## Scenario  
A user reported a suspicious email claiming to be from Adobe with a Word document attachment related to a security incident.

---

## Tools Used  
- TheHive (Case Management)   
- VirusTotal (Threat Intelligence)  
- Wazuh (SIEM)  
- Any.Run (Sandbox Analysis)  

---

## Investigation Process  

### Email Analysis  
I analyzed the email and noticed inconsistencies, including an invalid DKIM signature and formatting differences, which made it suspicious.

---

### File Analysis (VirusTotal)  
The file hash was checked in VirusTotal, where multiple vendors flagged it as malicious and associated it with a known exploit. <img width="1414" height="770" alt="VirusTotal Hits" src="https://github.com/user-attachments/assets/981e1914-b6a8-47a1-b9ef-28307170c8cd" />



---

### Behavioral Analysis (Sandbox)  
The file behavior was analyzed in a sandbox environment, revealing that the Word document triggered PowerShell execution and initiated external communication. <img width="1245" height="704" alt="Screenshot 2026-03-21 153632" src="https://github.com/user-attachments/assets/9ea561b4-122a-4a47-a4b7-cee8de46246f" />


---

### SIEM Investigation (Wazuh)  
Logs showed PowerShell execution and outbound connections to a known malicious IP address (159.65.249.205), confirming the file executed. <img width="1407" height="826" alt="Wazuh Log PowerShell + IP" src="https://github.com/user-attachments/assets/837bd0f1-b27f-4395-83a5-02f4565c2daa" />


---

## Key Findings  
- Attachment flagged as malicious by multiple security vendors  
- Evidence of exploit behavior (CVE-2017-0199)  
- PowerShell execution triggered by document  
- Outbound communication to malicious IP  

---

##  Conclusion  
The email was a spearphishing attempt containing a malicious attachment.  
The attachment was executed, leading to outbound communication with a malicious server, indicating the system was compromised.

---

## Skills Demonstrated  
- Email threat analysis  
- Malware validation using threat intelligence  
- Log analysis in SIEM  
- Identifying command & control behavior  
- Incident investigation workflow  
