---
layout: page
title: "Troubleshooting installation problems"
description: "Common installation problems and their solutions."
date: 2015-01-20 22:36
sidebar: false
comments: false
sharing: true
footer: true
---

It can happen that you run into trouble while installing Home Assistant. This page is here to help
you figure out the most common problems.

**pip3: command not found**<br>
This utility should have been installed as part of the Python 3.4 installation. Check if Python 3.4
is installed by running `python3 --version`. If it is not installed,
[download it here](https://www.python.org/getit/).

If you are able to successfully run `python3 --version` but not `pip3`, run the following command instead
to install Home Assistant: `python3 -m pip install homeassistant`.

**No module named pip**<br>
[Pip](https://pip.pypa.io/en/stable/) should come bundled with the latest Python 3 but is ommitted
by some distributions. If you are unable to run `python3 -m pip --version` you can install `pip` by
[downloading the installer](https://bootstrap.pypa.io/get-pip.py) and run it with Python 3:
`python3 get-pip.py`.

**CentOS and Python 3**<br>
To run Python 3.x on [CentOS](https://www.centos.org/) or RHEL, [Software Collections](https://www.softwarecollections.org/en/scls/rhscl/rh-python34/) needs to be activated.</p>

**Run the development version**<br>
If you want to stay on top of the development of Home Assistant then you can upgrade to the latest stuff what is available in the dev branch `pip3 install --upgrade git+git://github.com/balloob/home-assistant.git@dev`. Keep in mind, that stable releases of Home Assistant are published often.

**No access to the frontend**<br>
In newer Linux distributions (at least Fedora 22/CentOS 7) the access to a host is very limited.
This means that you can't access the Home Assistant Frontend that is running on a host outside of the host machine. Windows and OSX machines may also have issues with this.

To fix this you will need to open your machine's firewall for TCP traffic over port 8123. The method for doing this will vary depending on your operating system and the firewall you have installed. Below are some suggestions to try. Google is your friend here.

[Windows](http://windows.microsoft.com/en-us/windows/open-port-windows-firewall#1TC=windows-7) and [Mac OSX](https://support.apple.com/en-us/HT201642) have good instructions posted.

For firewalld systems (Fedora, RHEL, etc.):
```bash
sudo firewall-cmd --permanent --add-port=8123/tcp
sudo firewall-cmd --reload
```

For UFW systems (Ubuntu, Debian, Raspbian, etc.):
```bash
sudo ufw allow 8123/tcp
```

For iptables systems (usually the default):
```bash
iptables -I INPUT -p tcp --dport 8123 -j ACCEPT
iptables-save > /etc/network/iptables.rules  # your rules may be saved elsewhere
```
###[&laquo; Back to Getting Started](/getting-started/index.html)
