# My eJPT Journey
I am using this repository to document my learnings as I undertake preparation for the [eLearnSecurity Junior Penetration Tester (eJPT)](https://elearnsecurity.com/product/ejpt-certification/) certification. 

## Content
I am tracking my learning progress in the following two places:
- [Topics](/docs/topics/topics.md)
- [Labs](/docs/labs/labs.md)

The Topics area covers my notes from the course content.  It also contains additional notes from supplemental resources.  

The Labs area covers my experience and learnings as I work through each of the labs.

# About the eJPT
Training for the eJPT is provided by [INE](https://ine.com), of which [eLearnSecurity](https://elearnsecurity.com/) is a subsidiary. INE stands for InternetNetwork Expert.

![](/img/eJPT.png)

The eJPT certification is the first of three certifications I intend to achieve to expand my knowledge in pentesting and offensive security operations:

```mermaid
  flowchart TD
    A["<a href='https://elearnsecurity.com/product/ejpt-certification/'>eLearnSecurity Junior Penetration Testing (eJPT)</a>"] --> B
    B["<a href='https://elearnsecurity.com/product/ecpptv2-certification/'>eLearnSecurity Certified Professional Penetration Tester (eCPPT)</a>"] --> C
    C["<a href='https://www.reddit.com/r/Pentesting/comments/dq7rxn/oscp_vs_gpen_and_gxpen/?utm_source=share&utm_medium=ios_app&utm_name=iossmf'>Offensive Security Certified Professional (OSCP)</a>"]
```

I discovered this certification track from the good folks at Reddit from this thread [here](https://www.reddit.com/r/Pentesting/comments/dq7rxn/oscp_vs_gpen_and_gxpen/?utm_source=share&utm_medium=ios_app&utm_name=iossmf). 

Here is a helpful link to a map of numerous security certifications, showing where the eJPT falls into play: [Security Certification Roadmap](https://pauljerimy.com/security-certification-roadmap/). 

[![](/img/track.png)](https://pauljerimy.com/security-certification-roadmap/)

# eJPT Topics
INE offers training for the eJPT [here](https://ine.com/learning/certifications/internal/elearnsecurity-junior-penetration-tester). The training consists of four parts:
1. Penetration Testing Prerequisites
2. Penetration Testing: Preliminary Skills and Programming
3. Penetration Testing Basics
4. eJPT Exam Preparation

Each module comprises a mixture of study guides and labs. The study guides are intended to bring you up to speed on the basic concepts and may have no relevance to the labs. The labs force you to explore concepts on your own -- to pull you out of the structured learning mindset -- and are intended to be very challenging. I've easily sunk a week in a lab but found it to be extremely invigorating and rewarding!

Here's a list of topics covered. Most of the topics are introductory in nature, but it's up to you to explore to get the most out things:
- Networking - IP, TCP/UDP, Firewalls, DNS, Wireshark
- Web Applications - HTTP, cookies, sessions, Burp Suite
- Penetration Testing - overview and lifecycle
- Programming - low- and high-level languages, programming vs scripting, C++ intro, Python intro, Bash, Windows command line
- Information Gathering - open-source intelligence, enumeration
- Footprinting & Scanning - NMAP, Masscan
- Vulnerability Assessment - Nessus
- Web Attacks - Netcat, Dirbuster, cross-site scripting, SQL injection
- System Attacks - Malware, backdoor, password attacks, John the Ripper, Hashcat
- Network Attacks - authentication cracking, Hydra, bruteforce and password cracking, null sessions, ARP poisoning, ARP spoofing, Metasploit, remote code execution
