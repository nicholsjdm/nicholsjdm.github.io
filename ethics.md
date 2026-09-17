---
title: Ethical Dilemma
---

# Isolate or keep watching

## The situation

In August 2026 at my MSP job, a workstation had software that looked like a backup tool. It was a remote-access agent with a keylogger talking to a command-and-control server. It started with a phishing email that looked like DocuSign.

The dilemma was two decisions.

First, isolate or keep watching. If we left the box online we might see more of the domain and who it talked to. That could help identify the attacker. It would also give malware more time on a machine that already had a keylogger and possible clinical information in the log. 
I had started live analysis before I understood how bad it was. We found scheduled tasks and hard-coded IPs. My supervisor called isolate through the EDR agent early. I was not sure how it would play out. I knew there was risk either way.

Second, the keylog. To know if data was exposed I had to look. There were credentials and clinical workflow text. I needed enough to say this is sensitive and it may have left. I did not need to read someone’s workday. That data is not mine.

Who was involved: me on analysis and evidence, my supervisor on the isolate call, coworkers on containment and threat research, the client, and the person who used that computer. No names here.

## Initial response

A Secure DNS alert blocked a site from an unfamiliar program. I called the customer, asked questions, and looked at the host while it was live. I found hidden files and scheduled tasks, disabled persistence, and the host was isolated. 
I collected live evidence, then we recovered the machine and made an analysis image and a preservation image. I built a timeline, hunted for lateral movement, and found the first click in email. The sending business confirmed their mailbox had been compromised. 
The drive was wiped and the workstation rebuilt. Passwords on that machine were treated as burned. People who needed to know were told about possible exposure. There is no proof the log uploaded. We cannot assume it did not.

## Analysis

The isolate call followed professional incident-response practice. NIST-style response is prepare, detect, contain, eradicate, recover, and document. Containment exists because curiosity is not a control. 
Leaving the host up for a cleaner C2 picture would have served my report more than the user. Possible clinical data in a keylog raises a duty to limit harm. My supervisor made the right call. Principle 3: just because I can watch longer does not mean I should.

Reading the keylog was necessary and also a privacy line. I cannot assess impact if I refuse to look. I also cannot treat the file like entertainment. Minimum necessary, then stop. That matches stewardship (D&C 104) and protect agency and reduce harm. 
I refused three assumptions: that the user was foolish or lying, that DNS blocking the domain later meant nothing left, and that I get to read everything because I am the tech.

What I learned: the person on that PC, and whoever’s information was in the log, pays if we wait for a prettier picture of the attacker. Evidence still matters. People matter more. Not the hashes. The choice.

## References

National Institute of Standards and Technology. (2012). *Computer security incident handling guide* (SP 800-61 Rev. 2). https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final
