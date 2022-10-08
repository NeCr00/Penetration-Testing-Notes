# Nmap Cheat Sheet
Reference guide for scanning networks with Nmap.

**Table of Contents**
1. [What is Nmap?](#what-is-nmap)  
2. [How to Use Nmap](#how-to-use-nmap)  
    1. [Command Line](#command-line) 
3. [Basic Scanning Techniques](#basic-scanning-techniques)  
    1. [Scan a Single Target](#scan-a-single-target)  
    2. [Scan Multiple Targets](#scan-multiple-targets)  
    3. [Scan a List of Targets](#scan-a-list-of-targets)  
    4. [Scan a Range of Hosts](#scan-a-range-of-hosts)  
    5. [Scan an Entire Subnet](#scan-an-entire-subnet)  
    6. [Scan Random Hosts](#scan-random-hosts)  
    7. [Exclude Targets From a Scan](#exclude-targets-from-a-scan)  
    8. [Exclude Targets Using a List](#exclude-targets-using-a-list)  
    9. [Perform an Aggresive Scan](#perform-an-aggressive-scan)  
    10. [Scan an IPv6 Target](#scan-an-ipv6-target)  
4. [Port Scanning Options](#port-scanning-options)  
    1. [Perform a Fast Scan](#perform-a-fast-scan)  
    2. [Scan Specific Ports](#scan-specific-ports)  
    3. [Scan Ports by Name](#scan-ports-by-name)  
    4. [Scan Ports by Protocol](#scan-ports-by-protocol)  
    5. [Scan All Ports](#scan-all-ports)  
    6. [Scan Top Ports](#scan-top-ports)  
    7. [Perform a Sequential Port Scan](#perform-a-sequential-port-scan)  
    8. [Attempt to Guess an Unknown OS](#attempt-to-guess-an-unkown-os)  
    9. [Service Version Detection](#service-version-detection)  
    10. [Troubleshoot Version Scan](#troubleshoot-version-scan)  
    11. [Perform a RPC Scan](#perform-a-rpc-scan) 
5. [Discovery Options](#discovery-options)  
    1. [Perform a Ping Only Scan](#perform-a-ping-only-scan)  
    2. [Do Not Ping](#do-not-ping)  
    3. [TCP SYN Ping](#tcp-syn-ping)  
    3. [TCP ACK Ping](#tcp-ack-ping)  
    4. [UDP Ping](#udp-ping)  
    5. [SCTP INIT Ping](#sctp-init-ping)  
    6. [ICMP Echo Ping](#icmp-echo-ping)  
    7. [ICMP Timestamp Ping](#icmp-timestamp-ping)  
    8. [ICMP Address Mask Ping](#icmp-address-mask-ping)  
    9. [IP Protocol Ping](#ip-protocol-ping)  
    10. [ARP Ping](#arp-ping)  
    11. [Traceroute](#traceroute)  
    12. [Force Reverse DNS Resolution](#force-reverse-dns-resolution)  
    13. [Disable Reverse DNS Resolution](#disable-reverse-dns-resolution)  
    14. [Alternative DNS Lookup](#alternate-dns-lookup)  
    15. [Manually Specify DNS Server](#manually-specify-dns-server)  
    16. [Create a Host List](#create-a-host-list)  
6. [Firewall Evasion Techniques](#firewall-evasion-techniques)  
    1. [Fragment Packets](#fragment-packets)  
    2. [Specify a Specific MTU](#specify-a-specify-mtu)  
    3. [Use a Decoy](#use-a-decoy)  
    4. [Idle Zombie Scan](#idle-zombie-scan)  
    5. [Manually Specify a Source Port](#manually-specify-a-source-port)  
    6. [Append Random Data](#append-random-data)  
    7. [Randomize Target Scan Order](#randomize-target-scan-order)  
    8. [Spoof MAC Address](#spoof-mac-address)  
    9. [Send Bad Checksums](#send-bad-checksums)  
7. [Advanced Scanning Functions](#advanced-scanning-functions)  
    1. [TCP SYN Scan](#tcp-syn-scan)  
    2. [TCP Connect Scan](#tcp-connect-scan)  
    3. [UDP Scan](#udp-scan)  
    4. [TCP NULL Scan](#tcp-null-scan)  
    5. [TCP FIN Scan](#tcp-fin-scan)  
    6. [Xmas Scan](#xmas-scan)  
    7. [TCP ACK Scan](#tcp-ack-scan)  
    8. [Custom TCP Scan](#custom-tcp-scan)  
    9. [IP Protocol Scan](#ip-protocol-scan)  
    10. [Send Raw Ethernet Packets](#send-raw-ethernet-packets)  
    11. [Send IP Packets](#send-ip-packets)    
8. [Timing Options](#timing-options)  
    1. [Timing Templates](#timing-templates)  
    2. [Set the Packet TTL](#set-the-packet-ttl)  
    3. [Minimum Number of Parallel Operations](#minimum-number-of-parallel-operations)  
    4. [Maximum Number of Parallel Operations](#maximum-number-of-parallel-operations)  
    5. [Minimum Host Group Size](#minimum-host-group-size)  
    6. [Maximum Host Group Size](#maximum-host-group-size)  
    7. [Maximum RTT Timeout](#maximum-rtt-timeout)  
    8. [Initial RTT TImeout](#initial-rtt-timeout)  
    10. [Maximum Number of Retries](#maximum-number-of-retries)  
    11. [Host Timeout](#host-timeout)  
    12. [Minimum Scan Delay](#minimum-scan-delay)  
    13. [Maximum Scan Delay](#maximum-scan-delay)  
    14. [Minimum Packet Rate](#minimum-packet-rate)  
    15. [Maximum Packet Rate](#maximum-packet-rate)  
    16. [Defeat Reset Rate Limits](#defeat-reset-rate-limits)  
9. [Output Options](#output-options)  
    1. [Save Output to a Text File](#save-output-to-a-text-file)  
    2. [Save Output to a XML File](#save-output-to-a-xml-file)  
    3. [Grepable Output](#grepable-output)  
    4. [Output All Supported File Types](#output-all-supported-file-types)  
    5. [Periodically Display Statistics](#periodically-display-statistics)  
    6. [1337 Output](#1337-output)  
10. [Compare Scans](#compare-scans)  
    1. [Comparison Using Ndiff](#comparison-using-ndiff)  
    2. [Ndiff Verbose Mode](#ndiff-verbose-mode)  
    3. [XML Output Mode](#xml-output-mode)  
11. [Troubleshooting and Debugging](#troubleshooting-and-debugging)  
    1. [Get Help](#get-help)  
    2. [Display Nmap Version](#display-nmap-version)  
    3. [Verbose Output](#verbose-output)  
    4. [Debugging](#debugging)  
    5. [Display Port State Reason](#display-port-state-reason)  
    6. [Only Display Open Ports](#only-display-open-ports)  
    7. [Trace Packets](#trace-packets)  
    8. [Display Host Networking](#display-host-networking)  
    9. [Specify a Network Interface](#specify-a-network-interface)  
12. Nmap Scripting Engine  
    1. [Execute Individual Scripts](#execute-individual-scripts)  
    2. [Execute Multiple Scripts](#execute-multiple-scripts)  
    3. [Execute Scripts by Category](#execute-scripts-by-category)  
    4. [Execute Multiple Script Categories](#execute-multiple-script-categories)  
    5. [Troubleshoot Scripts](#troubleshoot-scripts)  
    6. [Update the Script Database](#update-the-script-database)  

## What is Nmap?
Nmap ("Network Mapper") is a free and open source utility for network discovery and security auditing. Many systems and network administrators also find it useful for tasks such as network inventory, managing service upgrade schedules, and monitoring host or service uptime. Nmap uses raw IP packets in novel ways to determine what hosts are available on the network, what services (application name and version) those hosts are offering, what operating systems (and OS versions) they are running. It was designed to rapidly scan large networks, but works fine against single hosts.

## How to Use Nmap
Nmap can be used in a variety of ways depending on the user's level of technical expertise.

| Technical Expertise | Usage |
|:--------------------|:------|
| Beginner            | [Zenmap](https://nmap.org/zenmap/) the graphical user interface for Nmap |
| Intermediate        | [Command line](https://nmap.org/) |
| Advanced            | Python scripting with the [Python-Nmap](https://pypi.org/project/python-nmap/) package |

### Command Line
```shell
nmap [ <Scan Type> ...] [ <Options> ] { <target specification> }
```

## Basic Scanning Techniques
The `-s` switch determines the type of scan to perform.

| Nmap Switch | Description                 |
|:------------|:----------------------------|
| **-sA**     | ACK scan                    |
| **-sF**     | FIN scan                    |
| **-sI**     | IDLE scan                   |
| **-sL**     | DNS scan (a.k.a. list scan) |
| **-sN**     | NULL scan                   |
| **-sO**     | Protocol scan               |
| **-sP**     | Ping scan                   |
| **-sR**     | RPC scan                    |
| **-sS**     | SYN scan                    |
| **-sT**     | TCP connect scan            |
| **-sW**     | Windows scan                |
| **-sX**     | XMAS scan                   |


### Objectives:
* Scan a whole Subnet.
* Trace all the sent and received packets.
* Perform a slow comprehensive scan.
* Create a new profile to perform a Null Scan.
* Scan TCP and UDP ports.
* Analyze hosts details and their topology.
* Scanning Techniques:
  * TCP Connect Scan
  * Xmas Scan
  * ACK Flag Scan
  * UDP Scan
  * IDLE Scan
* Avoiding Scanning Detection 

### Requirements:
* Windows server 2012 machine.
* Windows 10 machine.
* Ubuntu [Metasploitable](https://information.rapid7.com/download-metasploitable-2017.html) machine.
* Kali Linux machine.
* Make sure to [configure](https://www.techrepublic.com/article/how-to-create-multiple-nat-networks-in-virtualbox/) properly the network topology on your virtual environment. 

**Note** #0: Since this lab is exclusive on scanning networks, you don't need to download these specifics machines. Since you have any virtual machine to scan (besides the Kali), you good to go.

**Note** #1: You can use whatever Nmap version you prefer. Personally I prefer the CLI version instead of the GUI, is more adaptable to workflow and have a more solid learning curve.

## Scan a whole Subnet
Open the Terminal window and type `nmap -h` to list all the commands available. Since Nmap have so many options, you can use this [cheat sheet](https://nmapcookbook.blogspot.com/2010/02/nmap-cheat-sheet.html), [[2]](https://www.stationx.net/nmap-cheat-sheet/) to view some examples.


`nmap -O <IP Range>`

The option `-O` is related to Operating System Detection.

To specify the IP range you can use two methods:

**Wildcard**:
`nmap -O 10.0.2.*`

**Subnet notation:**
`nmap -O 10.0.2.1/24`

Both do the same, with little differentiations, like the subnet notation is a little bit more faster than wildcard.

**Run this scan and check out the results.**

The Nmap scans the entire network and displays information for all the hosts, along with open ports, device type, details of OS, and so on.

## Trace all the Sent and Received Packets
**Select** one host that you scanned

`nmap --packet-trace 10.0.2.23`

By issuing the `--packet-trace` command, Nmap sends some packets to the intended machine and receives packets in response to the sent packets. It prints a summary of every packet it sends and receives.

The output below show the packets **sent from host to target** and packets **received from target to host**.
```
...
SENT (4.1431s) TCP 10.0.2.15:35962 > 10.0.2.23:3005 S ttl=43 id=22968 iplen=44  seq=1965204224 win=1024 <mss 1460>
SENT (4.1433s) TCP 10.0.2.15:35962 > 10.0.2.23:4000 S ttl=39 id=51710 iplen=44  seq=1965204224 win=1024 <mss 1460>
SENT (4.1434s) TCP 10.0.2.15:35962 > 10.0.2.23:1503 S ttl=53 id=146 iplen=44  seq=1965204224 win=1024 <mss 1460>
SENT (4.1435s) TCP 10.0.2.15:35962 > 10.0.2.23:1761 S ttl=56 id=27951 iplen=44  seq=1965204224 win=1024 <mss 1460>
...
```
Note in the bottom of the output also is shown the open TCP ports:
```
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
88/tcp    open  kerberos-sec
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
389/tcp   open  ldap
443/tcp   open  https
445/tcp   open  microsoft-ds
...
```

## Identifying Services with TCP Null Scan

`nmap -sN -T4 -A <Target IP address>`

`-sN`: TCP Null Scan.<br>
`-T4`: Timing: (4)Aggressive mode speeds scans up by making the assumption that you are on a reasonably fast and reliable network.<br>
`-A`: Enables OS detection, version detection, script scanning, and traceroute 

By issuing this command, Nmap sends TCP packets with none of the TCP flags set in the packet. If the scans returns an RST packet, it means the port is closed; If nothing is returned, the port is either filtered or open.
```
...
53/tcp   open  domain      ISC BIND 9.4.2
| dns-nsid: 
|_  bind.version: 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
|_http-server-header: Apache/2.2.8 (Ubuntu) DAV/2
|_http-title: Metasploitable2 - Linux
111/tcp  open  rpcbind     2 (RPC #100000)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login       OpenBSD or Solaris rlogind
514/tcp  open  tcpwrapped
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
...
```
As shown above, we can se the piece of the output of the scan, performed on the Metasploitable Linux. Later we can check the versions and type of services running on the open ports. This type of information is very valuable because we can search for vulnerabilities, flaws and so on.

# Scanning Techniques 
Nmap comes with various inbuilt scripts that can be employed during a scan process in an attempt to find the open ports and services running on the ports.

Summary of scans that will be performed:
1. **TCP Connect Scan** uses a normal TCP connection to determine if a port is available.
2. **Xmas Scan** involves sending TCP segments with the all flags sent in the packet header, generating packets that are illegal according to RFC 793.
3. **ACK Flag Scan** involves sending ACK probe packet with random sequence number.
4. **UDP Scan** involves sending a generic UDP packet to the target.
5. **IDLE Scan** involves sending spoofed packets to a target. 

## 1. TCP Connect Scan
This is scan is the most basic of TCP scanning. The connect() system call provided by your OS is used to open a connection to every interesting port on the machine. If the port is listening, connect() will succed, otherwise the port is not reachable. One strong advantage to this technique is that you don't need any special privileges.

Perform a TCP scan with a normal timing (`-T3`):

`nmap -sT -T3 -A <Target IP address>`

`-sT`: TCP connect port scan (Default without root privilege).

The scan result includes all the open ports, OS Fingerprint result, nbstat result, smb-os-discovery results, smb version, and so on.

## 2. Xmas Scan
Xmas Scan sends a TCP frame to a remote device with PSH, URG, and FIN flags set. FIN scans only with OS TCP/IP developed according to RFC 793. The current version of MS Windows is not supported.

**Note: The next scan will be on a Firewall-enabled machine (i.e., Windows Server 2012).**

`nmap -sX -T4 <Target IP address>`

`-sX`: Sets the FIN, PSH, and URG flags, lighting the packet up like a Christmas tree
```
Nmap scan report for 10.0.2.23
Host is up (0.00040s latency).
All 1000 scanned ports on 10.0.2.23 are open|filtered
MAC Address: 11:22:33:44:55:66 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 21.64 seconds
```
Nmap returns a result stating that the all ports are **opened/filtered, which means a firewall has been configured on the target machine.**

**Next, turn off the Firewall on the target machine.**

## 3. ACK Flag Scan
The ACK scan never locates an open port. It only provides a "filtered" or "unfiltered" disposition, because it never connects to an application to confirm an "open" state.

This scan initiates ACK scan and displays the port disposition, as show below:

`nmap -sA -v -T4 <Target IP address>`
```
Initiating ARP Ping Scan at 13:18
Scanning 10.0.2.23 [1 port]
Completed ARP Ping Scan at 13:18, 0.04s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 13:18
Completed Parallel DNS resolution of 1 host. at 13:18, 0.05s elapsed
Initiating ACK Scan at 13:18
Scanning 10.0.2.23 [1000 ports]
Completed ACK Scan at 13:18, 1.26s elapsed (1000 total ports)
Nmap scan report for 10.0.2.23
Host is up (0.00029s latency).
All 1000 scanned ports on 10.0.2.23 are unfiltered
MAC Address: 11:22:33:44:55:66 (Oracle VirtualBox virtual NIC)

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 1.51 seconds
           Raw packets sent: 1060 (42.388KB) | Rcvd: 1001 (40.028KB)
```
Attackers send an ACK probe packet with a random sequence number.

* No response means the port is filtered.
* Unfiltered response means the port is closed.

## 4. UDP Scan
UDP scanning is performed to find any UDP ports on the target machine. If have any to determine their state (Open/Closed).

`nmap -sU -T5 <Target IP address>`
```
...
Not shown: 986 open|filtered ports
PORT      STATE  SERVICE
123/udp   open   ntp
137/udp   open   netbios-ns
389/udp   open   ldap
445/udp   closed microsoft-ds
688/udp   closed realm-rusd
1001/udp  closed unknown
1901/udp  closed fjicl-tep-a
8001/udp  closed vcom-tunnel
16674/udp closed unknown
18818/udp closed unknown
28973/udp closed unknown
30656/udp closed unknown
31109/udp closed unknown
57172/udp open   unknown
...
```

## 5. IDLE Scan
IDLE scan is an advanced scan method that performs a truly blind TCP port scan of the target (meaning no packets are sent to the target from your real IP address). Instead, a unique side-channel attack exploits predictable IP fragmentation ID sequence generation on the zombie host to glean information about the open ports on the target.

In this example the zombie will be Windows Server 2012 machine and the target Windows 10 machine using port number 80 (or any port which you want to test).

`nmap -Pn -p 80 -sI <IP address of the zombie> <Target IP address>`
```
Idle scan using zombie 10.0.2.37 (10.0.2.37:80); Class: Incremental
Nmap scan report for 10.0.2.23
Host is up (0.0069s latency).

PORT   STATE SERVICE
80/tcp open  http
MAC Address: 22:44:11:55:66:77 Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 1.08 seconds
```
IDLE scan can be tricky for the first-timers, I recommend try and test out in your own way. I recommend this [link](https://gbhackers.com/idle-zombie-scan-nmap/) for any missing information about it.
***
## Ping Sweep
Ping sweep is a method that can establish a range of IP addresses which map to live hosts.

Now instead of checking for individual systems, we will check for all the systems alive in the network by performing a ping sweep.

`-sP`: Perform a Ping Only Scan

`nmap -sP 10.0.2.*`
```
Nmap scan report for 10.0.2.1
Host is up (0.0011s latency).
MAC Address: 22:44:99:33:11:55 QEMU virtual NIC)
Nmap scan report for 10.0.2.2
Host is up (0.00084s latency).
MAC Address: 22:44:99:33:11:55 (QEMU virtual NIC)
Nmap scan report for 10.0.2.3
Host is up (0.00097s latency).
MAC Address: 11:22:33:44:55:66 (Oracle VirtualBox virtual NIC)
Nmap scan report for 10.0.2.22
Host is up (0.00075s latency).
MAC Address: 11:22:33:44:55:66 (Oracle VirtualBox virtual NIC)
Nmap scan report for 10.0.2.23
Host is up (0.00066s latency).
MAC Address: 11:22:33:44:55:66 (Oracle VirtualBox virtual NIC)
Nmap scan report for 10.0.2.37
Host is up (0.00051s latency).
MAC Address: 11:22:33:44:55:66 (Oracle VirtualBox virtual NIC)
Nmap scan report for 10.0.2.15
Host is up.
Nmap done: 256 IP addresses (7 hosts up) scanned in 2.29 seconds
```
Nmap scans the subnet and shows a list of alive systems as shown above. The result might vary in your lab environment.

# Avoiding Scanning Detection using Multiple Decoy IP Addresses
The Nmap command `nmap -D RND:10` is the decoy option, that lets you scan using multiple decoy IP addresses.

Firewalls and IDS detect normal scanning attempts on the target network. However, you can use the IP address decoy technique to avoid detection.

**Before starting this lab, make sure that you have your Windows Firewall on the target turned on.**

## IP Fragmentation

Open a new Terminal window on Kali and enter the target IP address (Windows).

`nmap -f <Target IP Address>`

`-f`: Used to scan tiny fragment packets.
```
Nmap scan report for 10.0.2.23
Host is up (0.00074s latency).
Not shown: 979 filtered ports
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
88/tcp    open  kerberos-sec
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
389/tcp   open  ldap
443/tcp   open  https
445/tcp   open  microsoft-ds
464/tcp   open  kpasswd5
593/tcp   open  http-rpc-epmap
636/tcp   open  ldapssl
3268/tcp  open  globalcatLDAP
3269/tcp  open  globalcatLDAPssl
3389/tcp  open  ms-wbt-server
MAC Address: 11:22:33:44:55:66 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 13.72 seconds
```
When the Windows Firewall service is turned on, you can only see the ports opened as shown in the output above.

## Perform Maximum Transmission Unit
This command is used to transmit smaller packets instead of sending one complete packet at a time.

This scan is very similar to the previous one but with **Maximum Transmission Unit** (`-mtu`) and `8` bytes of packets.

`nmap -mtu 8 <Target IP Address>`

If everything works, the results should be identical to the previous one.

## Decoying IP address
This command is used to scan multiple decoy IP addresses. Nmap will send multiple packets with different IP addresses, along with your attacker's IP address.

`nmap -D RND:10 <Target IP Address>`

Again, the output is the same as previous outputs but on the target view is very different.

Check the Logs on your Windows Server Firewall and analyze the last scan performed. You also can analyze this information with Wireshark turned on.

Both shows multiple IP addresses along with your real attacker IP address.

![firewall](https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/6c4f716f549aedea473d2701b1f40bb592413e47/firewallLog-RND.png)
_Windows Firewall Log: Decoyed IP Address_

![wireshark](https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/6c4f716f549aedea473d2701b1f40bb592413e47/wireshark-RND.png)
_Wireshark: Decoyed IP Address_


***
**In conclusion**: Nmap is a very powerful tool for network scanning / network security assessments. Basically the must-have tool on your belt when we talk about Network Security, Ethical Hacking or Pentesting.


Useful links:

* [Official Documentation](https://nmap.org/docs.html)
* [Cheat Sheet with Pro Tips](https://hackertarget.com/nmap-cheatsheet-a-quick-reference-guide/)
* [Cheat Sheet](https://nmapcookbook.blogspot.com/2010/02/nmap-cheat-sheet.html)
* [Cheat Sheet 2](https://www.stationx.net/nmap-cheat-sheet/)
* [Zenmap presets](https://www.securesolutions.no/zenmap-preset-scans/) 
* [Bypassing Firewall Rules](https://nmap.org/book/firewall-subversion.html)

### Scan a Single Target
```shell
nmap [target]
```

### Scan Multiple Targets
```shell
nmap [target1, target2, etc]
```

### Scan a List of Targets
```shell
nmap -iL [list.txt]
```

### Scan a Range of Hosts
```shell
nmap [range of IP addresses]
```

### Scan an Entire Subnet
```shell
nmap [ip address/cdir]
```

### Scan Random Hosts
```shell
nmap -iR [number]
```

### Exclude Targets From a Scan
```shell
nmap [targets] --exclude [targets]
```

### Exclude Targets Using a List
```shell
nmap [targets] --excludefile [list.txt]
```

### Perform an Aggresive Scan
```shell
nmap -A [target]
```

### Scan an IPv6 Target
```shell
nmap -6 [target]
```

## Port Scanning Options

### Perform a Fast Scan
```shell
nmap -F [target]
```

### Scan Specific Ports
```shell
nmap -p [port(s)] [target]
```

### Scan Ports by Name
```shell
nmap -p [port name(s)] [target]
```

### Scan Ports by Protocol
```shell
nmap -sU -sT -p U:[ports],T:[ports] [target]
```

### Scan All Ports
```shell
nmap -p 1-65535 [target]
```

### Scan Top Ports
```shell
nmap --top-ports [number] [target]
```

### Perform a Sequential Port Scan
```shell
nmap -r [target]
```

### Attempt to Guess an Unknown OS
```shell
nmap -O --osscan-guess [target]
```

### Service Version Detection
```shell
nmap -sV [target]
```

### Troubleshoot Version Scan
```shell
nmap -sV --version-trace [target]
```

### Perform a RPC Scan
```shell
nmap -sR [target]
```

## Discovery Options
**Host Discovery**
The `-p` switch determines the type of ping to perform.

| Nmap Switch | Description                 |
|:------------|:----------------------------|
| **-PI**     | ICMP ping                   |
| **-Po**     | No ping                     |
| **-PS**     | SYN ping                    |
| **-PT**     | TCP ping                    |

### Perform a Ping Only Scan
```shell
nmap -sn [target]
```

### Do Not Ping
```shell
nmap -Pn [target]
```

### TCP SYN Ping
```shell
nmap -PS [target]
```

### TCP ACK Ping
```shell
nmap -PA [target]
```

### UDP Ping
```shell
nmap -PU [target]
```

### SCTP INIT Ping
```shell
nmap -PY [target]
```

### ICMP Echo Ping
```shell
nmap -PE [target]
```
### ICMP Timestamp Ping
```shell
nmap -PP [target]
```

### ICMP Address Mask Ping
```shell
nmap -PM [target]
```

### IP Protocol Ping
```shell
nmap -PO [target]
```

### ARP ping
```shell
nmap -PR [target]
```

### Traceroute
```shell
nmap --traceroute [target]
```

### Force Reverse DNS Resolution
```shell
nmap -R [target]
```

### Disable Reverse DNS Resolution
```shell
nmap -n [target]
```

### Alternative DNS Lookup
```shell
nmap --system-dns [target]
```

### Manually Specify DNS Server
Can specify a single server or multiple.
```shell
nmap --dns-servers [servers] [target]
```

### Create a Host List
```shell
nmap -sL [targets]
```

## Port Specification and Scan Order

| Nmap Switch | Description                 |
|:------------|:----------------------------|

## Service/Version Detection

| Nmap Switch | Description                  |
|:------------|:-----------------------------|
| **-sV**     | Enumerates software versions |

## Script Scan

| Nmap Switch | Description             |
|:------------|:------------------------|
| **-sC**     | Run all default scripts |

## OS Detection

| Nmap Switch | Description                 |
|:------------|:----------------------------|

## Timing and Performance
The `-t` switch determines the speed and stealth performed.

| Nmap Switch | Description                 |
|:------------|:----------------------------|
| **-T0**     | Serial, slowest scan        |
| **-T1**     | Serial, slow scan           |
| **-T2**     | Serial, normal speed scan   |
| **-T3**     | Parallel, normal speed scan |
| **-T4**     | Parallel, fast scan         |

Not specifying a `T` value will default to `-T3`, or normal speed.

## Firewall Evasion Techniques

### Firewall/IDS Evasion and Spoofing
| Nmap Switch | Description                 |
|:------------|:----------------------------|

### Fragment Packets
```shell
nmap -f [target]
```

### Specify a Specific MTU
```shell
nmap --mtu [MTU] [target]
```

### Use a Decoy
```shell
nmap -D RND:[number] [target]
```

### Idle Zombie Scan
```shell
nmap -sI [zombie] [target]
```

### Manually Specify a Source Port
```shell
nmap --source-port [port] [target]
```

### Append Random Data
```shell
nmap --data-length [size] [target]
```

### Randomize Target Scan Order
```shell
nmap --randomize-hosts [target]
```

### Spoof MAC Address
```shell
nmap --spoof-mac [MAC|0|vendor] [target]
```

### Send Bad Checksums
```shell
nmap --badsum [target]
```
  
## Advanced Scanning Functions

### TCP SYN Scan
```shell
nmap -sS [target]
```

### TCP Connect Scan
```
nmap -sT [target]
```

### UDP Scan
```shell
nmap -sU [target]
```

### TCP NULL Scan
```shell
nmap -sN [target]
```

### TCP FIN Scan
```shell
nmap -sF [target]
```

### Xmas Scan
```shell
nmap -sA [target]
```

### TCP ACK Scan
```shell
nmap -sA [target]
```

### Custom TCP Scan
```shell
nmap --scanflags [flags] [target]
```

### IP Protocol Scan
```shell
nmap -sO [target]
```

### Send Raw Ethernet Packets
```shell
nmap --send-eth [target]
```

### Send IP Packets
```shell
nmap --send-ip [target]
```

## Timing Options

### Timing Templates
```shell
nmap -T[0-5] [target]
```

### Set the Packet TTL
```shell
nmap --ttl [time] [target]
```

### Minimum NUmber of Parallel Operations
```shell
nmap --min-parallelism [number] [target]
```

### Maximum Number of Parallel Operations
```shell
nmap --max-parallelism [number] [target]
```

### Minimum Host Group Size
```shell
nmap --min-hostgroup [number] [targets]
```

### Maximum Host Group Size
```shell
nmap --max-hostgroup [number] [targets]
```

### Maximum RTT Timeout
```shell
nmap --initial-rtt-timeout [time] [target]
```

### Initial RTT Timeout
```shell
nmap --max-rtt-timeout [TTL] [target]
```

### Maximum Number of Retries
```shell
nmap --max-retries [number] [target]
```

### Host Timeout
```shell
nmap --host-timeout [time] [target]
```

### Minimum Scan Delay
```shell
nmap --scan-delay [time] [target]
```

### Maxmimum Scan Delay
```shell
nmap --max-scan-delay [time] [target]
```

### Minimum Packet Rate
```shell
nmap --min-rate [number] [target]
```

### Maximum Packet Rate
```shell
nmap --max-rate [number] [target]
```

### Defeat Reset Rate Limits
```shell
nmap --defeat-rst-ratelimit [target]
```

## Output Options

| Nmap Switch | Description   |
|:------------|:--------------|
| ``-oN``     | Normal output |
| ``-oX``     | XML output    |
| ``-oA``     | Normal, XML, and Grepable format all at once |

### Save Output to a Text File
```shell
nmap -oN [scan.txt] [target]
```

### Save Output to a XML File
```shell
nmap -oX [scan.xml] [target]
```

### Grepable Output
```shell
nmap -oG [scan.txt] [target]
```

### Output All Supported File Types
```shell
nmap -oA [path/filename] [target]
```

### Periodically Display Statistics
```shell
nmap --stats-every [time] [target]
```

### 1337 Output
```shell
nmap -oS [scan.txt] [target]
```

## Compare Scans

### Comparison Using Ndiff
```shell
ndiff [scan1.xml] [scan2.xml]
```

### Ndiff Verbose Mode
```shell
ndiff -v [scan1.xml] [scan2.xml]
```

### XML Output Mode
```shell
ndiff --xml [scan1.xml] [scan2.xml]
```

## Troubleshooting and Debugging

### Get Help
```shell
nmap -h
```

### Display Nmap Version
```shell
nmap -V
```

### Verbose Output
```shell
nmap -v [target]
```

### Debugging
```shell
nmap -d [target]
```

### Display Port State Reason
```shell
nmap --reason [target]
```

### Only Display Open Ports
```shell
nmap --open [target]
```

### Trace Packets
```shell
nmap --packet-trace [target]
```

### Display Host Networking
```shell
nmap --iflist
```

### Specify a Network Interface
```shell
nmap -e [interface] [target]
```

## Nmap Scripting Engine

### Execute Individual Scripts
```shell
nmap --script [script.nse] [target]
```

### Execute Multiple Scripts
```shell
nmap --script [expression] [target]
```

### Execute Scripts by Category
```shell
nmap --script [category] [target]
```

### Execute Multiple Script Categories
```shell
nmap --script [category1,category2,etc]
```

### Troubleshoot Scripts
```shell
nmap --script [script] --script-trace [target]
```

### Update the Script Database
```shell
nmap --script-updatedb
```

