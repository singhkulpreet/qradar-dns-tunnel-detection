Rule 1 — Possible DNS Tunneling — High Query Volume / Unique Labels

Description: Trigger if the BB BB:KUL:DNS Tunneling hunting matches >= 20 times from the same Source IP within 1 minute.

Rule Actions:

Dispatch new event

Event Name: DNS Tunneling expected

Description: High volume of DNS queries from a single IP in short time.

Severity: 5, Credibility: 10, Relevance: 10

High-Level Category: Risk

Low-Level Category: Data Loss Possible

Annotate offense with T1071.004 – Application Layer Protocol: DNS (MITRE)

Force dispatched event to create new offense.

Notes: In screenshot the BB is applied to Local system. Building block itself contains the logic to classify suspicious DNS events (see BB content below).


Rule 2 — DNS Tunneling — Long subdomain labels

Description: Trigger on events where qid=48250031 and subdomain lengths indicate unusually long labels.

AQL filter in the test: qid=48250031 AND dnsClientIP != "" AND subdomain != "" (adjust to your fields). Exclude payloads that look like short base64 fragments by applying negative regex NOT payload matches /\s+[A-Za-z0-9+/=]{0,5}\./.

Trigger: 10 events from same Source IP in 1 minute.

Rule Actions:

Dispatch New Event

Event Name: Subdomains are longer

Event Description: This is an indication of data exfiltration and DNS Tunneling

Severity: 5, Credibility: 10, Relevance: 10

High-Level Category: Access

Low-Level Category: Access Denied

Force dispatched event to create a NEW offense.