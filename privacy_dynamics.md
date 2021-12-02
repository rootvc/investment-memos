# Investment Memo for Privacy Dynamics

## Overview
Privacy Dynamics is a solution for data privacy through intelligent anonymization. A core belief of the company is that enforcing data privacy inside a company should make doing the right thing easy to do, and never produce friction. The reality, whether or not we like it, is that users of data and decision makers on privacy are often at odds, causing friction and disobedience when it comes to privacy policies. We see over and over again, that engineers and analysts/data scientists will repeatedly choose convenience over privacy, and engineers especially, will not tolerate any amount of friction. When alternatives to privacy software include hiring consultants to make the problem go away, doing manual data transformations, or simply not complying, the most successful software solutions will 1) provide reasonable defaults, 2) be transparent and frictionless, 3) be configurable and usable by the employees who are intrinsically motivated - data privacy teams, security, CPOs, and potentially legal.

## Team
Graham Thompson, founder & CEO
* Microsoft, Legal and Corporate Affairs
* Former ME
* BS MechE and MBA from UW and USF

## Product
[Demo Video](https://www.loom.com/share/0e61c217b3834898814fe18641623f9b)

Right now, the product is a Snowflake plugin that makes it easy to select data for anonymization, redaction, and obfuscation on a database, table, or column level. The system then creates safe versions of these databases with the same schema, making pointing queries to the safe dataset easy. In simple cases, the user may want the system to provide realistic but random names, ages, doctor’s visit dates, or zip codes. But for almost any interesting use case, the ability to create statistically valid noise (changing this data while maintaining things like the median, or geographic clustering, or keeping the day of the week while randomizing the date, is the somewhat more annoying part.

Users can then see a [k-anonymization](https://en.wikipedia.org/wiki/K-anonymity#:~:text=The%20concept%20of%20k%2Danonymity,subjects%20of%20the%20data%20cannot) score of their cleaned data set. This concept is easily expanded to include other data warehouses, databases, and other forms of data stores and sources. Future roadmap clearly includes more integrations. Like many of our bets in the data space, I think there is a lot of long term value in customers’ internal SaaS data, such as that from ADP, Zendesk, Salesforce, or Stripe that a company may want to analyze for operational or business intelligence.)

## Technology
As data sets get larger (and particularly, wider,) this problem gets harder. The field of [differential privacy (DP)](https://en.wikipedia.org/wiki/Differential_privacy), which [came to prominence around 15 years ago](https://link.springer.com/chapter/10.1007%2F11681878_14), is full of challenges in getting this exactly right. [Despite best efforts](https://www.sciencemag.org/news/2019/01/can-set-equations-keep-us-census-data-private) to [implement state of the art differential privacy](https://www.census.gov/about/policies/privacy/statistical_safeguards.html), the 2020 US Census had a few cases of reidentification according to one of our sources (citation needed.) In any case, it is so challenging at this scale, that many [criticized the Census Bureau for even trying](https://www.sciencemag.org/news/2019/01/can-set-equations-keep-us-census-data-private).

To that end, a few Open Source and consortium based solutions to DP exist such as [OpenDP from Harvard](https://opendp.org/), and [Google’s own DP solution](https://developers.googleblog.com/2019/09/enabling-developers-and-organizations.html). Reading these sites, gives an idea of the complexity of these tools. Privacy Dynamics will seek to make reasonable defaults of these services available to product engineers solving bugs, entry-level BI analysts looking to answer simple questions, BD teams swapping data in a partnership, legal teams assessing risk, and compliance officers proving compliance. It will be able to do this using rules-based and ML-based approaches to decide e.g. which columns should be treated how, and if a Gaussian or Laplace thresholding algorithm works better with a particular dataset.

Deployed inside a customer’s data warehouse - VPC, or on-prem, Privacy Dynamics also seeks to simplify deployment of these algorithms and maintenance of these services.

## Trends
2 years ago, only 10% of the world was covered by localized data privacy regulations. In two more years, that number will be 65%. ([Gartner](https://www.gartner.com/en/newsroom/press-releases/2020-09-14-gartner-says-by-2023--65--of-the-world-s-population-w))

The macro trend for privacy is very clear at this point. Regulators all over the world are imposing stronger and stronger regulations. Even in the most politically divided governments, data privacy is a bipartisan issue, where for example, civil libertarians fear mass surveillance, big government advocates seek to exert more control - arguably to solidify their own monopoly on the data panopticon, more socialist-leaning movements fear powerful corporations, nationalist movements outside the U.S. dislike the American-centric tech industry, and politicians of every stripe can identify at least one personal grievance against Facebook, Google, Twitter, or Amazon.

Concretely, we have of course seen GDPR, CCPA, and PDP have rocked the way companies build applications, even though judgments so far have been small and far between. Every company has changed the way they handle customer data at least on the web, entire categories of companies have shut down or completely pivoted away from their core business. Much of the impact of these regulations is already in the pipeline, and will hit soon. [The Schrems lawsuit](https://epic.org/privacy/intl/schrems/) for example is 9 years in the making and has just concluded. All of the impact of privacy regulations that we see around us is still just a leading indicator of what is inevitable.

## Market
There are a few markets here and a few ways to think about them.

We know there exists a big market for buying data or data insights from companies that have the data. Insurance companies, banks, and advertising companies for starters. But even physical retail brands, DTC product companies, social media and consumer apps, and the USPS buy and sell customer data.

One insight gained from diligence is that there are fundamentally two different kinds of customers for data privacy. The extrinsically motivated and the intrinsically motivated. Even if you believe that enforcement of privacy laws will be light, then the extrinsically motivated market loses everyone too small to sue, but likely retains any company large enough to worry about the risk anyway - banking, insurance, F500, etc. But regardless, the segment of extrinsically motivated companies will include those that are very brand conscious, are in a space where privacy is part of the value prop to the customer (e.g. Epic,) or are positioned strategically with respect to privacy (e.g. Apple.)

Another way to think of the markets was presented by Alex Schultz. There are two uses for this product: 1 is data sharing, export, import, partnerships, third-party research. The other is internal data warehouse teams, which is mostly what I’ve talked about in this memo. But Alex believes I am underestimating the importance of the first. It’s possible that the business succeeds on $80/mo/seat of the latter. But while the number of companies that have valuable enough data to want to sell, share, offer for research, or otherwise monetize is small, 1) they need complex privacy, 2) it is growing very quickly, 3) the engagements are extremely high value and privacy is a primary objective directly in the value chain.

Yet a third way to think about this market is verticals. It’s unclear to me until Privacy Dynamics starts selling, where they will be most attractive. Companies saddled with compliance issues is one obvious path, such as healthcare (HIPAA) or social media (COPA). Another is companies just at the stage of growth where basic data privacy practices start to become necessary - maybe these are growing tech-first companies where deriving value from the data is second nature, and introducing compliance has been avoided because it will increase friction. This latter set of companies would derive value from Privacy Dynamics through a more subtle sales pitch that they can continue to be a data empowered culture while still running best practices by default.

I think the best way to discover which kinds of customers on these axes are the best fit for Privacy Dynamics is to get in front of as many of them as possible and try to understand them. Snowflake’s plugin partners program [currently contains no privacy plugins](https://www.snowflake.com/partners/technology-partners/?_sf_s=privacy). That’s going to change. If Privacy Dynamics gets there first, I think that fills their entire pilot customer cohort in the first month.

## Competitors
[Renee Shah at Amplify has a great thread about this space](https://twitter.com/reneeshah123/status/1384172897531416578). A few notables that came up in convos:

Gretel
* A large number of dataset operations like “remove bias in dataset” and “anonymize data”

Skyflow
* API for querying your data and getting private responses

DataGrail
* Workflow for data mapping, data subject requests, 

BigID
* Discovery, indexing, mapping, asset ownership, data breach search
* Demo here: https://vimeo.com/256377756

Tonic.ai
* Synthetic data focus
* Two uses cases: scaling AI, and data anonymization

Very Good Security
* Consultant model

We’ve seen a few of these folks (and others) in this space, and many of these fall into a few buckets:
1. Data transformation service, of which *very basic* anonymization is one feature
1. Compliance project management and checklists, access management
1. Data mapping
1. Process automation
1. Synthetic data

More importantly, the big competitor here is apathy. Some teams don’t care about data privacy. My thesis, which Graham shares, is that if data privacy were the intelligent default, everyone would do it, providing it added no friction.

## Fundraise
Past
* $(redacted), various
* $(redacted) from our friends at Geometry

Now
* Seeking $3.5M (_Hindsight note: oversubscribed and blew past this target._ 😄)

## Diligence
_heavily redacted for privacy_ (hah!)

Eng Manager on ML at health company
* Generally hates SV startups
* ...but liked this one
* Company generally chooses to cut corners, especially engineers
* Have implementing privacy by default on the roadmap but never prioritized - clear case of buy over build here
* Rarely consider evaluating startup services, but wants an intro to Graham to evaluate
* Recommended reading by Cynthia Dwork of MSFT/Harvard [paper](https://link.springer.com/chapter/10.1007/11787006_1)
* Left excited

Two-for-one: Friend at unnamed healthcare company + his former manager at another company
* Opened my pitch by describing DP
* “Sounds like overkill, even for us”
* (redacted) started caring a lot more about privacy 2-3 years ago, before that, nobody really cared about privacy
* Most customer data privacy use cases are solved by having people sign contracts, trusting them, firing bad actors
* Doesn’t believe this can be done automatically (if it could, it might be interesting, but he doesn’t think it’s really possible)
* (Awesome! If Graham can pull this off, it will look like magic)

Experienced executive at large company dealing with large amounts of sensitive data, angel investor
* First reaction, when I simply said it was SaaS for privacy: nobody will pay for privacy
* Second reaction, once I said this was an implementation of anonymization for the masses: “this is a necessary product” - “concept is a good concept”
* Importance of statistical noise, very very bullish on DP
* Company evaluated vendors (contractors) for this a few years ago and was ahead of the curve - built products internally on this
* Main value: companies that want to give data away (or sell it)
* “Bigger than you think” - e.g. Netflix data challenge, all healthcare, all social, 
* Secondary value: the data warehouse
* “When I invested in (current decacorn) and (past decacorn exit), I told the founders now is the right time to do this. I feel the same way about this idea right now.”
* Data privacy will be seen as a human right, rightly
* “The real growth in the importance of data privacy is hidden, due to long lead time of these cases.”
* Privacy Shield reversal, BA fine, FB fine, Schrems, India - all point to everyone needing to care about this, much more than they even think they do now.
* “Everyone? Even small startups?” “Yes, everyone.”
* Wants to invest (Love that. Let's make it happen either way.)

Head of Data at important devtools company
* Yahoo! Did this a long time ago - FireEagle (Tom Coates) in 2007
* FireEagle was ahead of its time - it predated mobile and the proliferation of private data everywhere. It focused primarily on securing users’ geo data. And again. This was before the mobile phone.
* Great idea, too early.
* Is now the time?

General Counsel at large software infrastructure company
* Main thing he wants is a dashboard where he can see datasets that engineers and analysts are using and understand a privacy report for that data
“This does that!”
* Must be on-prem or co-resident with Snowflake
* Who has liability? He expects any significant problem would get litigated, but admitted that’s true of any kind of fine at all for any reason
* Liability question wouldn’t block a sale from happening here

PM at fintech unicorn
* Immediately loved this
* They use Very Good Security (VGS), which has some basic filters using regexes, not enough

Director of Product at media company
* Many potential customers in streaming media, one exception:
* Disney would never be a customer - they own this themselves with an internal “data governance army”
* Would you use it? - “depends what they charge”
* Intrinsic motivation = brand risk
* VPPA is even more serious than HIPAA (had to google this - regs for looking at people’s online video viewing, passed by possibly some creepy porn addict senator in the 90’s/00’s - is literally stricter than HIPAA, and dealt with by all video providers. 
* Insistent “Engineers DO care about privacy”
* Its just that some of these regs are stupid, like VPPA. They take the important ones seriously.
* Very sensitive info like email address is always upstream - there’s no reason you’d query it
* “This is the right workflow for everyday data privacy.”

Personal reference calls all went well and weren’t super substantive. Leaving out notes for now.
