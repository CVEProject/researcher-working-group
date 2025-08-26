# CVEDibs

## Overview

This repository is an experimental channel to coordinate CVE ID assignments for Publicly Disclosed vulnerabilities, per the
as-yet-to-be-designed CVE Distributed Interrogative Basic System (CVE-DIBS) protocol. But also see below where we draft the CVE-DIBS protocol!

The CVE Researcher Working Group ([RWG](https://cve-cwe-programs.groups.io/g/RWG)) is working to improve how CVE IDs are assigned quickly and accurately for Publicly Disclosed vulnerabilities, especially "hot" topics (e.g., recent, exploited in the wild, lacking remediation).  The RWG has some [working notes](https://docs.google.com/document/d/18ApPD0s7o55jE8Lj-YjC5QywroMUFtf1d7Trr9IVtTE).

## CVE-DIBS Protocol (TLDR)

Placeholder for the concise version. See below for important details.

0. Required conditions: Vulnerability is Publicly Disclosed and hot.

1. CNA1 makes a Dibs-Request by opening an issue.

2. Within N hours, if nobody responds with a collision (competing claim), CNA1 is clear to proceed.

3. If someone (CNA2) does respond with a collision within N hours, work it out quickly, priority goes to earliest claim of substantial involvement (ongoing CVD, analysis work, scope, etc.).

4. If no agreement, go to Root/CNA-LR.

## CVE-DIBS Protocol (TL)

The detailed version. This is largely copied mostly from the Google notes document, it's probably too detailed, make a shorter version starting with the core dibs activity. Also very much still a work in progress.

0.0 A [Vulnerability](https://www.cve.org/ResourcesSupport/Glossary#glossaryVulnerability) is [Publicly Disclosed](https://www.cve.org/ResourcesSupport/Glossary#glossaryPubliclyDisclosed).

1.0 Someone, call them the Requester (R), observes the Publicly Disclosed Vulnerability lacking a CVE ID. R may be just somebody on the internet (goto 2.0) or R may be a CNA (goto 3.0).

2.0 If R is not a CNA then:

2.1 R makes an assignment request of a CNA with appropriate scope (CNA1).

2.2 CNA1 may be the Supplier of the affected Product.  The Supplier is almost always the CNA with the most appropriate scope and the Supplier CNA has the right of first refusal (4.2.1 link to the rules).

2.3 CNA1 may be a CNA-LR. If the Supplier is a CNA, the CNA-LR will talk to the Supplier CNA (first refusal, cite rule).

2.4 CNA1 may be another type of CNA with appropriate scope, for example, a coordinator or researcher CNA, or a CNA that solicits vulnerability reports? This type of CNA must also notify the Supplier CNA if it exists.

2.5 Whatever type CNA1 is, they follow the rules (MUST contact Supplier CNA if it exists, vulnerability determimation, assignment rules). R and CNA1 work it out and CNA1 assigns (or doesn't).

2.6 Dispute Policy may apply here if R and CNA1 do not agree or R does not accept the decision of CNA1.

3.0 If R is a CNA then:

3.1 (Effectively, R may be CNA1 as described in 2.1, that is, CNA1 receives an assignment request for a Publicly Disclosed Vulnerability from some other R' or CNA1 is R who observed the Publicly Disclosed Vulnerability.)

3.2 R (who is CNA1) investigates the requested assignment, analyzes evidence, determines vulnerability (4.1 rules), evaluates assignment rules (4.2 rules), and evaluates their scope.

3.2.1 (Note that lessons learned from this experiment may result in changes to the assignment rules (4.2 rules), but for the time being, this protocol follows the current rules.)

4.0 R (who is CNA1) decides to assign.

4.1 (Everything up to this point is basically background or preliminary. CVE-DIBS really starts here, when a CNA wants to assign for a Publicly Disclosed Vulnerability.)

5.0 R sends a Dibs-Request message to the channel, which means creating a new issue in this repo. The title of the issue starts with "Dibs-Request: " followed by a concise phrase that MUST identify the affected Product (and MAY include other words).

5.1 What else about the Dibs-Request message? MUST identify the requesting CNA (using CNA short name)? MUST include public reference.

5.2 The nature of the Dibs-Request is that R as done the homework, wants and is ready to assign *unless* another CNA (possibly a CNA-LR) has a prior or competing claim. By default and without a colliding response within the timeout period, R will be clear to assign.

5.2 Channel participants have N hours to respond.

5.2.1 Dibs-Request messages are ordered by time, when an issue was created or a comment added, according to GitHub.

5.3 We probably want to distinguish between two classes of Publicly Disclosed vulnerabilities, hot or not.

5.3.1 Hot. New, recent, fresh, getting public attention (socials, media), possibly EITW, possibly lacking a clear and authoritative fix, FUD, thrashing, not-working fixes... High pressure and high value in assigning a CVE ID quickly. Examples: CrushFTP.

5.3.2 Not. Old, stale, not recent, not getting attention, not EITW, low value in getting a CVE ID quickly, but value in getting an ID at all. For this class, the Dibs Protocol may not be necessary, as the requesting CNA can talk to the CNA-LR through regular, non-urgent channels (e.g., cveform.mitre.org for the MITRE CNA-LR). Example: OpenBSD Errata. Or maybe we use CVE-DIBS with a longer timeout, 72 hours? Three "business" days? One week?

5.4 If a participant responds in agreement, great, that's nice, optional, but can help R learn that other participants are not making conflicting claims. A Dibs-Agree message is reassuring, informational, and optional.

5.5 If a participant (CNA2, or more, CNA3...) responds in conflict (let's call this a collision, so, a Dibs-Collision message), the participants should try to work it out, quickly (maybe another time limit). If they can't, escalate to Root / CNA-LR. If CNAs have differen Roots, then what?

5.5.1 A CNA-LR MAY delegate assignment to R or another appropriate CNA participating in the Dibs-Request.

5.5.2 If a CNA-LR already has a pending request, the CNA-LR SHOULD assign, quickly (see 5.6.2 and 5.6.3)

5.5.2 (Escalating to Roots/CNA-LRs is not fast, which is counter to the need for and value in a quick assignment).

5.5.3 CNA2 responds with a Dibs-Collision message to R (R is also CNA1). This is a comment on the Dibs-Request issue. The colliding CNAs should consider factors including: which CNA started working on the assignment earlier, has more appropriate scope, has better information, was involved in CVD, really really cares more. See 5.5.2, a CNA-LR with a pending request has priority.

5.5.4 Remember the goal is quick assignment. We want some level of quality and to avoid duplicates and thrashing, but nobody gets a prize for winning Dibs. We all get a prize for a decent quality CVE going out quickly. Prizes for everyone playing Dibs.

5.6 If the timer expires without a Dibs-Collision message, R has Dibs and is clear to assign and publish.

5.6.1 R informs the channel of the assignment. At this point, no other CNAs may assign without additionally discussing with R and with R's agreement. This is another message type (Dibs-Confirm?). A comment on the Dibs-Request issue. Close the issue? Tags and resolutions would probably help.

5.6.2 R MUST act fast. No sandbagging. If some timeout (2 hours?) is reached, Dibs reopens? Or Root / CNA-LR takes over?

5.6.3 After assignment and publication, the usual rules and policies apply. An assignment or Record content can be disputed or rejected, ownership can be transferred.

6.0 R can send a PLA (Public Lacking Assignment) message to the channel. Dibs-Observed? In this case, the CNA is not claiming Dibs but alerting the channel, presumably with the idea that another CNA might want Dibs. In this case, maybe just go to a Root/CNA-LR?
