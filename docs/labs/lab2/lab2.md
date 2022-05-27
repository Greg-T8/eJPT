# Lab 2: Data Exfiltration

In this lab, you use data exfiltration techniques to capture data in a restricted environment.

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

Run Nmap to determine open connections. The `-A` switch turns on *Advanced* and *Aggressive* features such as OS detection and service detection. Note that port 8000/tcp is open.

![](img/nmapresults.png)

Viewing this service through a browser, you get a message indicating **cmd parameter required**.

![](img/browserresult.png)

You get the same result using the `curl` command:

![](img/curl1.png)

At this point, I had to glance back at the solution, as I had no idea how to pass the **cmd** parameter. As it turns out, you can pass **cmd** parameter with the URL in the form of `http://url/?cmd=`. This is a very common style used with web shells. When you pass the `cmd` parameter by using the `ls` command, you see the payload **flag.zip**.

![](img/curl2.png)

The next task is to figure out how I to pass arguments to the `ls` command. Knowing that **%20** is the equivalent of a space in a URL, you can use additional arguments with `ls`:

![](img/curl3.png)

After peaking back at the solution, I discovered you can use **+** in place of **%20**:

![](img/curl4.png)

## Investigating the **tools** Folder
The tools folder contains an interesting Python script, called **exfil.py**. 

![](img/ls-exfil.png)

By noting the presence of the **.git** folder, you determine this tool is associated with a Git repository. You can use the **cat** command to view the contents of the Git config file:

![](img/gitconfig.png)

Documentation for **exfil.py** is available here: https://github.com/averagesecurityguy/exfil

By viewing the README file, you learn that **exfil.py** can be used to pass data via covert channels, such as ICMP and DNS Lookup. This tool relies on creating a client-server connection and includes a number of dependent modules and packages:

- Dependent Packages
  - dnslib
  - dpkt

- Dependent Modules
  - dns_lookup
  - ping_data

In turn, each of these modules and packages have a number of dependencies, most of which are not available on the host.

You can use a combination of the **cat** command and the redirection operator to copy the modules to the host, but you'll eventually run into a permissions error when trying to copy the **dpkt.py** module, as it is located in a folder, `/usr/local/lib/python2.7` for which the remote shell does not have access. And given the host machine does not have an Internet connection to install the package, this route ended up becoming a dead in, for my case.

However, I feel this tool is valuable, so I'm documenting it here for future use.
