---
service: "Bing"
service_slug: "bing"
doc: 5
role: "unknown"
url: "https://blogs.bing.com/search-quality-insights/June-2013/Experimentation-and-Continuous-Improvement-at-Bing/"
final_url: "https://blogs.bing.com/search-quality-insights/June-2013/Experimentation-and-Continuous-Improvement-at-Bing/"
captured_at: "2026-07-31T01:13:09+00:00"
vantage: "IT"
sha256_text: "d4938c950a1068ef54ae5a7ef7206c0d026e45e0fb868cd4414c3ac46a08374f"
chars: 10883
wayback_url: null
---

Experimentation and Continuous Improvement at Bing | Search Quality...
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
June 12 2013
Experimentation and Continuous Improvement at Bing
One technical problem in Web search is how best to measure the quality of search results. Our powerful machine learning systems correct the spelling of your query , interpret your search intent, differentiate quality pages from junk , rank documents from our index of tens of billions of documents, and optimize whole-page layout . These systems, and many more, must all be optimized towards user satisfaction. The problem is that there is no perfect measure of objective user satisfaction, so we use surrogate measures. Surprisingly, once your machine learning systems are powerful enough, your choice of surrogate measure has a strong influence on the kind of results you return. In this blog post Nick Craswell and Filip Radlinski describe some of the issues motivating their award winning research paper on measuring search results which was presented at the international conference WSDM-2013.
– Dr. Harry Shum, Corporate Vice President, Bing R&D
In information retrieval (IR) research there is a strong focus on relevance measurement. For example this year at SIGIR , which is one of the largest research conferences in the area, there are two sessions dedicated to IR evaluation, plus one tutorial and one workshop. As members of a research team at Bing, we get to work on a large range of interesting problems in machine learning, data mining and information retrieval. A recurring theme is relevance measurement. In this blog post we’ll outline some of our work in the area.
From the broad range [ 1 , 2 ] of possible measures of search quality, we will cover two major alternatives: online and offline. Our goal is to describe what they are and why we need both. Then we’ll describe our recently-published work at WSDM-2013 [ 3 ], which is about online measurement.
Online vs Offline Evaluation
To provide the most relevant and useful search results, modern search engines must try to correctly predict what people are trying to accomplish. If someone types the query ‘florida songs’, the engine has to interpret whether the searcher meant songs about Florida, or songs by rapper Flo Rida, or something else. It’s difficult to know the right interpretation without asking the person who typed the query, or deducing their intent based on their behavior. That’s where online measures come in, these are the ones that involve feedback from a real user in context of what they are doing.
At the same time, we’d like the search to return results of high quality. For instance, imagine two pages with the same information, but one has many more ads and pop-up windows. Imagine two pages with the same information, but one is from the National Institute of Health and the other is from an abandoned health blog with only one entry. Or imagine two pages from the same site, but one directly answers your query while the other one requires you to browse within the site. To tell which pages are best, we perform offline evaluation. We write detailed guidelines on what constitutes a high-quality page, and ask trained experts to annotate which pages are best.
Now the problem. The paid experts, despite all their training, have difficulty guessing correctly whether it was Florida or Flo Rida. The only person who knows the correct interpretation is the one who typed that query, and we need their online feedback to identify the true intent. Meanwhile it is difficult for online experiments to detect subtle issues with page quality. People who see slightly the wrong page or the wrong site may still find the information they need but we could have provided a better result. To identify such problems, and define guidelines on what constitutes a good search result, we use offline annotations from our trained experts.
We need both online and offline measurement to correctly measure relevance. Now let’s look at how we employ online metrics.
Using Online Evaluation
A typical online experiment compares some new version of Bing to the existing version, to see whether the new idea is an improvement on average. When we set up such an experiment, we want three things. First, it must give the right answer. This might seem obvious, but if people prefer the new version we want our experiment to detect that in a reliable way. Second, the evaluation must not degrade the search experience. For instance, we could pop a window up to ask you whether you were successful after searching, but that would be intrusive and annoying. Ideally you would not even know that you are in an experiment. Finally, we would like the evaluation to give us an answer fast. If an idea makes Bing better, we would like to have it out the door as soon as possible. If an idea fails we want to know that quickly too, so we can stop showing it to people.
Since there is no questionnaire, the main thing we can observe is your search behavior:
· You enter your search terms, we retrieve results, and you respond to these results by clicking on some, or typing a new query.
We do an online evaluation by measuring these responses.
To compare the two versions of Bing, one option is to do a controlled experiment, which is also known as an A/B test. Each person in the experiment is assigned either to a control group that sees system A or a treatment group that sees system B. We then measure the responses of each group, to try and infer which system was better. For instance, if people in group A select results more quickly than in group B, that would indicate that system A is better, all other things being equal. Our researchers spend a lot of time studying controlled experiments [4] to understand how changes in user responses correspond to improvements in user satisfaction.
An alternative to an A/B test is called a paired comparison, where everybody is shown a mix of the results produced by both the A and the B systems. This way, everyone sees some results that come from Bing today, and some from Bing with our new idea.
It is a blind experiment, meaning that you can’t tell which came from Bing today, and which came from our new idea. Showing A and B together means we can elicit a direct preference, telling us whether people preferred results from A or from B. This direct preference means that a paired experiment can reach its conclusion much more quickly than an A/B experiment. Another advantage of combining A and B is that it avoids the downside if one list is much worse than another. For example, if B fails for some query then nobody is stuck with just B, they still see some of A.
Our WSDM-2013 paper [ 4 ] proposes a new way of performing unbiased and informative paired evaluations. This is where things get a little more technical. When someone sets up a paired comparison experiment using our approach, we allow them to specify two things. One is what combinations of A and B are allowable. For example, if A and B return disjoint top-10 lists then we have 20 unique results, one approach would be to allow any of the 20 results to appear anywhere in the combined list. However, being too free with this is essentially shuffling the results, which is bad for people in the experiment. We solve this by restricting the allowable combinations. In the paper we stick with combinations such that any prefix of the combined list is made up of prefixes from A and B.
The other thing the experimenter can define is some reward function, which is applied when someone selects a result from the combined list. The general principle is to identify where the selected result appears in A and B, then reward the system that had it closer to the top, giving a bigger reward if the result was moved further and closer to the top. For example, if the selected result is at rank 4 in A and rank 2 in B, perhaps this gives 2 points to B, rewarding based on the difference in rank.
Based on input from the experimenter, we now know the possible ways of combining A and B, and we also know how to reward each system based on what results are selected. Then the core of our approach is a method for deciding which combinations to show, to get an unbiased and informative experiment. The main bias that we’re concerned with is “position bias”: Results near the top of the combined list are more likely to be selected by users. In the context of our experiment, if we systematically put results from B above those of A then this extra prominence means B is more likely to win. The solution is to sometimes show lists biased towards A and sometimes lists biased towards B. More specifically, given the allowable combined lists and reward function, we solve for a probability distribution over lists that is unbiased with respect to a user model that generates a top-heavy click pattern. Since there are usually multiple solutions, we also have a preference for solutions that are informative, which means that the combined list has a mixture of results that reward A and B, rather than just one or the other.
We can refer you to the paper for the details, but the overall outcome is that we can generate an optimal paired experiment that brings together a unique combination of results and reward functions. As a Bing user, you have probably taken part in both A/B and paired evaluations many times. Now you know that it is thanks to you that we can keep Bing ahead of the competition!
– Dr. Nick Craswell and Dr. Filip Radlinski, Applied Research, Bing R&D
[ 1] M. Sanderson (2012). Test Collection Based Evaluation of Information Retrieval Systems . Vol. 4. No. 4. Foundations and Trends in Information Retrieval
[ 2] S.T. Dumais, R. Jeffries, D. Russell, D. Tang, and J. Teevan (2011). Design of large scale log analysis studies. In Proceedings of CHI 2011 (Course)
[ 3] F. Radlinski and N. Craswell (2013). Optimized interleaving for online retrieval evaluation . Optimized interleaving for online retrieval evaluation. In Proceedings of WSDM 2013
[ 4] R. Kohavi, A. Deng, B. Frasca, R. Longbotham, T. Walker and Y. Xu (2012). Trustworthy online controlled experiments: five puzzling outcomes explained. In Proceedings of KDD 2012
Back to
Top
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