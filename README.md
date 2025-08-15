# Cybersecurity-Internship---Task-4
# Setup and Use a Firewall on Windows/Linux

## Objective

Configure and test basic firewall rules to allow or block traffic using Windows Firewall.

***

## Environment

- **OS:** Windows 11
- **Firewall:** Windows Defender Firewall with Advanced Security

***

## Tasks Completed

- Listed current firewall rules
- Blocked inbound traffic on port 23 (Telnet)
- Tested blocked port connection
- Documented all commands/GUI steps and results
- Answered key interview questions
- Added screenshots as evidence

***

## Steps Followed

### 1. List Current Firewall Rules

- Opened **Windows Defender Firewall with Advanced Security** (`wf.msc`)
- Navigated to **Inbound Rules** to view current configuration

### 2. Add Rule to Block Telnet Port (23)

- Selected **Inbound Rules**
- Chose **New Rule** → **Port** → **TCP**, entered **23**
- Selected **Block the connection**
- Applied to all profiles
- Named rule: `Block Telnet Port 23`
- Verified rule added in the rule list

_See screenshot: Block Telnet Port 23 rule created and enabled (Screenshot 161736)

### 3. Test the Rule (Telnet Blocked)

- Opened **Command Prompt**
- Attempted to use `telnet localhost 23`
- Error: `'telnet' is not recognized as...`  
  (Telnet client not installed by default on Windows)

_See screenshot: Telnet client test and error shown (Screenshot 161736)

- Used **PowerShell** alternative command:
  ```powershell
  Test-NetConnection -ComputerName localhost -Port 23
  ```
- Result:  
  ```
  WARNING: TCP connect to (127.0.0.1 : 23) failed
  TcpTestSucceeded: False
  ```
- Verified that the firewall rule successfully blocks port 23 for both IPv4 and IPv6[2]

_See screenshot: PowerShell test result confirming block (Screenshot 162555)

### 4. Remove Test Block Rule (If Needed)

- Located `Block Telnet Port 23` in the firewall list
- Right-clicked and deleted the rule to restore original state

### 5. Documentation and Screenshots

- Screenshots included:
  - Firewall rules list (with block rule visible)
  - Command Prompt / PowerShell showing failed connection attempts

***

## How Firewall Filters Traffic

A firewall acts as a barrier, filtering incoming and outgoing network packets based on defined rules. When a block rule for port 23 is active, the firewall discards incoming TCP packets destined for port 23, preventing unsafe Telnet connections.[3][1]

***

## Interview Questions

1. **What is a firewall?**  
   A firewall is a security system that monitors and controls incoming and outgoing network traffic based on predefined security rules. It acts as a barrier between trusted and untrusted networks.

2. **Difference between stateful and stateless firewall?**  
   - Stateless: Examines each packet independently, without remembering previous packets.
   - Stateful: Monitors active connections and makes decisions based on the state of the connection.

3. **What are inbound and outbound rules?**  
   - Inbound rules control traffic coming into your computer.
   - Outbound rules control traffic leaving your computer.

4. **How does UFW simplify firewall management?**  
   UFW (for Linux) provides easy-to-use commands for managing firewall rules, hiding the complexity of iptables.

5. **Why block port 23 (Telnet)?**  
   Telnet communicates without encryption, so blocking port 23 prevents insecure remote logins and protects from eavesdropping and attacks.

6. **What are common firewall mistakes?**  
   - Overly permissive rules
   - Not testing configurations
   - Forgetting to allow essential services
   - Not removing obsolete rules

7. **How does a firewall improve network security?**  
   By filtering unauthorized traffic, blocking threats, and enforcing policies, firewalls significantly reduce risk.

8. **What is NAT in firewalls?**  
   Network Address Translation (NAT) allows multiple devices on a local network to share a single public IP, hiding internal IPs and adding a layer of security.

***
