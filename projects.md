---
title: Projects
---

# Projects

Each write-up is what I did and how the three principles showed up. No client names. No hashes.

## 1. Incident response playbook

**Role.** I wrote the playbook and ran a dry run. My supervisor reviewed it. The goal is a process other techs can follow when something bad shows up.

**Skills.** Evidence handling, ticket flow, PowerShell, talking to the customer and the team, writing steps people can use under stress.

**Challenge.** We did not have a repeatable way to gather evidence. Time pressure makes people skip steps. That is the preparation phase in NIST incident response.

**Outcome.** Draft complete and tested. Waiting on final supervisor notes before we put it in front of the whole team.

**Faith.** Consecrated skill and house on the rock (Luke 6). A playbook is not a trophy. It is a foundation so the next person does not have to invent care in the moment.

## 2. Sanitized incident response case

**Role.** I led the investigation and wrote the full package: investigation report, executive summary, forensic analysis, and after-action.

**Skills.** Triage, malware analysis at a high level, checking for possible data exposure, timelines, communication with my supervisor and the client.

**Challenge.** A fake backup tool was a remote-access agent with a keylogger and command-and-control traffic. Clinical information may have been in the log. I had to stay with facts, ask for help, and not put patient or client detail in any school file.

**Outcome.** Contained, imaged, wiped, rebuilt. Passwords treated as compromised. For this site I only keep a redacted story. The real report stays at work.

**Faith.** Truth over verdict and power under covenant. Isolate early instead of watching for a prettier picture. Minimum necessary on the keylog. The choice, not the hashes.

## 3. Python command-and-control lab (class)

**Role.** Programming course lab. I built a crude server and payload in an isolated lab so I could see how remote control looks from the other side.

**Skills.** Python, basic networking, reading attacker patterns so I can recognize them at work.

**Challenge.** I had never written anything like it. My programming was basic. I had to stay inside a lab and not treat it like a toy to use on a real person.

**Outcome.** It worked in the lab: virtual machine as the server, host as the test victim, remote control over the channel we set up. That is the only place it ran.

**Faith.** Power under covenant. I needed to understand the tool. I do not get to use it because I can. Closed lab. No production. No “just to see.”

## Also in progress

**Proxmox home lab.** After-hours practice so I do not learn only on a customer’s machine. Still being built. Same rule: test off production.
