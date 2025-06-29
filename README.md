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
3. Choose **TCP**, enter port `23`, click **Next**
4. Choose **Block the connection**, click **Next**
5. Select all profiles (Domain, Private, Public), click **Next**
6. Name the rule **"Block Telnet Port 23"** → click **Finish**
![Screenshot 2025-06-29 180317](https://github.com/user-attachments/assets/4bba375f-c9e1-4258-a001-aed7053e17b1)
---
### Step 3 (Optional): Create a Rule to Allow Port 22 (SSH)
- Repeat the above steps using port **22**
- Choose **Allow the connection**
- Name the rule: `Allow SSH (Port 22)`
![Screenshot 2025-06-29 180317](https://github.com/user-attachments/assets/5668f06e-f6b8-4b80-bc53-8b45a1ed1a1e)
---
## Testing the Rule

### Step 4: Enable Telnet (for Testing)
1. Open **Command Prompt as Administrator**
2. Run:
   ```cmd
   dism /online /Enable-Feature /FeatureName:TelnetClient
   ```
### Step 5: Test Port 23 Block
Run this in Command Prompt:
```cmd
telnet localhost 23
```
If firewall is correctly blocking the port:
- Connection fails or times out
- No Telnet banner or prompt appears

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
