# Meroxa Deal Memo
  
Demo: https://drive.google.com/file/d/1JqkWaOmU_urNSKFGfqMHbmREQMgsirj9/view

_Note: very old demo!_

Investment: Root Ventures (Lee Edwards) led the Seed round that closed July 17, 2020, and participated in the Series A.

## Team
### [DeVaris Brown, CEO](https://www.linkedin.com/in/devarispbrown/)
* Director of PM (DX), Heroku
* Previously: Microsoft
* Floodgate Academy and General Assembly instructor

### [Ali Hamidi, CTO](https://www.linkedin.com/in/ahamidi/)
* Senior engineer, data products at Heroku

Overall, the team diligences extremely well, and after many phone calls, I leave with the impression that DeVaris is a tenacious and eager founder on top of everything else.

## Overview
Meroxa provides a simple Heroku-like API that provisions data services and manages their scaling, access control, and environment. More interestingly, the cli tool can create connections between source data stores and destinations - Kafka-backed data streams that capture change data and insert these deltas into a destination store. This pattern can completely replace traditional ETLs in a data infrastructure, and are more scalable, flexible, and (generally) performant than a traditional ETL architecture. It also provides access to data streams, which can be broadly useful to a product and organization.

These streams are more broadly useful than data archiving. Streaming architecture has become popular in recent years, as evidenced by the surge in growth of Confluent ($4.5B private valuation April 2020,) which sells software and support services for Kafka, a popular component of event streaming architecture. Data streams can be used in a pub-sub architecture (using e.g. PubNub, privately valued at a few $100M at Series D) to allow applications and services to be aware of data flowing through an organization and react accordingly. In the world of businesses shifting from the BI of data dashboards and lagging indicators to one that is more present and realtime, data streams are the enabling technology for “closing the loop” - acting on data by feeding it back into the system to adjust behavior. They can also be critical to machine learning models, especially related to training and redeployment.

Today all the pieces for this kind of modern data architecture exist, but they require configuration, connection, and long term maintenance. They also tend to be multi-cloud, and many key services exist outside of the primary cloud platforms (AWS, GCP, and Azure.) Companies like MongoDB ($MDB, $11B market cap), Snowflake (seeking >$20B IPO shortly,) Terradata ($TDC, $2.3B market cap,) DataDog ($DDOG, $22B market cap,) and ElasticSearch ($ESTC, $6.5B market cap) live outside of, but must be configured and integrated with, a company’s primary VPC and related services.

On top of that, the fastest growing segment of a company’s data infrastructure, and possibly the least well-used for internal data streams, data lakes, and warehouses, is third-party enterprise application data, which includes services like Salesforce, Zendesk, Atlassian, NetSuite, and Stripe, all key operational sources of truth for an organization, as well as products like Lever/Greenhouse/SmartRecruiter, ADP, and Zenefits which enable data-driven approaches to HR, and all kinds of up and coming internal products and services like LatticeHQ, Airtable, Notion, or even a company’s Twitter, HubSpot, and Google Analytics for marketing analytics and automation.

No service today really wraps that class of services as well as internal data sources and destinations. We see companies like Mulesoft (exit $CRM for $6.5B) and Zapier ($35MM ARR) working on connecting products via the APIs that those services provide, and companies like UIPath ($7B valuation) and Automation Anywhere ($6.8B valuation) integrating them at the UI level. Neither are focused on connecting these services to internal sources and stores of data, and neither are creating data streams that are accessible to engineering and data science/analytics teams inside a company.

## Product & Technology
Demo: https://drive.google.com/file/d/1JqkWaOmU_urNSKFGfqMHbmREQMgsirj9/view

Part of the Meroxa technology is the suite of connectors to data sources and destinations, which include things like application databases, data warehouses, document stores, and streams, as well as third-party SaaS application sources like Stripe Connect or Netsuite, and destinations like Slack or SMS via Twilio. This part of the products feels like a sort of Mulesoft that works at the data level rather than the API level, and ends up building value for the customer based on the number of integrations and level of support for difficult integration points, as Plaid and Stripe do.

Another part is the PaaS, which makes it easy to build a data infrastructure. It also gives Meroxa something of a moat for customers, since they do own those services an the data in them. Yet another way to think about Meroxa is as Mulesoft but for SQL stores and 3rd party SaaS apps instead of APIs.

With so many components to this product, one challenge Meroxa will have in the early days is identifying the highest value use case and focusing on that customer segment. Do you sell this as an EDW? An alternative to managed Kafka? A replacement for ETLs? A staff augmentation for data engineering teams? A number of pilot customers exist, but this question won't be answered with confidence until it's been tested further.

In terms of defensibility, it’s fair to say this is not a protected IP-driven business. If Meroxa is to create a moat, I believe it has a few avenues, none of which are admittedly as strong as protected core IP.

In developer tools, as in enterprise software and consumer products, sometimes the best usability, and the best tracking to customer needs wins in a crowded market. I believe DeVaris’ background as Director of Developer Experience at a company known for being best in class at DX or “developer ergonomics,” sets him apart. The demo, and the diligence, so far confirms this in my mind.

Managing integrations across platforms is tedious work with a lot of upkeep. We have seen a number of companies that don’t have IP per se, but who have done the complex work quickly, and built a good business on top of that - Stripe, Twilio, Zapier, and Plaid come to mind immediately.

Meroxa owns the database management. Which is not to say they own the data. They don’t, in the sense that they will certainly sign privacy agreements with customers, but they own where the data lives, and especially as service expansion happens, migration becomes difficult and expensive. In some sense, Meroxa is the ultimate system of record for a company, as enterprise data warehouses are the source of truth for auditable data for all aspects of a business (with the notable exception of financial data, which often has its own finance data warehouse for SEC compliance - a problem for another thesis and deal memo - haha.)

## Traction
Meroxa is very early, but has a handful of unpaid pilot customers, mostly friends of the founders.

## Market
The Data Engineering Services market is predicted to be worth around $77B by 2023. There are clearly public market comps for data engineering services companies, and comps for hosted data stores (MongoDB, Snowflake,) services (Confluent, Cloudera, Elastic) and PaaS (Heroku Pivotal, Hashicorp.)

A few examples exist of companies whose technology is integrations with multiple complex backing services - Twilio, Stripe, Plaid, Mulesoft, OneLogin.

## Go-to-Market
Adam Gross and Jason Warner suggest Heroku Marketplace is one place worth trying to distribute Meroxa. Billed there as a data services product that builds a data warehouse, there could be good adoption among Heroku’s 100Ms of active users, which would give them some users to provide guidance on what parts of the roadmap are important.

Very quickly, Meroxa will become an enterprise sales company targeting mid-size companies - those large enough to have enough data to care about, but at least initially, Fortune 1000 may not be a good target, as they tend not to work with PaaS vendors like Heroku. (Note that there is potential change here in the future, see: Hashicorp's and Pivotal's client lists. The main blocker in the early days is the distraction of building large enterprise focused products and services for customers like this.)

This mid-sized company customer segment is going to require a sales org. Neither founder has direct experience building and running an inside sales team, but we've seen many technical founding teams learn this skill and/or hire for it.

## Monetization
We have observed that margins on cloud compute for a PaaS vendor built on top of AWS usually end up around 50%, whereas for data services, margins can be closer to 90% if managed well.

One path exists for Meroxa to simply charge the user a premium on top of their own hosting costs. This price might be anchored against the cost to build, host, and maintain data services internally, which would include hiring more data engineers. Other possible paths exist. Certainly on the high end, there is a strong argument for value-based pricing.

## Competitors
Fivetran offers a very similar promise and is well-funded and further along. Meroxa’s approach is different from a developer experience perspective. DeVaris and Ali draw heavy inspiration from Heroku and are building a CLI-first product with a focus on developer ergonomics. Fivetran is focused on ETL tools, which run asynchronously, and do not create data streams internally. Many similar ETL tools/comapnies exist.

StreamSets deals with the stream part of this product, but not the source/destination provisioning and management.

Things like Mulesoft and Zapier are built to connect services that have APIs, and don’t do much with internal data sources and destinations, or data that isn’t exposed via an API

## Financing
Existing pre-seed investors include top devtools operator/executives as angels. - Great people around the table.

_financing details redacted_

## Diligence
_Heavily edited, some removed, as some of this looks the way 360-feedback looks - pros and cons. I shared all the feedback, good and areas of improvement, with DeVaris after investing._

### Head of Data at _major cloud infra company_, former CTO _major software company_
* "I have built this before at several companies and would pay money to not have to do that next time."

### Engineering Manager at _major pre-IPO tech company_, formerly _well-known startup with huge, valuable data set_
* "Everyone has built this a million times, it sucks, and they would pay to have it built for them."

### CEO at _Root portfolio company_
* "This is really interesting!"
* "I have built this before at several companies and would pay money to not have to do that next time."

### _Executive formerly in direct line with DeVaris_
* Huge fan of DeVaris
* Opportunity is real, needed

### _Former CEO, major cloud infra company_
* “We tried to build this internally, but it lost priority“
* Something like this will exist, there will be a winner

### _Big tech executive, mentor to DeVaris_
* Mentoring DeVaris for awhile
* Big believer in the idea, and the long term largest vision of “the data lake with data tributaries” lol the data as water anaologies never stop

### _DeVaris' former direct manager_
* DeVaris has a strong business sense
* Willing to challenge executives up to the CEO
* High performer, demands high performance around him
* Often brings DeVaris in to close deals with technical customers
