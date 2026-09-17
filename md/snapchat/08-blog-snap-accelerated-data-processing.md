---
service: "Snapchat"
service_slug: "snapchat"
doc: 8
role: "unknown"
url: "https://blogs.nvidia.com/blog/snap-accelerated-data-processing/"
final_url: "https://blogs.nvidia.com/blog/snap-accelerated-data-processing/"
captured_at: "2026-07-31T01:14:52+00:00"
vantage: "IT"
sha256_text: "326f51d456a8ea1af2e1915a32e997169117f8dd55252ab14268a5dab0e45a9a"
chars: 5685
wayback_url: null
---

Open Libraries for Accelerated Data Processing Boost A/B Testing for Snap | NVIDIA Blog
Skip to content
Snap Decisions: How Open Libraries for Accelerated Data Processing Boost A/B Testing for Snapchat
NVIDIA cuDF accelerates Apache Spark applications on Google Cloud helps Snap engineers test and deploy new features faster while unlocking significant cost savings.
March 17, 2026 by Sid Sharma
0 Comments
Share
Share This Article
X
Facebook
LinkedIn
Copy link
Link copied!
The features on social media apps like Snapchat evolve nearly as fast as what’s trending. To keep pace, its parent company Snap has adopted open data processing libraries from NVIDIA on Google Cloud services to boost development.
Every new feature rolled out to Snapchat’s more than 940 million monthly active users goes through a set of controlled experiments before it’s launched. During this A/B testing cycle, the development team studies different variables with a subset of users, measuring nearly 6,000 metrics that analyze engagement, app performance and monetization.
Snap runs thousands of these experiments each month — processing over 10 petabytes of data within a three-hour window each morning using the Apache Spark distributed framework. By adopting Apache Spark accelerated by NVIDIA cuDF , the company is boosting these data processing workloads on NVIDIA GPUs to achieve 4x speedups in runtime with the same number of machines, providing a cost-effective path to scale.
By pairing NVIDIA’s GPU-optimized software, including NVIDIA CUDA-X libraries, with Google’s infrastructure management services such as Google Kubernetes Engine, Snap is harnessing a full-stack platform for data processing at scale.
“Experimentation is at the core of our company. Changing our data infrastructure from CPUs to GPUs allows us to efficiently scale this experimentation to more features, more metrics and more users over time,” said Prudhvi Vatala, senior engineering manager at Snap. “The more experiments we’re able to run, the more innovative experiences we can deliver for Snapchat users.”
A Sustainable Way to Scale
Snapchat fans frequently see new features in the app — from arrival notifications to AI-generated stickers — but Snap is also continuously rolling out behind-the-scenes updates such as performance optimizations and compatibility updates for new operating system versions.
The A/B testing for all these new features now runs on cuDF, which allows developers to run existing Apache Spark applications on NVIDIA GPUs with no code changes for easy deployment. The open library for accelerated data processing builds on the power of the NVIDIA cuDF GPU DataFrame library while scaling it for the Apache Spark distributed computing framework.
With this migration, the team has — based on Snap internal data collected between January 1 and February 28 — realized 76% daily cost savings using NVIDIA GPUs on Google Kubernetes Engine compared with CPU-only workflows.
“We were projecting an ambitious roadmap to scale up experimentation that would have blown up our computing costs based on our existing infrastructure,” Vatala said. “Switching to GPU-accelerated pipelines with cuDF gave us a way to flatten the scaling curve, and the results were tremendous.”
To support workload migration, the team also harnessed cuDF suite of microservices that automatically qualify, test, configure and optimize Spark workloads for GPU acceleration at scale.
Working with NVIDIA experts, the Snap team optimized its pipelines on Google Cloud’s G2 virtual machines powered by NVIDIA L4 GPUs so they required just 2,100 GPUs running concurrently — as opposed to the initial projection that around 5,500 GPUs would need to run concurrently, according to data Snap collected between January 1 and March 13.
“When I saw the results of the initial experiments, they were pretty crazy — we saw much higher cost savings than we had expected,” said Joshua Sambasivam, a backend engineer on the A/B testing team. “The Spark accelerator is a perfect match for our workloads.”
Looking ahead, the Snap team plans to integrate the Spark accelerator beyond the A/B team to a broader range of production workloads.
“We didn’t realize we were sitting on this gold mine,” Vatala said. “We’ve so far migrated our two biggest pipelines, but there’s a lot of opportunity ahead.”
Learn more by tuning into Vatala’s session at NVIDIA GTC , taking place Tuesday, March 17 at 1 p.m. PT .
Read more about NVIDIA cuDF and get started with GPU acceleration for Apache Spark .
Main image above courtesy of Snap, depicting A/B test of its Maps feature.
NVIDIA GTC Berlin Registration Is Now Open
October 20-22
Register Now
Recent News
Gaming
Best in Class: Stream PC Games and Study on the Same Laptop With GeForce NOW
July 30, 2026
Robotics
Powerful Compute So Compact, It’s Clutch — Build AI Anywhere With NVIDIA Jetson
July 28, 2026
AI
Industry Leaders Unite in Open Secure AI Alliance for AI Safety and Security
July 27, 2026
Hardware
NVIDIA Harnesses Vera CPU to Speed Up Design of Next-Generation CPUs and GPUs
July 26, 2026
View All Recent News
Categories:
Accelerated Analytics
Software
Tags:
Consumer Internet
CUDA-X
Customer Stories
Data Science
Open Source
Related News
AI
Industry Leaders Unite in Open Secure AI Alliance for AI Safety and Security
Jul 27, 2026
AI
At AI Summit, South Korea Outlines Its AI Future With NVIDIA and Partners
Jul 23, 2026
AI
Built in Fort Worth: Wistron Opens Advanced Manufacturing Plant to Produce NVIDIA AI Systems
Jul 21, 2026
AI
NVIDIA and Partners Build in America, for America
Jul 21, 2026
Share This
Facebook
LinkedIn
Share on Mastodon
Enter your Mastodon instance URL (optional)
Share