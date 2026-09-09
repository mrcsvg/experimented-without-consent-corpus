---
service: "X"
service_slug: "x"
doc: 7
role: "non-binding"
url: "https://blog.x.com/engineering/en_us/a/2015/the-what-and-why-of-product-experimentation-at-twitter-0"
final_url: "https://blog.x.com/engineering/en_us/a/2015/the-what-and-why-of-product-experimentation-at-twitter-0"
captured_at: "2026-07-31T20:21:31+00:00"
vantage: "IT"
sha256_text: "e2080436bd7e25f7632e25d3bd4b0b8fa5716b286365cfd0c4208616cd5d9f76"
chars: 13200
wayback_url: null
---

The what and why of product experimentation at Twitter
Engineering
Back
Engineering
Insights
Infrastructure
Open source
Sign Up
Sign Up
The what and why of product experimentation at Twitter
Friday, 23 October 2015
Link copied successfully
Experimentation is at the heart of Twitter’s product development cycle. This culture of experimentation is possible because Twitter invests heavily in tools, research, and training to ensure that feature teams can test and validate their ideas seamlessly and rigorously.
The scale of Twitter experiments is vast both in quantity and variety — from subtle UI/UX changes, to new features, to improvements in machine learning models. We like to view experimentation as an endless learning loop:
Build a hypothesis: Come up with an idea for a new feature or an improvement to an existing one.
Define success metrics: Estimate the “opportunity size” — number of users who will be affected by the change. Formally define success and failure metrics for your experiment; consider what trade-offs are acceptable.
Test hypothesis: Implement the proposed change, instrument appropriate logging, and perform sanity checks to make sure an experiment is set-up correctly.
Learn: Examine the data collected in the experiment to see what we can learn from it, and share with other Twitter teams.
Ship : Having gathered the data, determine if the experiment validated the hypothesis, and make the ship or no-ship decision.
Build another hypothesis: Generate more hypotheses for more improvements, incorporating new ideas from the experiment.
A/B Testing, decision-making, and innovation
The Product Instrumentation and Experimentation (PIE) team at Twitter thinks about philosophy of experimentation a lot. A/B testing can provide many benefits, but it has well-known, easy-to-hit pitfalls . Its results are often unexpected and counter-intuitive . How do we avoid the pitfalls? When should we recommend running an A/B test to try out a feature or proposed change? How do we stay nimble and take big risks while also staying rigorous in our decision-making process?
The benefits of testing, and a little about incrementalism
The big concern about a culture of A/B testing feature changes is that it leads to small incremental gains, and that most experiments only move the needle by single-digit percentages, or even fractions of a percent. So, the argument goes, what’s the point? Why not work on something more impactful and revolutionary?
It’s true: by far the majority of experiments move metrics in a minimal way, if at all; an experiment that moves a core metric by a few percentage points for a large fraction of users is considered an exceptional success.
This is not due to something fundamental about A/B testing. This is because a mature product is hard to change in a way that moves the metrics by a large margin. A lot of ideas people think are home-runs simply do not move the needle: humans turn out to be pretty bad at predicting what will work (for more on this, see “ Seven Rules of Thumb for Web Site Experimenters ”). Most of the time, poor A/B test results allow us to find out early that an idea that sounds good may not work. We’d rather get the bad news and go back to the drawing board, as early as possible; so we experiment.
A/B testing is a way to make sure good ideas don’t die young, and are given the opportunity to develop fully. When we really believe in an idea, and initial experiment results don’t fulfill our expectations, we can make further changes to the product, and continue improving things until they are ready to be shipped to the hundreds of millions of people. The alternative is that you create something that feels good, you ship it, move on to some new idea, and a year later someone realizes no one is using the feature, and it gets sunset quietly.
Quickly iterating and measuring the effects of proposed changes lets our teams incorporate implicit user feedback into the product early on, as we work through various prototypes. We are able to ship a change, look at what’s working and what isn’t, create a hypothesis for what further changes would improve the product, ship those, and keep going until we have something that’s ready to launch widely.
Some may look at incremental changes as insufficient. Certainly, shipping a “big idea” sounds far better than a small improvement. Consider, however, that small changes add up, and have a compounding effect. Shying away from incremental changes that materially improve the product is simply not a good policy. A good financial portfolio balances safe bets that give predictable, albeit less than astronomical, return, and some higher-risk, higher-reward bets. Product portfolio management is not very different in that regard.
That said, there are lots of things we cannot, or perhaps should not, test. Some changes are designed to result in network effects which user-bucketed A/B testing won’t capture (although other techniques do exist to quantify such effects). Some features do not work when given only to a random percentage of people. For example, Group DMs are not a feature to use in a plain A/B test, because chances are the lucky people who get the feature would want to message those who don’t have it, which makes the feature essentially useless. Others might just be totally orthogonal — e.g., rolling out a new app like Periscope is not a Twitter application experiment. But once it’s out, A/B testing becomes an important way to drive measurable incremental and not-so-incremental changes within that app.
Yet another class of changes is major new features that are tested in internal builds and via user research, but released in a big-bang moment to all the customers in a given market for strategic reasons. Such a decision is made when, as an organization, we believe it’s the right thing to do for the product and the customer. We believe there are greater gains to be had from a large release than there are from incremental changes that lead, perhaps, to a better initial release that might get more customers trying it and using it. It’s a trade-off the product leadership chooses to make. And are we going to A/B test incremental changes to such a new features after they launch? You bet! As ideas mature, we guide their evolution using well-established scientific principles — and experimentation is a key part of the process.
Experimenting responsibly
Now that we’ve made the case for running experiments, let’s discuss what one can do to avoid the pitfalls. Experiment setup and analysis is complex. It is very easy for normal human behavior to lead to bias and misinterpretation of the results. There are several practices one can implement to mitigate the risks.
Requiring a Hypothesis
Experimentation tools generally expose a lot of data, and frequently allow experimenters to design their own custom metrics to measure effects of their changes. This can lead to one of the most insidious pitfalls in A/B testing: “cherry-picking” and “ HARKing ” — choosing from among many data points just the metrics that support your hypothesis, or adjusting your hypothesis after looking at the data, so that it matches experiment results. At Twitter, it’s common for an experiment to collect hundreds of metrics, which can be broken down by a large number of dimensions (user attributes, device types, countries, etc.), resulting in thousands of observations — plenty to choose from if you are looking to fit data to just about any story.
One way we guide experimenters away from cherry-picking is by requiring them to explicitly specify the metrics they expect to move during the set-up phase. Experimenters can track as many metrics as they like, but only a few can be explicitly marked in this way. The tool then displays those metrics prominently in the result page. An experimenter is free to explore all the other collected data and make new hypotheses, but the initial claim is set and can be easily examined.
Process
No matter how good the tools are, a poorly set up experiment will still deliver poor results. At Twitter, we have invested in creating an experimentation process that improves one’s chances of running a successful, correct experiment. Most of the steps in this process are optional — but we find that having them available and explicitly documented greatly decreases time lost to re-running experiments to collect more data, waiting on app store release cycles, and so on.
All experimenters are required to document their experiments. What are you changing? What do you expect the outcomes to be? What’s the expected “audience size” (fraction of people who will see the feature)? Collecting this data not only ensures that the experimenter considered these questions, but also allows us to build up a corpus of institutional learning — a formal record of what’s been tried, and what the outcomes were, including negative outcomes. We can use this to inform future experiments.
Experimenters can also take advantage of Experiment Shepherds. Experiment Shepherds are experienced engineers and data scientists who review experiment hypotheses and proposed metrics to minimize the chances of experiments going awry. This is optional, and recommendations are non-binding. The program has received great feedback from people who participate in it, as they have much more confidence that their experiment is set up correctly, that they are tracking the right metrics, and that they will be able to correctly analyze their experimental results.
Some teams also have weekly launch meetings, in which they review experimental results to determine what should and should not launch to a wider audience. This helps with addressing issues like cherry-picking and misunderstanding of what statistical significance is saying. It’s important to note this is not a “give me a reason to say no” meeting — we’ve definitely had “red” experiments ship, and “green” experiments not ship. The important thing here is to be honest and clear about the expectations and results of the changes we are introducing, not to tolerate stagnation and reward short-term gains. Introducing these reviews has significantly raised the overall quality of the changes we ship. It’s also an interesting meeting, because we get to see all the work that’s occurring on the team, and how people are thinking about the product.
Another practice we employ frequently is using “holdbacks” when possible — rolling out a feature to 99% (or some other high percentage) of users, and observing how key metrics diverge from the 1% that was held back over time. This allows us to iterate and ship quickly, while keeping an eye on the long-term impact of the experiment. This is also a good way to validate that gains expected from the experiment actually materialize.
Education
One of the most effective ways to ensure that experimenters watch out for pitfalls is simply to teach them. Twitter Data Scientists teaches several classes on experimentation and statistical intuition, one of which is in the list of classes all new engineers take in their first few weeks at the company. The goal there is to familiarize engineers, PMs, EMs and other roles with the experimentation process, caveats, pitfalls, and best practices. Increasing the awareness of the power and pitfalls of experimentation helps us avoid losing time on preventable mistakes and misinterpretations, getting people to insights faster and improving cadence as well as quality.
Coming soon
In upcoming posts, we will describe how DDG, our experimentation tool, works; we will then jump straight into several interesting statistical problems we have encountered — detecting biased bucketing, using (or not using) a second control as a sanity check, automatically determining the right bucket size, session-based metrics, and dealing with outliers.
Acknowledgements
Thanks to Lucile Lu , Robert Chang , Nodira Khoussainova , and Joshua Lande for their feedback on this post. Many people contributed to the philosophy and tooling behind experimentation at Twitter. We’d particularly like to thank Cayley Torgeson , Chuang Liu , Madhu Muthukumar , Parag Agrawal , and Utkarsh Srivastava .
Share:
Link copied successfully
Follow
Tweets
Following
Followers
X platform
X.com
Status
Accessibility
Embed a post
Privacy Center
Transparency Center
Download the X app
Try Grok.com
X Corp.
About the company
Company news
Brand toolkit
Jobs and internships
Investors
Help
Help Center
Using X
X for creators
Ads Help Center
Managing your account
Email Preference Center
Rules and policies
Contact us
Developer resources
Developer home
Documentation
Forums
Communities
Developer blog
Engineering blog
Developer terms
Business resources
Advertise
X for business
Resources and guides
X for marketers
Marketing insights
Brand inspiration
X Ads Academy
‎© 2026 X Corp.‎
Cookies
Privacy
Terms and conditions
Did someone say … cookies?
X and its partners use cookies to provide you with a better, safer and
faster service and to support our business. Some cookies are necessary to use
our services, improve our services, and make sure they work properly.
Show more about your choices .
Accept all cookies
Refuse non-essential cookies