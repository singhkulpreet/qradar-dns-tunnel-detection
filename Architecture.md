Explain data flow:

Windows sends DNS queries to Kali (bind9). Bind9 logs queries to /var/log/named/named.log or via syslog.

rsyslog on Kali tails the bind9 log and forwards lines to QRadar over TCP 514.

QRadar DSM ingests events; custom DSM or parser for bind/named may be required (or use Generic Syslog).

QRadar rule stack detects suspicious patterns and dispatches events which then create offenses.