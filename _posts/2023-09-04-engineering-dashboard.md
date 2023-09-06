---
layout: single
title:  "The who, what, where, why, and how of engineering dashboards"
date:   2023-08-28 10:00:00 +0100
categories: startups management analytics
---

This is how ChatGPT would start this post:
‘“In the fast-paced realm of modern technology, where innovation is relentless and competition is fierce, engineering teams are challenged to deliver exceptional results while managing complex projects and dynamic landscapes. The key to success lies in harnessing the power of data insights—transforming raw information into actionable knowledge that empowers informed decision-making, fosters collaboration, and drives continuous improvement.”

I can put it more succinctly: being a developer is fucking hard. Everything changes all the time and expectations on us are high (as they should be). However, all is not lost, as we have 2 major levers to help us in our role:
1. We know data
2. We can build cool shit to visualise data 
  
Welcome to the (not so comprehensive) guide on “Navigating Engineering Excellence with Data-Driven Dashboards” aka the who, what, where, why, and how of
 engineering dashboards (although it’’s not really so much the ‘who’ or ‘where’ as who doesn’t make sense and the where is your company…). 

There’s one goal for this post: to encourage you to consider implementing an engineering dashboard if you haven’t already. Whether you’re a startup aiming to optimise your development processes or an established company seeking to enhance your engineering endeavours, I truly believe that a dashboard can help improve your teams performance (plus it has other benefits that extend beyond your team as we will see shortly) .

## The need for engineering dashboards
I don’t believe I will shock you when I say that tracking and monitoring Key Performance Indicators (KPIs) is crucial for ensuring project success, team efficiency, and continuous improvement. However, neither would I be shocked, if you told me that yes you’ve spoken about KPIs at some point in the past, and may have even set some, but you don’t think about them often and speak about them even less. There are many reasons for this, the traditional methods of manual data collection, analysis, and reporting can be time-consuming, error-prone, and lack real-time insights. This is where engineering dashboards come into play, revolutionising  the way engineering teams manage and harness their KPIs. ‘Revolutionising’ may seem like an overly grand term for what is essentially just removing manual processes (or adding processes that didn’t exist previously), but in the same way that continuous deployment has revolutionised the way we deploy code, this will do the same for performance tracking. 

Manual KPI tracking involves sifting through data across various tools and systems, making it challenging to get a holistic view of team performance and project health. The delays in data aggregation and reporting hinder timely decision-making, potentially impacting project timelines and outcomes. Plus if it’s a pain to do, people will stop doing it at the first available opportunity.

Engineering dashboards are simple to grasp: they consolidate data from multiple sources into a single, visually rich platform. The dashboard acts as a real-time control centre, offering engineering teams an ‘at a glance’ view of their KPIs, metrics, and progress. Whether it’s monitoring code quality, deployment frequency, bug trends, or team velocity, an engineering dashboard presents these insights in a concise and interactive manner. One of the more compelling advantages of an engineering dashboard is its ability to provide real-time insights. By capturing and presenting data in real-time, engineering teams gain an immediate understanding of their current status. They can then respond promptly to changes, address issues, and make informed decisions.

Now the true power comes when you share the dashboard more widely i.e. outside the team. Engineering dashboards can foster transparency within organisations by offering a centralised view of KPIs. Team members, managers, and stakeholders can access the same set of data, facilitating open discussions and aligning goals. Furthermore, dashboards cultivate a sense of accountability as KPIs are clearly visible to all, driving a culture of responsibility and ownership.

So now you know why you want one, where do you begin? Well, if you’re in one of the many _many_ organisations that haven’t yet, you need to first define your KPIs. This is not a task to take light hearted. It can and will break your organisation if you chose the wrong KPIs.

## Defining relevant KPIs
An engineering dashboard is only as effective as the KPIs it tracks. The process of defining and selecting the right KPIs is a critical foundation for a successful dashboard (and company).

The success of your engineering dashboard hinges on the relevance and significance of the KPIs you choose to track. KPIs should directly reflect your team’s objectives, providing insights into the areas that matter most for achieving project success, team efficiency, and continuous improvement.

Below are a few high level steps for your consideration. There have been whole books written on the subject of defining KPIs, and I won’t even pretend to be an expert in the matter, so take this section in the spirit it was written: to get you thinking about some of the steps you could take to write effective KPIs.

**Step 1: Understand Your Objectives:**
Begin by clearly defining the objectives of your teams. Are you focusing on improving code quality, enhancing deployment frequency, optimising bug resolution time, or boosting team collaboration? How do these objectives fit into the overarching company KPIs? Understanding your objectives will guide the selection of KPIs that align with these goals. Do you want objectives for each cross-functional team? (yes) Do you want overarching objectives for the whole of engineering? (probably). 

**Step 2: Identify Actionable Metrics:**
Choose KPIs that are actionable and can drive meaningful changes. These are metrics that, when tracked, can trigger specific actions or decisions. For example, tracking code review turnaround time can lead to process improvements that enhance code quality.

**Step 3: Balance Lead and Lag Indicators:**
Lead indicators are predictive in nature, offering insights into future outcomes. Lag indicators, on the other hand, reflect historical performance. A well-rounded engineering dashboard includes a mix of both types to provide a comprehensive view of your team’s trajectory.

Examples of lag metrics:
- number of defects that have reached production
- revenue
- profit
- customer retention rate
- customer satisfaction score

Examples of lead metrics:
- website traffic
- social media engagement
- conversion rates

**Step 4: Consider the Agile Manifesto Principles:**
If your engineering team follows Agile methodologies, consider KPIs that align with Agile principles, such as customer satisfaction, working software, collaboration, and responding to change.

**Common KPIs for Engineering Dashboards:**
- **Code Quality Metrics:** Include metrics like code churn, cyclomatic complexity, and code coverage to assess the health of your codebase.
- **Deployment and Release Metrics:** Track deployment frequency, lead time, and successful deployment rates to ensure efficient releases.
- **Bug and Issue Metrics:** Monitor bug trends, resolution time, and customer-reported issues to gauge product stability and customer satisfaction.
- **Team Efficiency Metrics:** Measure team velocity, sprint burndown, and cycle time to assess team productivity and performance.

**Customising KPIs to Your Team’s Context:**
Every engineering team is unique, with its own set of goals and challenges. Therefore, tailor the selection of KPIs to match your team’s specific context and priorities. Keep in mind that KPIs should provide actionable insights that foster continuous improvement and contribute to the overall success of your projects.

As you embark on the journey of building your engineering dashboard, remember that the KPIs you choose to track will shape the narrative of your team’s performance. By carefully selecting KPIs that align with your objectives, you set the stage for a dashboard that empowers your team with data-driven insights and fuels your pursuit of excellence.

With a clear understanding of the KPIs you want to track, the next step in building your engineering dashboard is selecting the appropriate dashboard platform. 

## Choosing the Right Dashboard Platform
The right platform not only enables seamless integration of data sources but also empowers you to visualise KPIs effectively. But how do you decide which platform is the one for you and your team?

**Consider Your Data Sources:**
Before diving into platform options, assess the variety of data sources your engineering team relies on. These sources might include version control systems, issue trackers, continuous integration tools, project management platforms, analytics platforms and more. A suitable dashboard platform should have the capability to integrate with these sources to provide a comprehensive view of your KPIs. 

**Balancing Off-the-Shelf vs. Custom Solutions:**
As with many solutions, a dashboard platform comes in two flavours: off-the-shelf and custom-built. Off-the-shelf platforms, such as Grafana and Tableau, offer pre-built templates and integration options that expedite setup. Custom solutions, built using frameworks like D3.js, grant you complete control over customisation and tailored functionality.

**Integration Capabilities:**
Choose a dashboard platform that seamlessly integrates with your data sources. Look for integration plugins, APIs, or connectors that facilitate data extraction and synchronisation. The ability to fetch real-time data directly from your sources ensures that your dashboard remains up-to-date and relevant.

**Customisation and Visualisation:**
The effectiveness of an engineering dashboard heavily relies on its ability to visualise data in a meaningful manner. It’s not worth much if it doesn’t visualise data in the way you want it to. Consider a platform that offers a wide range of exciting visualisation options, such as line charts, bar graphs, pie charts, and heat maps. Customisation features, like colour schemes and layout options, allow you to tailor the dashboard’s appearance to match your team’s preferences.

**Ease of Use and Learning Curve:**
The dashboard platform should be user-friendly and accessible to both technical and non-technical team members. A steep learning curve might hinder adoption and result in underutilisation of the dashboard’s capabilities. There’s nothing worse than spending days/weeks creating a useful tool for your company for it to be ignored or overlooked as it’s too complex. Prioritise platforms with intuitive interfaces and straightforward configuration processes. This needs to be considered in any homemade solutions. 

**Scalability and Performance:**
As your engineering team grows and the volume of data increases, the dashboard needs to scale without compromising performance. Look for platforms that offer optimised data handling and responsive performance, even when dealing with extensive datasets. 

**Community and Support:**
Opt for a dashboard platform that boasts an active and engaged community. Because when it breaks (and it will break), it’s nice to know that someone else has already solved your issue and posted about it online. A vibrant community ensures a wealth of resources, including tutorials, documentation, plugins, and troubleshooting assistance. 

**Budget and Cost Considerations:**
Both off-the-shelf and custom solutions come with associated costs. Evaluate your budget and weigh the benefits of each option. While off-the-shelf solutions might have licensing fees, custom solutions require development resources and maintenance.

**Security and Data Privacy:**
Ensure that the dashboard platform prioritises security and data privacy. Whether you’re hosting the dashboard internally or using a cloud-based solution, data security should be paramount. Encryption, access controls, and authentication mechanisms are critical considerations.

So you’ve selected a dashboard, but how do you feed it? A dashboard will starve and be relegated to the scrap heap unless you feed it the right data to make it useful. 

## Data Collection and Integration
The steps to integrate data into your dashboard are heavily dependent on the source of the data and your selected dashboard. However, they all follow a similar process:

**Step 1: Identifying Data Sources:**
We generate a lot of data in Engineering, from version control repositories and issue trackers to continuous integration pipelines and project management tools. Begin by identifying the sources that house the KPIs you’ve chosen to monitor. This might include Git repositories, JIRA, Jenkins, Slack, and other platforms your team relies on.

**Step 2: Extracting and Transforming Data:**
Data rarely comes in a neatly packaged format ready for visualisation. It often requires extraction, transformation, and sometimes cleansing to make it suitable for dashboard presentation. Use data connectors, APIs, or plugins provided by your chosen dashboard platform to extract data in real-time and prepare it for visualisation. You may need to build an ETL pipeline to support your dashboard. 

**Step 3: Integration with the Dashboard Platform:**
Your dashboard platform is the canvas on which your insights will come to life. Integrate the data sources you’ve identified with the dashboard platform to create a seamless flow of data. This integration ensures that your dashboard reflects the most current state of your engineering metrics, enabling real-time decision-making.

**Step 4: Maintaining Data Integrity:**
Data integrity is paramount. Ensure that the data presented on your dashboard is accurate, consistent, and up-to-date. Regularly validate data sources and connections to prevent discrepancies and inaccuracies that could lead to misguided decisions. Once the data is in the dashboard, sense check it with the source. Make sure you’re seeing what you expect. If you’re too close to it, get another set of eyes on the data!

**Step 5: Enabling Real-Time Updates:**
One of the hallmarks of an effective engineering dashboard is the ability to provide real-time updates. Configure your data sources and dashboard platform to enable automatic data refreshes at predefined intervals. Real-time updates empower your team to respond promptly to changes and emerging trends. Please don’t manually push the data into the system in the hope you will automate that in the future. It won’t happen as your team will get frustrated with the lag in the data and eventually you will get frustrated with having to manually push the data. To help ensure adoption, make the process as pain free as possible. 

**Step 6: Configuring Widget Types:**
Different types of widgets are suited for different types of data. Choose widget types that effectively represent your KPIs. For example:
- Line charts for tracking trends over time.
- Bar graphs for comparing metrics across categories.
- Pie charts for illustrating proportions.
- Gauge charts for visualising progress towards a goal.

**Step 7: Visualising Cross-Source Insights:**
The beauty of an engineering dashboard lies in its ability to consolidate data from various sources into a single, unified view. Leverage your dashboard platform’s visualisation tools to create comprehensive views that combine code quality metrics, deployment frequency, team efficiency, and more. Are there any data points that become more valuable when combined? For example, is there a correlation between deployment frequency and daily active users (DAU)? (But be careful not to assume causation!).

**Step 8: Ensuring Data Security:**
While data integration is essential, data security cannot be compromised. Protect sensitive engineering metrics by implementing encryption, access controls, and authentication mechanisms. Ensure that only authorised team members have access to the dashboard and its underlying data sources.

## Team Collaboration and Visibility
An effective engineering dashboard goes beyond providing data—it serves as a catalyst for collaboration, aligning goals, and enhancing team communication. But for this to happen, you need to embed the dashboard in existing processes. During meetings, stand-ups, or retrospectives, team members can refer to the dashboard to inform discussions, share insights, and identify areas for improvement. It serves as a visual representation of your team’s alignment with broader organisational goals. When team members can see how their work contributes to overarching objectives, they are motivated to work collaboratively towards shared success. A well-designed engineering dashboard promotes transparency by providing a comprehensive view of your team’s progress and performance. It fosters a culture of accountability, as team members can easily track their contributions and the impact of their efforts. The dashboard becomes a common ground for data-driven discussions. 

The dashboard serves as a neutral platform for discussing performance metrics. Instead of relying on anecdotes or assumptions, discussions are grounded in real-time data that facilitates accurate and objective assessments. When decisions are supported by data, their impact is more profound. The dashboard equips your team with the insights needed to make informed decisions, minimising the risks associated with gut feelings or assumptions. When making decisions we need to balance opinion and data and a dashboard helps us do just that. 

Collaboration around the dashboard encourages the identification of trends and patterns that might have otherwise gone unnoticed. Team members can collectively analyse data to unearth insights that drive innovation and process optimisation. The dashboard serves as a bridge between different roles and functions within your team. Developers, QA engineers, project managers, and leadership can all gain valuable insights from the dashboard, promoting cross-functional collaboration.

Key takeaway: the dashboard is only useful if you make it so. Not only do you need to track the right metrics, select a suitable dashboard, setup a data pipeline to automatically push the right data, and make sure that data is visualised in a meaningful way; you also need to pull the team in by embedding the dashboard in your regular engineering processes. 

## Data Security and Privacy
Security is important. In fact, data security and privacy are non-negotiable when it comes to engineering dashboards  There are a number of security considerations when implementing any new tool that moves confidential data from point a to point b and provided access to that data to users who may not have had it initially. 

**Securing Dashboard Access:**
Control access to the dashboard by implementing strong authentication mechanisms. Require team members to use their credentials, and consider incorporating multi-factor authentication to add an extra layer of security.

**Role-Based Access Control:**
Different team members have varying levels of clearance to view specific metrics. Implement role-based access control, allowing you to assign permissions based on roles within your team. This prevents unauthorised access to sensitive data.

**Encryption of Data in Transit and Storage:**
Encrypt data both in transit and at rest. Ensure that data exchanged between the dashboard and data sources is encrypted using secure protocols. Similarly, data stored on the dashboard platform should be encrypted to prevent unauthorised access.

**Regular Security Audits:**
Conduct regular security audits to assess vulnerabilities and potential risks. Regular audits help identify security gaps and ensure that your dashboard remains protected against emerging threats.

**Data Anonymisation:**
Anonymise data whenever possible, especially when displaying sensitive metrics. This ensures that individual identities are protected while still providing valuable insights.

**Compliance with Data Protection Regulations:**
Depending on your region and industry, you might be subject to data protection regulations such as GDPR or COPPA. Ensure that your dashboard setup complies with relevant regulations and guidelines.

**Monitoring and Incident Response:**
Implement monitoring tools to detect unusual activities or breaches. Establish an incident response plan to address any security incidents promptly and minimise potential damages.

**Data Retention Policies:**
Define data retention policies that determine how long data is stored on the dashboard. Automatically delete or archive data that is no longer relevant to prevent unnecessary exposure.

**Secure Data Source Integration:**
Data sources can be potential entry points for security breaches. Ensure that data source integrations are secure and follow best practices for API security to prevent unauthorised access.

**Educating Team Members:**
Educate your team members about the importance of data security and their role in maintaining it. Provide guidelines on how to handle sensitive information and adhere to security protocols.

## Case study
In this section, we’ll take a deep dive into a real-world case study that illustrates how FizzleTech, a technology startup, successfully implemented an engineering dashboard to optimise their development processes and enhance team collaboration. 

Note: ‘FizzleTech’ is not actually the companies real name. There a company I worked with many years ago and am no longer in touch with, so I didn’t want to air their internal tech without permission. 

**Background:**
FizzleTech, a London-based startup specialising in mobile applications, faced the challenge of efficiently managing their growing team and projects. With an expanding portfolio and a need for continuous innovation, they sought a solution that would provide real-time insights into their engineering performance and streamline decision-making.

**Goals and Objectives:**
FizzleTech‘s primary objectives for implementing an engineering dashboard were to:
- Enhance visibility: Gain a real-time view of project progress, code quality, and deployment cycles.
- Improve collaboration: Promote cross-functional collaboration by providing a central hub for data-driven discussions.
- Drive data-driven decisions: Empower team members with actionable insights for better decision-making.

**Dashboard Setup:**
FizzleTech chose to implement an engineering dashboard using a custom solution built on top of D3.js. This approach allowed them to tailor the dashboard’s design, widgets, and data sources to their specific needs.

**Metrics:**
FizzleTech’s engineering dashboard featured a range of widgets tailored to their development processes:
- A sprint progress tracker displayed the status of ongoing projects.
- A code quality heatmap showcased areas of the codebase requiring attention.
- A deployment frequency graph provided insights into release cycles.
- A user engagement widget integrated with customer feedback data to gauge user satisfaction.

**Results and Benefits:**
- **Enhanced Project Oversight:** The dashboard provided real-time project visibility, enabling FizzleTech‘s leadership to identify bottlenecks and allocate resources effectively.
- **Cross-Functional Collaboration:** The transparency offered by the dashboard fostered collaboration between developers, QA engineers, and product managers, leading to more streamlined workflows.
- **Informed Decision-Making:** Data-backed insights guided FizzleTech‘s decision-making process, helping them prioritise features and address critical issues swiftly.
- **Empowered Team Ownership:** Team members took ownership of their contributions, empowered by the dashboard’s visibility into their work’s impact on overall project goals.

**Continued Evolution:**
As FizzleTech grew, so did their dashboard’s capabilities. They integrated advanced analytics from Mixpanel to show changes in key metrics (retention, monetisation) after key releases. 

## Final thoughts
ChatGPT would conclude this post like so:
“As we reach the conclusion of our comprehensive guide on building engineering dashboards, we’ve explored the critical elements that contribute to their effectiveness, from understanding the need for data insights to the successful implementation of these tools. Engineering dashboards are not mere displays of data; they are powerful instruments that empower teams to navigate the complexities of development, make informed decisions, and achieve excellence.”

And it’s not far off, although I would remove the word ‘comprehensive’. However, to be fair, we have covered quite a bit, including:
- The importance of engineering dashboards in centralising data, enhancing transparency, and driving accountability.
- A high level process for defining relevant KPIs and metrics that align with both team and business objectives.
- Choosing the right dashboard platform, integrating data sources, and ensuring data security.
- The significance of real-time data updates and automation in providing timely insights.
- How engineering dashboards promote collaboration, alignment, and data-driven decision-making.
- Ensuring data security and privacy while maintaining the utility of the dashboard.
- A real-world case study showcasing the successful implementation of an engineering dashboard at FizzleTech.

The journey of building an engineering dashboard is one of transformation—a transformation from siloed data to collective insights, from manual tracking to real-time updates, and from isolated decision-making to data-driven collaboration.

I hope this post has accomplished the one thing it set out to do by encouraging you to consider building an engineering dashboard.  

As always, thank you for reading 🙂