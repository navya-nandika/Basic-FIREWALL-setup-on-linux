Firewall Configuration and Traffic Filtering using UFW
Objective:

To configure and test basic firewall rules on a Linux system using UFW (Uncomplicated Firewall).
This experiment demonstrates how to allow or block specific network traffic and understand how firewalls filter packets.

Tools Used

Operating System: Kali Linux (VMware)

Firewall Tool: UFW (Uncomplicated Firewall)

Testing Tools: nmap, netcat (for connection testing)

Setup and Configuration:
1️.Check if UFW is Installed

Run the following command:

sudo apt install ufw -y
<img width="1053" height="742" alt="image" src="https://github.com/user-attachments/assets/2335f526-8df6-4403-a335-66953bcaa23b" />


2️.Enable UFW

Activate the firewall:

sudo ufw enable
<img width="644" height="102" alt="image" src="https://github.com/user-attachments/assets/b77f81af-d390-4c8c-b9eb-ee4c95d958fc" />


Output:

Firewall is active and enabled on system startup

3.List Current Rules

View all existing firewall rules:

sudo ufw status numbered
<img width="589" height="89" alt="image" src="https://github.com/user-attachments/assets/96ed5da8-197c-463a-bb98-d70970901f36" />


4. Block Inbound Traffic on Port 23 (Telnet)

Add a rule to deny Telnet connections:

sudo ufw deny 23

<img width="563" height="115" alt="image" src="https://github.com/user-attachments/assets/9ef4e423-bff3-4c4c-9e99-321e4e53bc9c" />

Verify:

sudo ufw status


Expected Output:

To                         Action      From
--                         ------      ----
23/tcp                     DENY        Anywhere

5.Test the Rule

Try connecting to port 23:

nc -v localhost 23
<img width="1108" height="479" alt="image" src="https://github.com/user-attachments/assets/87394d8c-0f14-4135-afec-a87ab82c1636" />


You should see:

Connection refused


*This confirms the port is successfully blocked.*

6.Allow SSH (Port 22)

Add a rule to allow SSH traffic:

sudo ufw allow 22
<img width="507" height="105" alt="image" src="https://github.com/user-attachments/assets/9b1c099b-3058-413f-a710-da13e804e25d" />

<img width="676" height="250" alt="image" src="https://github.com/user-attachments/assets/22f9886a-48a6-43ee-923a-927bd252c125" />


7.Delete the Test Rule (Restore Original State)

To remove the Telnet block rule:

sudo ufw delete deny 23

<img width="664" height="313" alt="image" src="https://github.com/user-attachments/assets/38e1c934-74a4-441c-a206-3b82b11b282f" />

8.Disable Firewall (Optional)

If you want to stop UFW after testing:

sudo ufw disable
<img width="664" height="112" alt="image" src="https://github.com/user-attachments/assets/e95800b9-092b-4e23-bb94-c4ba579af95e" />



Concept Summary

Firewall: A network security system that monitors and controls incoming and outgoing network traffic based on predefined security rules.

UFW: Simplified interface for managing Linux’s iptables firewall.

Inbound Traffic: Network connections initiated from outside the system.

Outbound Traffic: Connections initiated by the system to external devices.

Questions:

1️. What is a firewall?

A firewall is a security mechanism that filters network traffic based on rules to protect systems from unauthorized access.

2️. Difference between stateful and stateless firewall?
Type	Description
Stateful	Tracks the state of active connections; allows or blocks packets based on the connection state.
Stateless	Filters packets individually without remembering previous packets.

3️. What are inbound and outbound rules?

Inbound: Controls traffic entering your computer.

Outbound: Controls traffic leaving your computer.

4️. How does UFW simplify firewall management?

UFW provides a simple command-line interface for managing complex iptables rules using easy-to-understand syntax.

5️. Why block port 23 (Telnet)?

Port 23 (Telnet) transmits data in plain text, making it insecure and prone to interception or credential theft.

6️. Common firewall mistakes

Forgetting to allow essential ports (e.g., SSH)

Overly broad “allow” rules

Not logging or monitoring rule activity

Leaving unnecessary open ports

7️. How does a firewall improve network security?

By restricting unauthorized access and filtering malicious traffic, it reduces attack surface and prevents data breaches.

8️. What is NAT in firewalls?

NAT (Network Address Translation) hides internal IP addresses by mapping them to a public IP, enhancing privacy and security.

🧩 Outcome

Successfully configured and tested UFW firewall rules.

Understood how to block and allow specific ports.

Gained practical knowledge of network traffic filtering and rule management.


*Author : Navya Nandika*

*Date : 26th October 2025*
