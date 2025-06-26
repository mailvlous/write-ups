# 🕵️‍♂️ Oski Lab

**Category:** Threat Intel  
**Tactics:** Initial Access, Execution, Defense Evasion, Credential Access, Command and Control, Exfiltration  
**Tools:** VirusTotal, ANY.RUN  
**Difficulty:** Easy | ⏱️ 30 Mins


### 📘 Scenario

The accountant at the company received an email titled **"Urgent New Order"** from a client late in the afternoon. When he attempted to access the attached invoice, he discovered it contained false order information. Subsequently, the SIEM solution generated an alert regarding downloading a potentially malicious file. Upon initial investigation, it was found that the **PPT file** might be responsible for this download. Could you please conduct a detailed examination of this file?


### ❓ Questions & Answers



**Q1:** The accountant at the company received an email titled "Urgent New Order" from a client late in the afternoon. When he attempted to access the attached invoice, he discovered it contained false order information. Subsequently, the SIEM solution generated an alert regarding downloading a potentially malicious file. Upon initial investigation, it was found that the PPT file might be responsible for this download. Could you please conduct a detailed examination of this file?

**Answer Q1:**  
Using VirusTotal we can detect threats since we have the MD5 hash. Go to `Details > History`, and then we can see the **Creation Time**, which is:  
**2022-09-28 17:40:46 UTC**



**Q2:** Identifying the command and control (C2) server that the malware communicates with can help trace back to the attacker. Which C2 server does the malware in the PPT file communicate with?

**Answer Q2:**  
We can see malware communicate through the connection URL in the **Relations** section. In the **Contacted URLs**, we see the attacker's server:  
**http://171.22.28.221/5c06c05b7b34e8e6.php**



**Q3:** Identifying the initial actions of the malware post-infection can provide insights into its primary objectives. What is the first library that the malware requests post-infection?

**Answer Q3:**  
Since this malware uses network communication, we can go through the **Behavior** tab. The **HTTP Requests** provide GET and POST methods, and we can see the library **sqlite3.dll** included in the GET method.



**Q4:** By examining the provided ANY.RUN report, what RC4 key is used by the malware to decrypt its base64-encoded string?

**Answer Q4:**  
Go to the ANY.RUN report. We can see the **RC4 key** in the **Malware Configuration**:  
**5329514621441247975720749009**



**Q5:** By examining the MITRE ATT&CK techniques displayed in the ANY.RUN sandbox report, identify the main MITRE technique (not sub-techniques) the malware uses to steal the user’s password.

**Answer Q5:**  
In the ANY.RUN sandbox report, go to the **MITRE ATT&CK** section. Since the question asks for the technique to steal user’s password, we can see it in the **Credential Access** row:

![image](https://github.com/user-attachments/assets/b0112d21-797e-4f07-bb93-4adc757d42e9)  
![image](https://github.com/user-attachments/assets/cd0bacc5-5774-4862-a54e-2e5682773046)



**Q6:** By examining the child processes displayed in the ANY.RUN sandbox report, which directory does the malware target for the deletion of all DLL files?

**Answer Q6:**  
In the ANY.RUN report under **Malware Configuration**, we can clearly see the directory the attacker is targeting:

![image](https://github.com/user-attachments/assets/28400589-aeae-443e-8002-17e6b6c0f6c7)



**Q7:** Understanding the malware's behavior post-data exfiltration can give insights into its evasion techniques. By analyzing the child processes, after successfully exfiltrating the user's data, how many seconds does it take for the malware to self-delete?

**Answer Q7:**  
In the ANY.RUN sandbox report's **Processes Tree**, we can see `timeout.exe` used for **5 seconds** before self-deletion:

![image](https://github.com/user-attachments/assets/db9566db-a288-430f-969e-dd451de7920c)
