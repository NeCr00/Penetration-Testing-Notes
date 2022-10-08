There is a myriad of tools and services available in cybersecurity for vulnerability scanning. Ranging from being commercial (and footing a heavy bill) to open-source and free, vulnerability scanners are convenient means of quickly canvassing an application for flaws.

  

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/a875f0744fa4e296c34693eec4fe623d.png)  

  

For example, the vulnerability scanner [Nessus](https://www.tenable.com/products/nessus) has both a free (community) edition and commercial. The commercial version costing thousands of pounds for a year's license will likely be used in organisations providing penetration testing services or audits. If you’d like to know more about Nessus, check out the TryHackMe [room](https://tryhackme.com/room/rpnessusredux) dedicated to it.

  

I have detailed some of the advantages and disadvantages of using a vulnerability scanner in the table below:

  

**Advantage**

**Disadvantage**

Automated scans are easy to repeat, and the results can be shared within a team with ease.

People can often become reliant on these tools.

These scanners are quick and can test numerous applications efficiently.

They are extremely "loud" and produce a lot of traffic and logging. This is not good if you are trying to bypass firewalls and the likes.

Open-source solutions exist.

Open-source solutions are often basic and require expensive licenses to have useful features.

Automated scanners cover a wide range of different vulnerabilities that may be hard to manually search for.

They often do not find every vulnerability on an application.

  

Frameworks such as Metasploit often have vulnerability scanners for some modules; this is something you will come onto learn about in a further module in this pathway.

  

Manual scanning for vulnerabilities is often the weapon of choice by a penetration tester when testing individual applications or programs. In fact, manual scanning will involve searching for the same vulnerabilities and uses similar techniques as automated scanning.

  

Ultimately, both techniques involve testing an application or program for vulnerabilities. These vulnerabilities include:

  

**Vulnerability**

**Description**

Security Misconfigurations

Security misconfigurations involve vulnerabilities that are due to developer oversight. For example, exposing server information in messages between the application and an attacker.

Broken Access Control

This vulnerability occurs when an attacker is able to access parts of an application that they are not supposed to be able to otherwise.

Insecure Deserialization

This is the insecure processing of data that is sent across an application. An attacker may be able to pass malicious code to the application, where it will then be executed.

Injection

An Injection vulnerability exists when an attacker is able to input malicious data into an application. This is due to the failure of not ensuring (known as sanitising) input is not harmful.

If you are keen to learn more about these vulnerabilities, the [OWASP framework](https://owasp.org/www-project-top-ten/) will be a useful read to you. TryHackMe even has a [room](https://tryhackme.com/room/owasptop10) showcasing the top ten vulnerabilities outlined by OWASP.

**Rapid7**

Much like other services such as Exploit DB and NVE, Rapid7 is a vulnerability research database. The only difference being that this database also acts as an exploit database. Using this service, you can filter by type of vulnerability (I.e. application and operating system).

  

![](https://assets.tryhackme.com/additional/vulnerability-module/exploiting-a-vulnerability/rapid1.png)  

  

Additionally, the database contains instructions for exploiting applications using the popular Metasploit tool (you will learn about this tool in-depth later in the learning path). For example, this entry on [Rapid7](https://www.rapid7.com/db/) is for “[Wordpress Plugin SP Project & Document](https://www.rapid7.com/db/modules/exploit/multi/http/wp_plugin_sp_project_document_rce/)”, where we can see instructions on how to use an exploit module to abuse this vulnerability.

  

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/13341f677de4db82759d413908781218.png)  

**GitHub**

[GitHub](https://github.com/) is a popular web service designed for software developers. The site is used to host and share the source code of applications to allow a collaborative effort. However, security researchers have taken to this platform because of the aforementioned reasons as well. Security researchers store & share PoC’s (Proof of Concept) on GitHub, turning it into an exploit database in this context.

  

GitHub is extremely useful in finding rare or fresh exploits because anyone can create an account and upload – there is no formal verification process like there is with alternative exploit databases. With that said, there is also a downside in that PoC’s may not work where little to no support will be provided.

  

  
![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/cc2a8c7caa8841aa1c45d10ccc4de385.png)

  

GitHub uses a tagging and keyword system, meaning that we can search GitHub by keywords such as “PoC”, “vulnerability”, and many more. At the time of writing, there are 9,682 repositories with the keyword “cve”. We are also able to filter the results by programming language.

  

**Searchsploit**

Searchsploit is a tool that is available on popular pentesting distributions such as Kali Linux. It is also available on the TryHackMe AttackBox. This tool is an offline copy of Exploit-DB, containing copies of exploits on your system. 

  

You are able to search searchsploit by application name and/or vulnerability type. For example, in the snippet below, we are searching searchsploit for exploits relating to Wordpress that we can use – no downloading necessary!

  

  

Using Searchsploit to look for exploits relating to "Wordpress"

```shell-session
searchsploit wordpress
WordPress Theme Think Responsive 1.0 - Arbitr | php/webapps/29332.txt
WordPress Theme This Way - 'upload_settings_i | php/webapps/38820.php
WordPress Theme Toolbox - 'mls' SQL Injection | php/webapps/38077.txt
WordPress Theme Trending 0.1 - 'cpage' Cross- | php/webapps/36195.txt
WordPress Theme Uncode 1.3.1 - Arbitrary File | php/webapps/39895.php
WordPress Theme Urban City - 'download.php' A | php/webapps/39296.txt
WordPress Theme Web Minimalist 1.1 - 'index.p | php/webapps/36184.txt
WordPress Theme White-Label Framework 2.0.6 - | php/webapps/38105.txt
WordPress Theme Wp-ImageZoom - 'id' SQL Injec | php/webapps/38063.txt
WordPress Theme Zoner Real Estate - 4.1.1 Per | php/webapps/47436.txt
```

Throughout your journey in cybersecurity, you will often come across a magnitude of different applications and services. For example, a CMS whilst they all have the same purpose, often have very different designs and behaviours (and, in turn, potentially different vulnerabilities).

Thankfully for us, there are resources on the internet that keep track of vulnerabilities for all sorts of software, operating systems and more! This room will showcase two databases that we can use to look up existing vulnerabilities for applications discovered in our infosec journey, specifically the following websites: 

1. [NVD (National Vulnerability Database)](https://nvd.nist.gov/vuln/full-listing)

2. [Exploit-DB](http://exploit-db.com/)

Before we dive into these two resources, let's ensure that our understanding of some fundamental key terms is on the same page:

**Term**

**Definition**

Vulnerability

A vulnerability is defined as a weakness or flaw in the design, implementation or behaviours of a system or application.  

Exploit

An exploit is something such as an action or behaviour that utilises a vulnerability on a system or application.

Proof of Concept (PoC)

A PoC is a technique or tool that often demonstrates the exploitation of a vulnerability.

  

## NVD – National Vulnerability Database

The National Vulnerability Database is a website that lists all publically categorised vulnerabilities. In cybersecurity, vulnerabilities are classified under “**C**ommon **V**ulnerabilities and **E**xposures” (Or CVE for short).

These CVEs have the formatting of `CVE-YEAR-IDNUMBER`. For example, the vulnerability that the famous malware WannaCry used was `CVE-2017-0144.`

NVD allows you to see all the CVEs that have been confirmed, using filters by category and month of submission. For example, it is three days into August; there have already been 223 new CVEs submitted to this database.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/aa86c1cce478d6c357f5507d927c9e88.png)

While this website helps keep track of new vulnerabilities, it is not great when searching for vulnerabilities for a specific application or scenario.

## Exploit-DB

[Exploit-DB](https://www.exploit-db.com/) is a resource that we, as hackers, will find much more helpful during an assessment. Exploit-DB retains exploits for software and applications stored under the name, author and version of the software or application.

We can use Exploit-DB to look for snippets of code (known as Proof of Concepts) that are used to exploit a specific vulnerability.

![](https://assets.tryhackme.com/additional/vulnerability-module/vulnerabilities101/exploitdb1.png)