---
service: "Bing"
service_slug: "bing"
doc: 6
role: "unknown"
url: "https://blogs.bing.com/search-quality-insights/August-2013/Large-Scale-Experimentation-at-Bing"
final_url: "https://blogs.bing.com/search-quality-insights/August-2013/Large-Scale-Experimentation-at-Bing"
captured_at: "2026-07-31T01:13:11+00:00"
vantage: "IT"
sha256_text: "9da679c47e1e933efe2fa22e4e8341403bd62a293fd1684e2880267d61a87b95"
chars: 7651
wayback_url: null
---

Large Scale Experimentation at Bing | Search Quality Insights
Skip to content
Menu
This is a place devoted to giving you deeper insight into the news, trends, people and technology behind Bing.
Search for
Blogs
Home
Search
Maps
Webmaster
Search Quality Insights
Jobs
Engineering Blog
Regions
Australia
Canada
China
France
Germany
India
Japan
UK
Follow us:
Subscribe RSS
August 8 2013
Large Scale Experimentation at Bing
Experimenting at large scale is fundamental for improving Bing. Last June, we published a blog in this Search Quality Insights series titled Experimentation and Continuous Improvement at Bing , which covered a specific type of experiments known as interleaving. In this blog, Dr. Ronny Kohavi describes our broader online experimentation efforts at large scale and includes compelling examples that illustrate the power of these efforts, e.g., he shows how a controlled experiment at large scale of a relatively small feature change can lead to many millions of dollars in revenue. Ronny’s blog is a brief summary of a research paper titled Online Controlled Experiments at Large Scale which will he will present next week at the international conference on Knowledge Discovery and Data Mining ( KDD 2013 ). The paper has already received positive feedback by well-known experts in this field, and we’re sharing their comments in this blog with their permission.
Dr. Harry Shum, Corporate Vice President, Bing R&D
Microsoft’s Bing search engine steadily increased US market share and improved financial performance in the four years since its launch. What the numbers don’t capture are the humbling experiences discussed in an upcoming paper at the KDD conference, titled Online Controlled Experiments at Large Scale .
When ideas are evaluated objectively in a controlled experiment, less than a third move the metrics they were designed to improve, and in an optimized domain like Bing, that number is lower. Humbling! We joke that our job in building Bing’s experimentation platform is to tell our developers and program managers that their new baby is ugly.
What is an online controlled experiment? In its simplest form, called an A/B test , we randomly split our users into two groups as shown in the diagram below. Their experiences are exactly the same, except for a change introduced to the Treatment (or B group).
We compare key metrics for the users in the treatment versus the control and determine, based on statistical tests, if the difference is large enough to be unlikely to be seen by chance, i.e., statistically significant. The idea is to expose our changes to real users and see if their experiences improve, following the Customer Development Process championed by Steve Blank.
A real example of an A/B test is as follows. We wanted to add a feature allowing advertisers to provide links to the target site. The rationale is that this will improve ads quality by giving users more information about what the advertiser’s site provides and allow users to directly navigate to the sub-category matching their intent. Visuals of the ads layout (Control) and the new ads layout (Treatment) with site links added are shown below.
Ads with site link experiment. Treatment (bottom) has site links. The difference might not be obvious at first but it is worth tens of millions of dollars
In this experiment, the evaluation criterion was simple: increase average revenue per user without degrading key user engagement metrics. The experiment results showed that the newly added site links increased revenue, but also degraded user metrics, likely because of increased vertical space usage. Even after reducing the extra space consumed by the new feature by lowering the average number of ads shown per query, this feature improved revenue by tens of millions of dollars per year with neutral user impact, resulting in extremely high ROI (Return-On-Investment).
Here are a few interesting points from the KDD paper :
Controlled experiments are the primary mechanism at Bing to separate the good ideas from the bad ones, hence our ability to lower the cost of experiments and run more experiments concurrently helps our innovation engine. As Mike Moran said in his book : “If you have to kiss a lot of frogs to find a prince, find more frogs and kiss them faster and faster.” The graph below shows the exponential growth in experimentation over time. On a typical day, there are over 250 experiments running on Bing.
Almost every user is in some experiment when they visit Bing. In fact, almost every user is in about 15 different experiments. There is no single Bing any more, but rather each user falls into one of the 30B possible experiment combinations.
Statistical tests are run regularly to detect badly performing experiments and interacting experiments; alerts are e-mailed to the experiment owners for underperforming experiments, and those impacting key metrics more severely are shut down automatically.
Many features start small, as a Minimal Viable Product, an idea popularized by Eric Ries in his Lean Startup book. After a small experiment, we ramp-up the Treatment and expose it to about 10% of our users.
We deal with Big Data. A 10% Treatment (and 10% Control) experiment that runs for two weeks requires processing about 4TB of data to generate a summary analysis.
It is not uncommon to see experiments that unintentionally impact revenue positively or negatively by 1%. This is why it is so important to evaluate everything in a controlled experiment.
Many web-facing companies have started running controlled experiments to guide product development and accelerate innovation. To scale to the level we have at Bing, we had to invest heavily in avoiding pitfalls and analyzing puzzling results . We hope the lessons we share will allow others to scale their systems and accelerate innovation through trustworthy experimentation. Paras Chopra, founder of Wingify (Visual Website Optimizer) wrote “I’m sharing your paper with our entire team at Visual Website Optimizer. I’m sure we will have lots of things to learn from your team. 200 concurrent experiments on a single product is simply incredible.”
— Dr. Ronny Kohavi, Partner Architect, Bing R&D
Microsoft’s upcoming KDD paper lovingly demonstrates Microsoft’s impressive scale at deploying controlled experiments to create an organization that thinks smart and moves smart!
– Avinash Kaushik, Author of Web Analytics 2.0, Web Analytics: An Hour a Day ,
and Occam’s Razor blog.
Awesome paper, the focus on customer experimentation—at scale—is an impressive example of customer development and evidence-based innovation.
– Steve Blank , a consulting associate professor at Stanford, and Author of the Four Steps to the Epiphany and the Startup Owner’s Manual .
Deploy all software as an A/B test, assess the value of your ideas, test everything. Years of experience went into Microsoft’s KDD paper. Go read it.
– Greg Linden, Entrepreneur, Blogger, Geeking with Greg
Tags
bing
Experimentation
Search Quality Insights
Back to
Top
Related Stories
Turing Bletchley v3 - A Vision-Language Foundation Model
8/29/2023 — Bing Team
Driving Performance at Microsoft Bing
8/17/2023 — Bing Team
Building the New Bing: Image Creator
3/23/2023 — Bing Team
Links for Bing
Explore Bing
Bing AI Tips
Bing Rewards
Bing Help
Bing Ads
Other Microsoft links
Official Microsoft Blog
About Microsoft
Microsoft AI
Microsoft News
Diversity and Inclusion
Other product blogs
Bing Ads Blog
Skype Blog
Windows Blog
M365 Blog
Xbox Wire
Powered by Azure
Legal
Trademarks
Privacy Statement
Consumer Health Privacy
Manage Cookies
© 2026 Microsoft Corporation. All Rights Reserved.