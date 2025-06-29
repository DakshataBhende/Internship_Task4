# Task 4 : Setup and Use a Firewall on Windows/Linux

- Objective: Configure and test basic firewall rules to allow or block traffic.
- Tools: Windows Firewall / UFW (Uncomplicated Firewall) on Linux.
- Deliverables: Screenshot/configuration file showing firewall rules applied.

## System Details
- **Operating System:** Windows 10 / 11
- **Firewall Tool:** Windows Defender Firewall with Advanced Security
- **Testing Tool:** Telnet Client (built-in)

## Steps Followed

### Step 1: Open Windows Firewall Settings
- Press `Windows + R`, type `wf.msc`, and hit Enter
- This opens **Windows Defender Firewall with Advanced Security**
![Screenshot 2025-06-29 180212](https://github.com/user-attachments/assets/ac6a87f4-ae68-4b79-8960-2ba6c5e42c15)
---
### Step 2: Block Inbound Traffic on Port 23 (Telnet)
1. Click **Inbound Rules** → **New Rule**
2. Select **Port**, click **Next**
![image](https://github.com/user-attachments/assets/704e200c-e74b-48de-af8b-e2a417b15c33)
3. Choose **TCP**, enter port `23`, click **Next**
4. Choose **Block the connection**, click **Next**
5. Select all profiles (Domain, Private, Public), click **Next**
6. Name the rule **"Block Telnet Port 23"** → click **Finish**
![Screenshot 2025-06-29 180937](https://github.com/user-attachments/assets/12d1e12b-d497-4d7d-8aa9-131e9a700647)
---
### Step 3 (Optional): Create a Rule to Allow Port 22 (SSH)
- Repeat the above steps using port **22**
- Choose **Allow the connection**
- Name the rule: `Allow SSH (Port 22)`
---
## Testing the Rule

### Step 4: Enable Telnet (for Testing)
1. Open **Command Prompt as Administrator**
2. Run:
   ```cmd
   dism /online /Enable-Feature /FeatureName:TelnetClient
![Screenshot 2025-06-29 181610](https://github.com/user-attachments/assets/7503bd8c-8448-4104-bdb4-20b3ad0b4593)
---
### Step 5: Test Port 23 Block
Run this in Command Prompt:
```cmd
telnet localhost 23
```
If firewall is correctly blocking the port:
- Connection fails or times out
- No Telnet banner or prompt appears
![Screenshot 2025-06-29 182022](https://github.com/user-attachments/assets/27c4e4f0-e0f6-42bd-83c3-ef40f350ba2e)
---
### Step 6: Disable Telnet After Testing (Optional)
```cmd
dism /online /Disable-Feature /FeatureName:TelnetClient
```

## What I Learned
- Hands-on experience with Windows firewall rule creation
- Understanding of port-specific traffic blocking
- Importance of filtering unused or risky ports (e.g., Telnet)

> Outcome: Basic firewall management skills and understanding of network traffic filtering.

## Additional Learnings
While working on this task, I discovered that beyond basic firewall rules, there are free tools and platforms like **Shodan**, **Nmap**, and **PortQry** that allow for more advanced firewall and network visibility testing. These tools help identify exposed services, scan open ports, and analyze how firewalls respond to different types of traffic — giving deeper insight into real-world security scenarios.
