---
title: Ethical Dilemma
---

# Isolate or keep watching

![A nineteenth-century balance scale](images/balance.jpg)

*A balance scale, about 1850. The dilemma was which side weighs more: more telemetry, or the people on the machine. Wikimedia Commons.*

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
Leaving the host up for a cleaner C2 picture would have served my report more than the user. Possible clinical data in a keylog raises a duty to limit harm. My supervisor made the right call. This follows with my spiritual principle of "Power under covenant" which means "just because I can watch longer does not mean I should.

Reading the keylog was necessary and also a privacy boundary line. I cannot assess impact if I refuse to look but I also cannot treat the file like entertainment. Minimum necessary inspection to determine private data, then stop. 
This matches our role as stewards (D&C 104) and my mission statement to protect agency and reduce harm. 
I refused three assumptions. First, that the user was foolish or lying. Second, that DNS blocking the domain later meant nothing left. Finally, that I get to read everything because I am the tech.

What I learned: the person on that PC, and whoever’s information was in the log, pays if we wait for a prettier picture of the attacker. Although evidence matters. people matter more. 


## Alternative approach

The essential principles here are honesty, responsibility to protect people, and privacy.

If I ran this again, I would isolate as soon as I saw an attempted connection to an unknown foreign address. I would not wait for my supervisor to make that call. Protecting the client and their data comes before reverse-engineering the malware.

This was my first time seeing something like this and felt curiosity and panic when the indicators were discovered. That experience made me faster at naming the priority, which is “contain first, then analyze.” I used to treat the NIST incident-response steps as a straight line. They are not. The steps cycle. Analysis can happen before and after containment.

This approach is better for everyone because seconds matter. It can be the difference between private data staying put and hundreds of people’s information getting leaked. It also shows the organization will not use a customer’s machine as a sandbox which builds trust. It is better to accept the cost of losing some live telemetry so we can protect the client and their customers. That is the highest priority.

After this case I knew a playbook had to be created. It is how those technical steps and these principles are passed to the team, so we are better, faster, and more consistent under stress, and so we serve the client instead of our own curiosity.


## What this taught me about the field (Week 5)

Incident response should follow two rules:
1. Learn enough to stop the attacker.
2. Do not violate the victim’s privacy to do it.

Privacy in IT is the same risk on a quieter day. As technicians, we hold mail, files, logs, and access to admin controls because the job requires it. That access is not ownership.

There are case studies that show the cost. Health plans and clinics keep showing up in breach notices. DentaQuest was one of the large health-data incidents in 2026. Education was hit when attackers went after Canvas, a system that already holds a huge number of students (TechCrunch, 2026). Those stories are not only “hackers are busy.” They are what happens when access is wide, vendors sit in the middle, and nobody treats other people’s records as sacred. The machine I worked was a smaller version of the same problem.

The experience made that lesson concrete. A live device and a keylog are just the loud version of permissions, admin accounts, ticket notes, and AI tools that can summarize a mailbox. The ethical problem is rarely “should I commit a crime?” It is more like “do I need to keep looking because I can, because I am curious, or because it will make me look thorough?”

How I will handle the next incident:
- Contain when the risk to people outweighs the value of more telemetry.
- Collect only what the incident and the customer’s request require.
- Tell the customer what I am doing.
- Do not use one client’s indicator of compromise as a free pass into other client tenants.
- Do not put private data in a public sandbox for testing purposes.
- Ask when I do not know. Time pressure is not permission.

As I continue to gain experience and skill in the field, the real work is deciding what we refuse to take advantage of.


## References

National Institute of Standards and Technology. (2012). *Computer security incident handling guide* (SP 800-61 Rev. 2). https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final

TechCrunch. (2026, September 15). Leaks, data breaches, and ransom notes: The worst hacks of 2026 so far. https://techcrunch.com/2026/09/15/the-worst-hacks-and-breaches-of-2026-so-far/

