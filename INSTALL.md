**Prerequisites**



* Hypervisor (VMware/VirtualBox) with three VMs: QRadar VM, Kali VM, Windows VM.



* QRadar installed and reachable from the network. Admin access to QRadar UI.



* Kali with bind9, rsyslog installed.





**High-level steps**



* Configure bind9 on Kali (see KALI/bind9\_config/named.conf.options example in this repo). Enable query logging to local syslog or a file.



* Configure rsyslog on Kali to forward bind9 logs (or the log file) to QRadar over UDP/TCP 514. Example snippet in KALI/rsyslog.named.conf.



* On QRadar, ensure a protocol for syslog (Log Source) is created and receiving events from Kali.



* Import or create the detection rules (see QRADAR/RULES.md).



* Test by generating DNS queries from the Windows VM towards the Kali Bind server.
