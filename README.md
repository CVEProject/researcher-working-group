# CVEDibs

## Overview

This repository is an experimental channel to coordinate CVE ID assignments for Publicly Disclosed vulnerabilities, per the
as-yet-to-be-designed CVE Distributed Interrogative Basic System (CVE-DIBS) protocol. But also see below where we draft the CVE-DIBS protocol!

The CVE Researcher Working Group ([RWG](https://cve-cwe-programs.groups.io/g/RWG)) is working to improve how CVE IDs are assigned quickly and accurately for Publicly Disclosed vulnerabilities, especially "hot" topics (e.g., recent, exploited in the wild, lacking remediation).  The RWG has some [working notes](https://docs.google.com/document/d/18ApPD0s7o55jE8Lj-YjC5QywroMUFtf1d7Trr9IVtTE).

## CVE-DIBS Protocol

Placeholder for the concise version.

## CVE-DIBS Protocol

The detailed version. This is largely copied mostly from the Google notes document, it's probably too detailed, make a shorter version starting with the core dibs activity. Also very much still a work in progress.

1.0 Requester (R) sees a Publicly Disclosed vulnerability lacking a CVE ID.

2.0 If R is not a CNA then

2.1 R makes an assignment request of a CNA with appropriate scope (CNA1).

2.2 CNA1 may be the Supplier of the affected Product, this Supplier is almost always the CNA with the most appropriate scope who has the right of first refusal (4.2.1 link to the rules).

2.3 CNA1 may be a CNA-LR. If the Supplier is a CNA, the CNA-LR will talk to the Supplier CNA (first refusal).

2.4 CNA1 may be another type of CNA with appropriate scope, for example, a coordinator or researcher CNA, or a CNA that solicits vulnerability reports?

2.5 R and CNA1

3.0 If R is a CNA, possibly CNA1 as described in 2. (that is, CNA1 receives an assignment request for a Publicly Disclosed vulnerability) then

3.1 R investigates the requested assignment, analyzes evidence, determines vulnerability (4.1 rules) and evaluates assignment rules (4.2 rules)

3.1.1 Note that lessons learned from this dibs protocol may result in changes to the assignment rules (4.2 rules).

4. R decides to assign (has evaluated vulnerability determination and assignment rules, has appropriate scope)

Everything up to this point is basically background or preliminary.

Dibs Protocol really starts here!

5.0 R sends a Dibs Request message to the channel, which means creating a new issue in this repo

5.1 The nature of this message is that R wants and plans to assign *unless* another CNA (possibly a CNA-LR) has a prior or competing claim. That is, by default and without a conflicting response within the timeout period, R will be clear to assign.

5.2 Channel participants have N hours to respond.

Dibs Request messages are ordered by time, when an issue was created or a comment added.

5.2.1 We may distinguish between two classes of Publicly Disclosed vulnerabilities, hot or not.

5.2.1.1 Hot. New, recent, fresh, getting public attention (socials, media), possibly EITW, possibly lacking a clear and authoritative fix). High pressure and value in assigning a CVE ID quickly.

5.2.1.2 Not. Old, stale, not recent, not getting attention, low value in getting a CVE ID quickly, but value in getting an ID at all. For this class, the Dibs Protocol may not be necessary, as the requesting CNA can talk to the CNA-LR through regular, non-urgent channels (e.g., cveform.mitre.org for the MITRE CNA-LR).

5.3 If a participant responds in agreement, great, that's nice, optional, but can help R learn that other participants are not making conflicting claims.

5.4 If one or more participants respond in conflict, the participants should try to work it out, quickly (maybe another time limit). If they can't, Root / CNA-LR. If CNAs have differen Roots, then what?

5.4.1 CNA2 responds in conflict to R (R is also CNA1). The conflicting CNAs should consider factors including: which CNA started working on the assignment earlier, has more appropriate scope, has better information, was involved in CVD.

5.5 If the timer expires without a conflicting response, R has Dibs and is clear to assign and publish.

5.5.1 R informs the channel of the assignment. At this point, no other CNAs may assign without additionally discussing with R and R's agreement.

5.5.2 R MUST act fast. No sandbagging. If some timeout is reached, Dibs reopens? Or Root / CNA-LR?

After assignment and publication, the usual rules and policies apply. An assignment or Record content can be disputed, ownership can be transferred.

6.0 R can send a PLA (Public Lacking Assignment) message to the channel. In this case, the CNA is not claiming Dibs but alerting the channel, presumably with the idea that another CNA might want Dibs. In this case, maybe just go to the Root / CNA-LR?
