---
layout: single
title:  "Mindful technical debt: a framework"
date:   2023-08-11 11:09:59 +0100
categories: startups 
header:
  overlay_image: /assets/images/posts/tech_debt.webp
  overlay_filter: 0.6 # same as adding an opacity of 0.5 to a black background
  teaser: /assets/images/posts/tech_debt.webp
---

I used to believe that technical debt was always bad. Whenever I joined companies that had well-established products, I couldn't help but question the quality of parts of the code. But why is it so common to encounter poorly designed code at the core of a system? 

As my experience and responsibilities grow, I am now in the position where I am deciding to (occasionally) take on tech debt. So why would I, or anyone else, willingly go down this path? The answer lies in the nature of startup culture, where speed is of utmost importance. And, as you’ll see, speed and technical debt are often inseparable twins. But before I instil the virtues of technical debt, let’s first define exactly what it is.


# What is technical debt?

Technical debt refers to the accumulated costs and consequences that arise from making suboptimal technical decisions during software development. It is comparable to financial debt, where short-term gains are made at the expense of long-term obligations i.e. that iPad Pro you just purchased, that you will be paying off for the next year! It manifests itself in the form of inefficient or poorly designed code, outdated libraries or frameworks, incomplete documentation, unresolved bugs, or architectural limitations. 

Like financial debt, tech debt accumulates interest over time. It can impede productivity, hinder innovation, increase the chances of errors and security vulnerabilities, and impose higher costs for maintenance and enhancement. The longer it remains unaddressed, the more it can drain resources, limit agility, and hinder the overall quality and stability of the software. Developers spend more time deciphering convoluted code, and working around legacy design choices rather than focusing on delivering new features or improvements. This can slow down development cycles, hinder collaboration, and ultimately decrease productivity within the development team.

Moreover, tech debt can act as a barrier to innovation. There is limited room for experimentation and pushing boundaries in a codebase that is resistant to change. This restricts the ability to introduce novel features, adopt new technologies, or embrace industry best practices. If left untreated, the rigidity imposed by tech debt stunts innovation, leaving the software stagnant and unable to adapt to evolving user needs and market demands.

There are many other consequences to accumulating tech debt that I won't go into here. However, even with this information at the forefront of my mind, I still find myself occasionally choosing to accumulate tech debt for one very specific reason. 



# Why is it (sometimes) necessary?


As Reid Hoffman, Co-founder of LinkedIn once said: “if you're not embarrassed by your first product launch, you've launched too late”. Or to put it another way: [release early, release often](https://en.wikipedia.org/wiki/Release_early,_release_often)

Herein lies the paradox: in the fast-paced world of startups, speed is crucial for survival. When a startup is trying to capitalise on a market opportunity, delivering a functional product trumps the need for meticulously crafted code. Consequently, accumulating some level of tech debt becomes inevitable. However, it's important to understand that incurring debt should never be a reckless or careless decision. It should be a conscious choice made with a clear understanding of the long-term consequences. Startups must balance the need for speed with the commitment to address and gradually pay off the accrued debt over time.

By acknowledging the necessity of tech debt and managing it properly, startups can strike the right balance between delivering a functional product quickly and ensuring a solid foundation for future growth. It's about making calculated trade-offs to seize market opportunities while keeping an eye on the future sustainability and scalability of the software product.

I take on tech debt, with one mindset: go fast now to go slower later. In a fast-paced startup ecosystem, reaching the market before your competition can be the difference between success and failure. If we're trying to find market fit quickly (i.e. before we run out of money), speed now trumps most things. Striking the right balance between tech debt and speed of delivery is an art, and one worth mastering. With that in mind, I present a simple framework for you to follow to introduce and manage technical debt mindfully.



# Framework

1. **Identify the need for introducing technical debt**. Start by identifying the problem or requirement that you believe justifies the introduction of technical debt. This could be due to pressure for a quick release, resource limitations, or any other valid reason. It’s important to take a moment here and decide whether the reason is truly valid before continuing. 

2. **Assess the impact**. Ok, so you’ve decided you need to compromise because of an external factor. There’s no other way around it. Before you jump in, you need to evaluate the potential impact of introducing technical debt on the project. Consider factors such as future development, maintenance, code quality, scalability, and team productivity. This step will help you make an informed decision, understand the implications, and inform the team of those implications. Which brings me to the next step:

3. **Discuss with the team**. This includes stakeholders, project managers, and other developers. Share two things: 
    1. The need for the compromise (identified in step 1) 
    2. The impact of the compromise (step 2). 
    
    Obtain their feedback and ensure everyone is aligned on the potential consequences. Have you spoken to the Project Manager about the tradeoffs necessary to reach the current release window? Is there wiggle room? Can you spend a bit longer and do it right first time?

4. **Create a ticket**. Once the decision is made and the team informed, you need to codify the decision in a ticket. The ticket should contain:

    *Title and Description*: Provide a clear and concise title for the ticket that describes the technical debt issue. In the description, explain the specific problem, its impact on the system, and any associated risks.

    *Detailed Explanation*: Provide a thorough explanation, including the reasons it occurred, how it affects the codebase or system, and any potential drawbacks or limitations.

    *Proposed Solution*: If you have one in mind, offer a proposed solution or approach to address the technical debt. At this point, you are the closest to the problem and your insight may prove invaluable when it comes to fix the issue.

    *Resources and Time Estimates*: Assess the resources required to address the technical debt, such as development time, expertise, or additional tools. Provide time estimates for completion and potential milestones if applicable.

    *Collaboration and Ownership*: Identify the team or individuals responsible for resolving the technical debt. Clearly communicate who should be involved and their roles in the process.

    *Success Criteria*: Define the criteria for success and completion of the ticket. It may include the successful elimination of the technical debt, improved system performance, enhanced code quality, or any other specific benchmarks.


7. **Implement the technical debt**. Begin implementing the necessary changes in the project. Even though, at this stage you know you're not implementing the ideal code, you still need to ensure that your code does not introduce critical bugs or issues that could jeopardise the stability of the application. Design your application with some flexibility. A good architecture allows changes to be done more smoothly and might also help in isolating parts of the app that are heavily in debt.

8. **Incorporate Technical Debt Management in Development Cycles**. This is an important one. Everything up to this point, would be meaningless if you don't spend time managing and resolving technical debt. It’s unlikely that you will ever get a full sprint to deal with technical debt. Instead, allocate a small percentage of each sprint to deal with tech debt. The percentage will fluctuate based on the needs of the company, but it is important that you keep pushing for time to make things right.

Remember this: Not all tech debt is bad. A deliberate, conscious decision to incur tech debt to hasten a product’s speed to market can be a wise trade-off, provided it is recognised and managed carefully. Like a tool, when wielded skilfully, it can allow startups to stay nimble, beat the competition, and make crucial pivots promptly. However, if neglected or left unnoticed, it can incur heavy penalties down the line and will impede your speed later. 

