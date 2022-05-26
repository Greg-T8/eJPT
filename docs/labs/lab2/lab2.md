# Lab 2: Data Exfiltration

In this lab, we use data exfiltration techniques to capture data in a restricted environment.

## Lab Environment
You have exploited a vulnerable API endpoint and overwritten it with malicious code. This modification allows you to run commands on the server machine hosting the API, as a low-privileged user, i.e. student. A sensitive flag file is kept in a zipped archive file in the student's home directory.

Also, there is a monitor process running on the server machine that blocks most protocols except HTTP.

**Objective:** Transfer the zipped archive to your Kali machine using HTTP protocol and retrieve the flag!

**Instructions:**  
- The API endpoint is accessible at **demo.ine.local** domain

![](img/laboverview.png)

**Tools:**
- Nmap
- Web browser
- Python scripting
- curl

## Exploration

Run Nmap to determine open connect. The `-A` switch turns on *Advanced* and *Aggressive* features such as OS detection and service detection. Note that port 8000/tcp is open.

![](img/nmapresults.png)

Viewing this service through a browser, I get a message indicating **cmd parameter required**.

![](img/browserresult.png)

Same result using the `curl` command:

![](img/curl1.png)

At this point, I had no idea how to use the `cmd` parameter with the URL, so I had to glance back at the solution. Turns out the `cmd` parameter means I can pass the parameter name `cmd` with the URL. This is a very common style used with web shells.

When I pass the `cmd` parameter with the `ls` command, I can see the payload file **flag.zip**.

![](img/curl2.png)

My next task is to figure out how I can pass arguements to the `ls` command. Knowing that **%20** is the equivalent of a space in a URL, I was able to use additional arguments with `ls`:

![](img/curl3.png)

After peaking back at the solution, I discovered you can also use **+** in place of **%20**:

![](img/curl4.png)

### Investigating the **tools** directory
The tools directory contains an interesting Python tool, called exfil, that can be used to pass data using covert channels, including ICMP and DNS Lookup.

![](img/ls-exfil.png)

I see that this tool is associated with a Git repository, so I used the **cat** command to view the contents of the Git config file:

![](img/gitconfig.png)

Documentation for the exfil tool is available here: https://github.com/averagesecurityguy/exfil
