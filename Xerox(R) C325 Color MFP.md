<b>CVE Submission Report: Unauthorized Administrative Access in Xerox® C325 Color MFP</b><br>
1. Report Title<br>
Unauthorized Administrative Access Vulnerability in Xerox® C325 Color MFP<br>
2. Vendor<br>
Xerox Corporation<br>
3. Product<br>
VersaLink C325 Color Multifunction Printer (MFP)<br>
4. Affected Version(s)<br>
All firmware versions of the Xerox® C325 Color MFP with the vulnerable Web EWS (Embedded Web Service) interface. The vulnerability was confirmed on devices responding to the network scan pattern `title="Xerox(R) C325 Color MFP"`.<br>
5. Vulnerability Type<br>
CWE-306: Missing Authentication for Critical Function<br>
OWASP Top 10 2021: A01:2021 – Broken Access Control<br>
6. Vulnerability Description<br>
A critical access control flaw exists in the Embedded Web Service (EWS) of the Xerox® C325 Color MFP. The device's web management interface fails to enforce proper authentication and authorization for high-privilege administrative functions. <br>Specifically, an unauthenticated attacker can directly access and exploit interfaces meant for creating new users and changing the administrator password, without providing any valid credentials.<br>
<br>
This vulnerability allows a remote attacker to gain complete administrative control over the affected device, compromising all its functions (print, copy, scan, fax) and any documents stored in its memory.<br>
7. Proof of Concept (PoC) & Attack Scenario<br>
Step 1: The attacker accesses the device's web interface via its IP address (e.g., http://<target_ip>).<br>
Step 2: Without logging in, the attacker navigates directly to the user management section (e.g., #/Settings/Security/UsernamePasswordAccounts).<br>
Step 3: The attacker can perform two critical unauthorized actions:<br>
    - Create Admin User: Clicks "Add User," enters a username (e.g., admin1), sets a password, selects the "Administrator" permission group, and saves. A new admin user is successfully created.<br>
    - Change Admin Password: Clicks on the existing admin user, changes its password, and saves. The default administrator password is now under the attacker's control.<br>
Step 4: The attacker can now log in with the newly created credentials or the modified admin password, obtaining full administrative privileges.<br>
8. Evidence of Widespread Impact<br>
The vulnerability is not isolated. A search using the FOFA dork title="Xerox(R) C325 Color MFP" revealed numerous devices exposed on the public internet. Successful exploitation was validated on multiple independent assets, confirming this is a systemic flaw in the product's access control logic, not a configuration error on a single device.<br>
<br>
proof of vulnerability：<br>
URL:<br>
http://178235093218.unknown.vectranet.pl:65000/#/Settings/Security/UsernamePasswordAccounts<br>
https://132.247.189.74/#/Settings/Security/UsernamePasswordAccounts<br>
http://69.251.119.14/#/Settings/Security/UsernamePasswordAccounts<br>

![1](https://github.com/user-attachments/assets/8ba6aecc-70d4-4708-80db-6a8607ac333c)<br>
![2](https://github.com/user-attachments/assets/0a482652-8036-43a1-a698-06abb571db11)<br>
![3](https://github.com/user-attachments/assets/22d4683d-23ce-4a6d-98de-0b45319dbc7a)<br>
![4](https://github.com/user-attachments/assets/30db9b29-f1ae-4055-8c9d-57cf8b1b0287)<br>
![5](https://github.com/user-attachments/assets/3f2f16c7-c061-407a-99cb-165ee2aed5ab)<br>
![6](https://github.com/user-attachments/assets/45054d7c-06a1-4d13-bfaf-bb24d33aba40)<br>
![7](https://github.com/user-attachments/assets/49d7570d-8bbf-4454-b96a-8682fb44f3c1)<br>
![8](https://github.com/user-attachments/assets/53cd90f0-e36c-44eb-8a38-58e67af55910)<br>
![9](https://github.com/user-attachments/assets/5563f10b-46c4-4797-8803-9dca208ef2a3)<br>
![10](https://github.com/user-attachments/assets/5730961c-512e-4459-ab66-cd9420329b0c)<br>
![11](https://github.com/user-attachments/assets/580ea1dc-4e97-46ab-9742-aae9c91edd23)<br>
![12](https://github.com/user-attachments/assets/5d40cd78-340f-4ca6-bd40-df9dbe677cc1)<br>
![13](https://github.com/user-attachments/assets/6dd7ae6c-bfe6-481c-b383-a8d4047ce487)<br>
![14](https://github.com/user-attachments/assets/75277c9e-822e-4b7a-bf82-8a3940b7377f)<br>
![15](https://github.com/user-attachments/assets/7989454c-d4ba-4d8f-b68a-ee562b126698)<br>
![16](https://github.com/user-attachments/assets/8c974710-15f7-4070-a858-b519e8737368)<br>
![17](https://github.com/user-attachments/assets/9762674d-9d36-4928-91de-9c233568f0d9)<br>
![18](https://github.com/user-attachments/assets/a5fb2d1c-10ee-4840-a4b9-719a41f4358c)<br>
![19](https://github.com/user-attachments/assets/b09c4f8b-d52b-48fb-b55f-5b8e086b6bdd)<br>
![20](https://github.com/user-attachments/assets/bbf802ea-931c-4681-8eb9-1a7afc2ed860)<br>
![21](https://github.com/user-attachments/assets/beaba436-a33a-42c7-9c51-52e558e03064)<br>
![22](https://github.com/user-attachments/assets/bee357d4-40d1-412b-bf1a-40c85860445f)<br>
![23](https://github.com/user-attachments/assets/c8829b5b-3d5c-4379-92d9-a7c0372c0ed7)<br>
![24](https://github.com/user-attachments/assets/cc180356-1655-47ad-b6f9-a806b387b8de)<br>
![25](https://github.com/user-attachments/assets/da01623f-ef08-44ea-b852-5a5d0da67701)<br>
![26](https://github.com/user-attachments/assets/dc1c1729-c51f-4b33-b80a-cd455a39d4bb)<br>
![27](https://github.com/user-attachments/assets/dd883d11-1e0b-410e-af49-047cc860f33d)<br>
![28](https://github.com/user-attachments/assets/e0e46abe-bd45-4a3e-a0a3-df8caa670ef4)<br>
![29](https://github.com/user-attachments/assets/f944c3bf-ddd2-47c6-9220-0a1725e724c3)<br>

<br>Sample Vulnerable URLs (Proof of Exposure):<br>
<br>
http://69.251.119.14<br>
http://91.217.53.123:8080<br>
http://70.93.183.121:81<br>
http://91.3.23.37:8084<br>
http://208.101.93.163<br>
http://132.239.31.227<br>
http://128.32.198.2<br>
http://130.255.157.224<br>
http://83.243.164.11<br>
http://91.3.19.231:8084<br>
http://80.140.241.121:8084<br>
http://50.198.11.82:81<br>
http://132.247.189.74<br>
http://81.141.222.199<br>
http://67.22.217.133<br>
http://71.66.4.146<br>
http://178235093218.unknown.vectranet.pl:65000<br>
http://biw.schramm-fahrschule.de:8084<br>
http://p97f9a3z83887pp8.myfritz.net:8084<br>
http://87.177.188.85:8084<br>
http://50.198.11.82:83<br>
http://5.13.240.236<br>
http://178.235.93.218:65000<br>
http://87.177.177.186:8084<br>
http://80.140.232.253:8084<br>
http://24.227.28.212<br>
http://62.103.89.184:10010<br>
http://83.243.178.242<br>
http://6a7hb1hev5c8yuj4.myfritz.net:8084<br>
http://5.148.74.136<br>
http://66.96.2.54<br>
http://24.123.127.170<br>
http://66.96.2.209<br>
http://96.90.46.138:81<br>
http://75.108.104.116<br>
http://75.110.226.148<br>
<br>
9. Impact<br>
- Complete Device Compromise: An attacker can take full administrative control of the MFP.<br>
- Data Breach: Access to scanned documents, print job history, and network configuration files.<br>
- Network Pivot: The compromised device can be used as an initial foothold for lateral movement within the corporate network.<br>
- Service Disruption: Critical device settings can be altered, disrupting office operations.<br>
10. Suggested Remediation<br>
- Vendor (Xerox): Issue a firmware update that enforces strict session validation and authorization checks for all administrative endpoints (/Settings/, /Security/ paths). Implement a default-deny policy for unauthenticated requests to management interfaces.<br>
- End Users:<br>
  1. Immediate Isolation: Disconnect affected devices from the public internet. Restrict management interface access to trusted internal networks via firewall rules.<br>
  2. Apply Updates: Check for and install the latest firmware from Xerox support immediately upon release.<br>
  3. Security Hardening: Disable HTTP, FTP, and Telnet if not required. Use strong, unique passwords for all accounts.<br>
11. Discoverer<br>
[yan min ]

