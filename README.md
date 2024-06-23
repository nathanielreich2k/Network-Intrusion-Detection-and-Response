# Network Intrusion, Detection, and Response using Snort and Wireshark.🦈🥸

## Introduction
✨Network intrusion detection is a vital component of cybersecurity. It encompasses the surveillance and examination of network traffic to identify indications of unauthorized entry or malicious actions. This initiative strives to equip you with the abilities necessary to establish an Intrusion Detection System (IDS), identify network intrusions, and implement appropriate countermeasures.

## Skills Learned

-Configuring the Snort tool to monitor and log network traffic.
-Simulating basic traffic and malicious traffic using Metasploit
-Capturing data using the wireshark application


### Setting Up the Lab Environment

#### 1. Install VirtualBox
- Download and install VirtualBox from the [official website](https://www.virtualbox.org/).

#### 2. Create Virtual Machines
- **IDS VM**: 
  - Create a new VM and install Ubuntu.
  - Install Snort:
    ```sh
    sudo apt-get update
    sudo apt-get install snort
    ```
  - Configure Snort for basic intrusion detection.

- **Client VM**: 
  - Create a new VM and install Ubuntu.
  - Ensure it is connected to the same network as the IDS VM.

- **Attacker VM**:
  - Create a new VM and install Kali Linux.
  - Kali Linux comes pre-installed with Metasploit and other penetration testing tools.

#### 3. Configure Network Settings
- Set all VMs to use a Host-Only Adapter in VirtualBox to ensure they are on the same virtual network and isolated from the host machine’s network.

#### 4. Install and Configure Tools
- **Wireshark**: Install Wireshark on the IDS VM for traffic analysis.
  ```sh
  sudo apt-get install wireshark

## Tasks

### Task 1: Setting Up and Configuring Snort
**Objective**: Set up Snort on the IDS VM to monitor network traffic.

**Steps**:
1. Install Snort on the IDS VM (if not already done).
2. Configure Snort to monitor the network interface:
   ```sh
   sudo nano /etc/snort/snort.conf
   ```
   Set the HOME_NET variable to the IP range of your virtual network.
   Add rules to detect basic intrusions.
3. Start Snort in IDS mode:
```sh
Copy code
sudo snort -A console -q -c /etc/snort/snort.conf -i eth0
```
4. Verify Snort is monitoring traffic and logging alerts.

Expected Output:

Snort running and logging alerts to the console or a log file.

### Task 2: Generating Network Traffic
Objective: Generate normal and malicious network traffic to test the IDS.

**Steps**:

1. use tools like ping, curl, or iperf on the Client VM to generate normal traffic.
2. On the Attacker VM, use Metasploit to launch a simple attack:
```sh
msfconsole
use auxiliary/scanner/portscan/tcp
set RHOSTS <Client_VM_IP>
run
```
Output:

Snort logs normal traffic without alerts.
Malicious traffic is detected and logged by Snort with alerts.

### Task 3: Analyzing Network Traffic with Wireshark
Objective: Capture and analyze network traffic using Wireshark on the IDS VM.

**Steps**:

1. Start Wireshark and select the network interface to monitor.
2. Capture traffic while generating both normal and malicious traffic.
3. Use Wireshark filters to isolate and analyze specific types of traffic (e.g., ICMP, TCP SYN scans).

**Output**:
- Captured network traffic with clear differentiation between normal and malicious traffic.
- Detailed analysis of packet contents and patterns.

### Task 4: Responding to Detected Intrusions
Objective: Respond to detected intrusions based on Snort alerts.

**Steps**:

1. Review Snort alerts and identify the type and source of the intrusion.
2. Implement network defenses such as:
     - Blocking the attacker's IP using iptables:
```
    sudo iptables -A INPUT -s <Attacker_IP> -j DROP
```

3. Document the incident and response actions.

**Expected Output**
- Effective blocking of the attacker's IP.
- Enhanced network security through updated firewall rules.
- Comprehensive incident response documentation.


## Conclusion
To identify potential malicious traffic running on a network, it is important to utilize tools such as Wireshark and Snort to capture data for review. Incorporating Metasploit as a penetration tool can aid in simulating an attack so that work can be carried out to fix vulnrabilities before an event could occur.




































