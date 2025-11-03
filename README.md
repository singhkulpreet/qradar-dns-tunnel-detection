# DNS Tunneling SOC Project

Project summary



You created a DNS tunneling lab where:



QRadar is installed on a VM (e.g. 192.168.X.100) and receives DNS logs.



Windows host (victim) is 192.168.X.1 and is compromised (acts as the ‘client’ generating suspicious DNS queries).



Kali VM 192.168.X.200 runs bind9 (named) and acts as the DNS server/attacker.



This repo documents how logs flow to QRadar, the detection rules you created, the test-playbook, and forensic/validation steps.



Goals



Detect high query volume DNS tunneling (many queries from a single source in short time).



Detect long subdomain labels typical of DNS-based exfiltration.



Generate offenses in QRadar and provide an analyst playbook to investigate and respond.

