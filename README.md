<div align="center">
  <img width="500" height="461" alt="image" src="https://github.com/user-attachments/assets/ed0b4fdc-56e8-4337-9742-7612cb94a9ef" />
</div>

# OSCP Made Easy



### Table of Contents:

- [Web](#web)
- [Linux](#linux)
- [Windows](#windows)
- [Active Directory](#active-directory)
- [Labs](#labs)

## Introduction

This is a culmination of me looking through all of the resources I could find for the OSCP exam. I will give all of the important topics, resources to learn, and commands to copy. I have also attached my CherryTree notes that I used to pass my exam.

### The Exam:
  You are given **23 hours and 45 minutes** to complete this exam. After, you are given another **24 hours** to submit your documentation. The exam must be proctored, so read the [proctoring tool manual](https://help.offsec.com/hc/en-us/sections/360008126631-Proctored-Exams).
  
### Exam Structure:
  
  The OSCP exam is structured like this:

  - **3 stand alone machines (60 point total):**
      - 20 points for each of the 3 machines
        
        -  10 points for low-privilege (local.txt)
        -  10 points for privilege escalation (proof.txt in /root/ or the Administrator Desktop)
        
  - **1 Active Directory set with 3 machines (40 point total):**
      - 10 points for machine 1 (client)
      - 10 points for machine 2 (client)
      - 20 points for machine 3 (domain controller)
   
  Possible scenarios to pass the exam (70/100):
  - 40 points AD + 3 local.txt flags
  - 40 points AD + 2 local.txt flags + 1 proof.txt flag
  - 20 points AD + 3 local.txt flags + 2 proof.txt flags
  - 10 points AD + 3 fully completed stand alone machines

### Exam Restrictions:
  - Spoofing (IP, ARP, DNS, NBNS, etc.)
  - Commercial tools (Metasploit Pro, Burp Pro, etc.)
  - Automatic exploitation tools (db_autopwn, browser_autopwn, SQLmap, SQLninja, etc.)
  - Mass vulnerability scanners (Nessus, NeXpose, OpenVAS, Canvas, Core Impact, SAINT, etc.)
  - AI Chatbots (OffSec KAI, ChatGPT, YouChat, etc.)
  - Features in other tools that utilize either forbideen or restricted exam limitations.

### Metasploit Restrictions:
  The usage of Metasploit and the Meterpreter payload are restricted during the exam. You may only use Metasploit modules (**Auxiliary, Exploit, and Post**) or the Meterpreter payload against only **one** single target machine of your choice. Once you have selected your one single target machine, you cannot use Metasploit modules (Auxiliary, Exploit, or Post) or the Meterpreter payload against any other machines.

  Metasploit/Meterpreter should not be used to test vulnerabilities on multiple machines before selecting your one target machine (this includes the use of **check**). You may use Metasploit/Meterpreter as many times as you would like against your one target machine.

  If you decide to use Metasploit or Meterpreter on a specific target and the attack fails, then you may not attempt to use it on a second target. In other words, the use of Metasploit and Meterpreter becomes locked in as soon as you decide to use either one of them.
  
  Metasploit **cannot** be used for **pivoting**, because it would thereby be used on more than one target.

  However, you can use all of the following against all of the target machines:
  - multi handler (aka exploit/multi/handler)
  - msfvenom

### Documentation

## Enumeration:
  
## Web

## Linux

## Windows

## Active Directory

### Enumeration:

Enumerate Users

```
net user
net user /domain
net user $domain_user /domain
```

Enumerate Groups

```
net group /domain

# Includes domain users that are part of local administrators group
net localgroup administrators
```

PowerView

```
# Import PowerView
PS> Import-Module .\PowerView.ps1

# Get info about current domain
PS> Get-NetDomain

# List all attributes of the user objects
PS> Get-NetUser

# Lists all usernames in the domain
PS> Get-NetUser | select cn

# Lists all groups in the domain
PS> Get-NetGroup | select cn

# List members of Domain Admins group
PS> Get-NetGroupMember -GroupName "Domain Admins"

# List all computers in domain
PS> Get-NetComputer

# Enumerate logged-on users
# NB: only lists users logged on to target if we have local administrator privileges on target
PS> Get-NetLoggedon -ComputerName $hostname

# Enumerate active user sessions on servers e.g. file servers or domain controllers
PS> Get-NetSession -ComputerName $hostname

# Enumerate SPNs
PS> Get-NetUser -SPN | select serviceprincipalname
```

### Attacking:

### Lateral Movement:

### Examples:

## Labs

If you have access to the labs
