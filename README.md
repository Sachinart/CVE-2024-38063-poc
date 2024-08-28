Real POC published https://github.com/ynwarcs/CVE-2024-38063 and I have updated in my code as well, This can cause crash into your system so use VM or just learning thing, you can get RCE by making changes in the code.

#### Usage

```iface``` <- If you have multiple adapters, you need to choose which one to use to send packets. e.g. "eth0" on linux or "Hyper-V Virtual Ethernet Adapter" on windows. If you're going to use your default interface, leave it empty.

```ip_addr``` <- IP address of the target system (IPv6)

```num_tries & num_batches``` <- How many different packet batches to send. more of them = more heap corruptions caused + higher chance of triggering the vulnerability.

```mac_addr``` <- Leave empty, unless scapy complains it can't find the mac address. See below in troubleshooting.

Enable it => Most probably this is enabled bydefault. 

![Screenshot_1](https://github.com/user-attachments/assets/01d8da94-6dbc-49eb-86b0-6c52d97f5073)

<mark>Check the ```CVE-2024-38063-poc.py``` for more.<mark>

Finder https://x.com/XiaoWei___
Code/POC credit => @ynwarcs
Thank You!
- Chirag Artani
