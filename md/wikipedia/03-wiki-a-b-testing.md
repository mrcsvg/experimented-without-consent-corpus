---
service: "Wikipedia"
service_slug: "wikipedia"
doc: 3
role: "non-binding"
url: "https://wikitech.wikimedia.org/wiki/A/B_testing"
final_url: "https://wikitech.wikimedia.org/wiki/A/B_testing"
captured_at: "2026-07-31T01:16:29+00:00"
vantage: "IT"
sha256_text: "006d03f3eda48a2470aca8a1bf7e6e7a25379eb952c9537cc4bce734d03dc49f"
chars: 4599
wayback_url: null
---

A/B testing - Wikitech
Jump to content
Main menu
Main menu
move to sidebar
hide
Navigation
Main page
Server admin log: Prod
Admin log: RelEng
Incident status
Deployments
SRE Team Help
Cloud VPS & Toolforge
Cloud VPS portal
Toolforge portal
Request VPS project
Admin log: Cloud VPS
wikitech.wikimedia.org
Recent changes
Special pages
Village pump
Search
Search
English
Appearance
Donate
Create account
Log in
Personal tools
Donate
Create account
Log in
Contents
move to sidebar
hide
Beginning
1
Infrastructure
2
Bucketing
3
Sample size / power analysis
4
General advice
Toggle General advice subsection
4.1
A/B testing on wiki
5
Software
Toggle the table of contents
A/B testing
Page
Discussion
English
Read
View source
View history
Tools
Tools
move to sidebar
hide
Actions
Read
View source
View history
General
What links here
Related changes
Permanent link
Page information
Cite this page
Get shortened URL
Print/export
Create a book
Download as PDF
Printable version
Appearance
move to sidebar
hide
From Wikitech
In the Wikimedia platform, the impact of many new features are tested using controlled experiments. Many more should be. This page collects any thoughts, questions, and links that are relevant to the topic.
Infrastructure
Test Kitchen (Experimentation Lab / xLab / MPIC)
Troubleshooting
Phab tasks
T76917 (2014): Investigate using Optimizely for UI A/B testing [declined]
T76919 (2014): Implement reusable framework for A/B testing product features [declined]
T135762 (2016): A/B Testing solid framework [declined]
T208089 (2018): Infrastructure for interventions impacting editing metrics [declined]
T213315 (2019): [Better Use of Data] Output 3.2: Controlled experiment (A/B test) capabilities [resolved]
The "bucket" field is the standard for recording buckets in EventLogging data. Maybe this could be made a default part of every schema, and general tools provided so that a bucketed user would have their bucket set along with all of their events for the duration of the test.
Bucketing
The most common way to bucket editors for A/B tests has been on their user ID. If the test spans multiple wikis, it would be an improvement to do it on their user name, because that's consistent across wikis, and would ensure they're placed in the same bucket across multiple wikis. This would mean we need to hash the user name to ensure a consistent distribution.
It would also be possible to user the global user ID, which would remove the need for hashing, although as of April 2019, that's not available to client-side JavaScript.
Sample size / power analysis
Evan's Awesome A/B Tools
General advice
Emily Robinson, Guidelines for A/B Testing
Privacy-conscious AB testing at Wikimedia Foundation
A/B testing on wiki
This is from an email from Aaron Halfaker.
This generally applies for any study that might affect our users. An experiment, a survey, or a large-scale interview study, etc.
Create a description of the study on Meta in the Research namespace
https://meta.wikimedia.org/wiki/Research:New_project
Make sure to clear describe the goals of the study and any disruption it might cause.
Post on a community forum where the active users are likely to take note. E.g. the Village Pump on English Wikipedia .
Engage in the discussion there.
Make sure to link to your Meta page.
It's common for no one to respond. You should wait at least a few days. Consider making a follow-up post reminding people that you'd like to start the study soon (bonus points for a target deployment date.
Sometimes there will be a negative response. Try your best to address concerns and make modifications to the study design. If the negative response persists, consider rescheduling or fundamentally redesigning the study.
Assuming the discussion went well, do the study. Update the meta page with results and discussion.
Post the results of the study in the same community forum and consider bringing it to the Wikimedia Research Showcase .
Software
Some Wikimedia A/B tests are hard-coded, such as A/B testing used for the skin Vector 2022. As of 2023, an example file they use can be found in the Vector 2022 repo and is named A/B.js .
Retrieved from " https://wikitech.wikimedia.org/w/index.php?title=A/B_testing&oldid=2366075 "
This page was last edited on 27 November 2025, at 14:06.
Text is available under the Creative Commons Attribution-ShareAlike License ;
additional terms may apply.
See Terms of Use for details.
Privacy policy
About Wikitech
Disclaimers
Code of Conduct
Developers
Statistics
Cookie statement
Mobile view
Search
Search
Toggle the table of contents
A/B testing
Add topic