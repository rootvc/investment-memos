# Superconductive

## Team
[Abe Gong](https://www.linkedin.com/in/abe-gong-8a77034/), CEO
* Technical CEO, data science background
* OSS author & contributor
* PhD in Complex Systems from U. Mich, B.S. BYU
* Author of the very relevant term “pipeline debt”: https://medium.com/@expectgreatdata/down-with-pipeline-debt-introducing-great-expectations-862ddc46782a

[Ben Castleton](https://www.linkedin.com/in/ben-castleton-ab393b3/), Co-founder
* Technical management and data eng/analyst background
* B.S. BYU

## Overview
I first met Abe Gong in May 2019 through my friend and Abe’s former coworker at Jawbone, Brian Wilt, who is currently at Facebook, after declining a job offer at Teespring (long story.) Abe has been thinking through ideas of how to build a business around his fast growing Open Source project, [Great Expectations](https://github.com/great-expectations/great_expectations). After brainstorming and exploring several different models with me of the course of the year, Abe and his cofounder Ben decided to found a company based on the Open Source Project and raise venture funding.

Great Expectations (GE) is a library for testing data. Much like Jasmine, JUnit, Rspec, or the built-in testing frameworks for iOS, Go, etc. GE provides an API for making assertions that: pass when code works as specified, and fails when it doesn’t. IN the world of software engineering, software tests are used for: 1) preventing bugs before code is submitted for review/release, 2) detecting problems during build/integration (continuous integration - CI), 3) replacing or augmenting quality assurance review (QA), 4) acting as a gate for deployment (continuous deployment - CD) a somewhat niche but passionate technique called test-driven development (TDD) or behavior-driven development (BDD) - N.B. this was a movement that Pivotal was at the forefront of when I was there, and I’m still a believer.

GE looks to provide these capabilities to data engineers, where data quality is often a root cause of production bugs (and hence PagerDuty wakeup calls for everyone.) GE expectations also solve an additional set of problems: 1) data cleaning and data wrangling (the process a data scientist goes through to format data properly for their specific applications), 2) data provenance (seeing a piece of data and answering the question - where did this come from, and how do I know it’s accurate?). These are among the largest concerns of data scientists, but there is very little software out there trying to solve it.

## Tech
The Great Expectations OSS project is written in Python and provides a command line tool that can be executed natively in Pandas, SQL, and Spark. This allows expectations to run up and down the data pipeline, from data “at rest” to data “in motion.” Near-term roadmap will ensure that expectations can be run anywhere that data is or can be.

Some more context on these initial use cases:

In the process of manipulating data with Pandas, data engineers can use GE to validate that data meets a spec before: e.g. training a model, drawing a data visualization, or exporting to a report, catching errors in the data before the data is used for some critical or sensitive purpose. This could be: catching a bug in the code, a faulty sensor, a problem with the data infrastructure, a bad query that misunderstood the measurement units of the data, model drift, or an accurate but important change in the nature of the data set such as a demographic change or change in user behavior.

Spark integrations (and those for other distributed map-reduce platforms) similarly can use GE at the point of integration of data. In map-reduce, a large set of data is “mapped” - taken one record at a time and operated on before “reducing”, or recombining, into an output format. Some form of map-reduce is used in almost all useful data transformation algorithms (though not all are at the scale of requiring distributed map-reduce like Spark.) A simple example would be taking a collection of users and grabbing their ages (map) and calculating the average as output (reduce.) Data validation in this example could be to make sure that ages are between 0 and 120, or that the average age stays within a reasonable distribution of expected ages (e.g. centered on 22-35 for TV viewers,) or further for COPA compliance (that <13 year olds are excluded or flagged.)

With the GE SQL integration, users can enforce the same constraints at the level of pulling data from a database, or at each step along the way of transforming data in an ETL pipeline.

## Product
Today, GE is an open source product, but there is a lot of value created by the ability to enforce assertions about data that could eventually provide a path to monetization. As an early seed deal, there is not a lot of validation on specific monetization strategies, but there are plenty of preliminary answers to this question.

The SaaS platform on top of Great Expectations will integrate with data sources (databases, document stores, logs) and data flows (ETL jobs, DAGs) and surface information about failures in data integrity. Users can connect these failures to actions, like stopping a build or deployment, alerting via Pager Duty, blocking a commit merge, or simply failing a local test suite. Additionally, the platform could infer its own constraints, and reason about what transformations are there. It should be able to detect anomalies in data using those inferences, and simple statistics (such as a sensor reading being >2 standard deviations outside the mean) and create its own expectations. There are a number of ways to use a product like this.

Some answers from the list under ”User Value” [here](https://github.com/great-expectations/great_expectations#why-would-i-use-great-expectations).
* Integrations with ETL tools (possibly with hosted first or third party ETL alongside)
* Spec/API Document generation
* Collaboration tooling
* CI/CD
* Production alerting systems
* Regulatory enforcement (GDPR, COPA, HIPPA)

It’s unlikely all of these will be first party (or any of them) to begin with - 3rd party integrations are more likely valuable as GE seeks adoption.

Additionally some common business models for this kind of product:
* Pay for hosting
* Pay for enterprise support and on-prem
* Pay once size of data exceeds certain amount
* Open Source / Closed Core + subscription or per-seat license
* Alerting services

Great Expectations will always remain Open Source, but we believe that if significant value is created for a company, there are things they will want to pay for, that they expect will cost money as an enterprise user. Therefore, the primary focus will be on finding product-market fit and product led growth for quite some time, maybe years. If Great Expectations creates enough value, there will be many possible paths to capturing revenue from enterprise customers.

## Market
There are maybe 11.4-19.4k data scientists globally, with 55% in the U.S. (6.25-10.67k) with an average U.S. salary of $120k. This means the U.S. spends about $12-15B annually on data scientists salaries. One would assume the number of people doing data analysis, defined broadly, is significantly higher.

There is a common saying in data engineering that data cleaning and wrangling is 80% of the job. Not to take that entirely too literally, but...that makes it look like the U.S. may be spending $9-12B on data cleaning and $2-3B on data science per year.

## Competition / Related Companies
There isn’t much. GE is not continuous integration (CircleCI, Jenkins, Travis, Cloudbees), version control (GitHub, DVC), DAG/ETL management (Luigi, Airflow), or alerting (PagerDuty.) GE’s success depends on a new category creation for data integrity. This need is well-known, but while software engineers may be familiar with automated test solutions, data scientists and analysts may not be. Some of these companies (i.e. Toro Data, Transform) have met with Abe, and neither views the other as competitive right now. They may in fact partner. But it's worth mentioning here, I think, because you could imagine some overlap in functionality in  the future.

A company called Data|Gravity is early and working on something similar. (Not to be confused with 2012 startup DataGravity from Nashua, NH that was acquired 2 years ago by HyTrust.)

Monte Carlo was founded this year, backed by Accel, and is going after data quality as well. They are pre-launch, and do not appear to be producing any Open Source software so far.

Another stealth company called Toro Data by former Uber employees who diligence very well with my Uber friends is working in a related, possibly competitive space.

A team from Airbnb is starting something in a similar space called Transform. They are pre-product, pre-seed, but the plan is to essentially make a single source of truth for every business metric in the company. Abe does not view this as competitive, but it also depends where this pre-product company goes.

Other companies come up during diligence as competitive if they work in ETL, data pipelines, data versioning. Superconductive looks to partner rather than compete with these companies in the near future. For comparison, CircleCI works with versioning like GitHub, deployment tools like Chef/Puppet, server configuration tools like Docker, and testing tools like Jasmine/RSpec. The analogy applies here I think.

Competing against apathy: One of my initial points of skepticism was that data scientists and analysts would not be amenable to changing how they work, but Abe has so far demonstrated the opposite - that data analysts are hungry for tools that mature their practice and increase their productivity/reduce their pain and friction, in the same way software engineers are. Abe is uniquely positioned to evangelize the power of data testing and become the obvious choice for solving this problem. I don’t think any of the above companies come close.

## Revenue
Consulting services - we are not ascribing much strategic value to this consulting revenue, but it is a channel to acquire a very small set of heavily invested customers to help get feedback on the product

Platform - None to date. Revenue plan will be to monetize the services built on top of GE - paid hosting, paid on-prem with support, paid subscription access to services. Additional products like compliance (HIPPA, COPA, GDPR) are possible long-term revenue streams, but are likely not quite focused enough for the early days.

## Funding
Abe has self-funded development of GE through his consulting agency that provides data integrity and data provenance to healthcare companies.

_(details redacted)_

## Diligence Calls
### Brian Wilt, former Head of Data at Jawbone, current Sr Manager, Decision Science at FB
Brian is one the best data leaders I know, I gave him an offer at Teespring that he sadly declined, we’ve stayed close
* He was Abe’s manager at Jawbone
* Abe Gong comes highly recommended by Brian - he made the intro
* Abe worked on the widely deployed, high throughput data systems at Jawbone
* Recall the Jawbone report where they used Jawbone data to detect an earthquake had happened (via everyone waking up at the same time in Napa/Sonoma)
* Brian says the gap between need for this service and capability of existing tools is large

### VPE at major AI-driven tech company
* “This looks useful. We should try this.”
* Did a bit more diligence and will be trying at work
* Believes this space is big and necessary - “there will be a winner”

### VPE at major AI-driven tech company
* They will build their own bespoke solution to this with their - and this is a direct quote - “comically large pile of dragon gold coins.”
* I view this as a “large companies can build this themselves, which demonstrates the need, and the high cost of internal development” type of answer.

### Root portfolio CEO
* In consulting for major government agencies and research institutions - they saw the problem space as a large and valuable one
* Company will want to be a customer of the OSS solution - to track lineage of the data in their data marketplace. Says it’s unclear if the paid platform would be necessary for their needs.

### Founder of a data startup in the BI space
* In an unrelated conversation, without me ever mentioning Abe or Great Expectations, they said that they were going to use Great Expectations alongside an open source data version control solution like DVC.
* I asked why GE, and they said it was the only solution that integrates with other services as a software library (as opposed to Data Gravity which is essentially a closed web platform)

### Data engineer at well-known unicorn
* Tried to start this company with his friend awhile back
* Sales top-down is very hard, and they failed
* Uses Data Gravity at current company, and says it’s a great product
* Had not heard of GE, but checked it out and likes it
* Sees the platform at Data Gravity as the main value - thinks GE would need to build that to compete
* Thinks OSS go to market is hard
* (Basically thinks both sales and developer growth are hard - he’s right haha)
