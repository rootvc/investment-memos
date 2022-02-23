Okteto Investment Memo
==
[Website](http://okteto.com)

_Some parts of this shamelessly stolen from Aashay's deal memo at Haystack, and deal memo is a bit lighter than usual, as I linked from time to time to Aashay's memo._


Overview
--
Okteto builds development environments that mirror production/staging with very little configuration on the part of the developer.

This may sound familiar. We’ve seen a few seed stage companies working on this problem, and Heroku has a feature like this called Review Apps. Like many of the companies we like, the focus is on making the developer experience better during the process of writing code, and before pushing code to CI or production. Okteto uses Kubernetes to create containerized deployments of simple to complex architectures.


Team
--
**CEO Ramiro Berrelleza**
- Previously a software architect at Atlassian, software engineer at ElasticBox, software engineer at Microsoft.
- Computer Science degree from Tecnológico de Monterrey

**CTO Pablo Chico de Guzman**
- Previously a postdoc research at IMDEA Software Institute, tech lead at Docker, software engineer at Tutum, software engineer at ElasticBox PhD,
- Master's, and Bachelor's from Universidad Politécnica de Madrid in Computer Science / Software Systems

**CPO Ramón Lamana**
- Previously a senior front end engineer at Google YouTube), front end engineer at Elasticbox
- Master's degrees from ENSIMAG and Université Joseph Fourier, Bachelor's in Computer Engineering from Universisdad Politécnica de Madrid

Ramiro is based in San Francisco, and Pablo & Ramón are based in Madrid. They worked together previously at Atlassian and ElasticBox.

Tech & Product
--
Okteto is a few things. It’s a web interface, maybe similar to Heroku, with each project/GitHub repo represented as a deployment. These deployments, however, are developer environments. Each developer could/should have their own.

Eventually, each pull request could have its own deployment. Like Heroku Review Apps, or the Netlify Deploy Button, Whenever a developer makes a PR, an environment can spin up for code review, QA, or PM/Design review. Deep links to this environment can be shared around an org e.g. via Slack so that developers, even remotely, can collaborate on a shared, per-developer, per-PR, environment.

Most importantly, Okteto is an integration with the developer’s local machine - through an IDE like VSCode, or with the command line, that allows the containers deployed by Okteto to act like services running on a local machine.

With Okteto:
- Engineers can deploy to personal and/or team localized development environments (e.g. for iterating quickly, for showing something to a teammate, for remote work, or for running tests)
- QA/PM can deploy to a staging server to test the functionality of a new feature/bug fix
- CI/CD can use the same deployment pipeline as dev/staging
- Products with on-prem support can use the same pipeline for deployment as the cloud-based tool
- Sales engineers can demo new features, and provide easy environments for sales reps
- SREs can debug production issues by tracing problems to single deployments
- IT or Finance can audit running instances - not just production, but all over the company


Market
--
Size: DevOps market: $2.5B, 15.5% CAGR [MarketWatch](https://www.marketwatch.com/press-release/devops-platform-market-size-to-grow-at-155-cagr-up-to-2024-2019-03-11) or 18.3% CAGR up to $15B by 2026 [Reports & Data](https://www.reportsanddata.com/report-detail/devops-market)

Some Comparables:
- Hashicorp: [$5B valuation](https://techcrunch.com/2020/03/16/hashicorp-soars-above-5b-valuation-in-new-175m-venture-round/?utm_source=Heavybit+Updates&utm_campaign=b10b4ed935-C+-+DevToolsDigest+-+3%2F25%2F20&utm_medium=email&utm_term=0_248ef1fc80-b10b4ed935-127045121&mc_cid=b10b4ed935&mc_eid=40abc336e1)
- Pivotal: [$2.7B acq. By VMware](https://www.forbes.com/sites/ilkerkoksal/2020/01/02/vmware-closes-27-billion-acquisition-of-pivotal-software/#709c737ce6ae)
- Runnable: small acq. by Mulesoft

There are 21M developers according to the most comprehensive Developer survey available, [Stack Overflow 2019](https://insights.stackoverflow.com/survey/2019). Gartner says there is demand for about 3M more developers than are trained today. Developers will need to get more efficient to meet demand.

In terms of growth, the same survey shows that only 8.6% of developers use Kubernetes, but that 76.8% want to. In the past, this has been a fantastic metric for technology growth, as developers often make their own tooling decisions and bring tooling business to companies. Budget for this is large due to developers being seen as revenue-generating.


Competition
--
- Perennial question: “Won’t AWS/GCP/Azure ‘just do this’?”
  - Let’s add Pivotal (PKS) and Hashicorp (Terraform) to this list of giants
  - These companies do “managed kubernetes.” They assume you use/understand kube, but need help hosting and tuning/configuring kubernetes clusters.
  - The cloud providers are single-cloud, and don’t deal with dev environments.
  - The Pivotal PKS and Hashicorp Terraform products are multi-cloud, but are also focused on production environments only.

- Heroku review apps, Netlify deploy button
  - similar product/DX, but only works with Heroku/Netlify, and does not orchestrate multiple apps/containers to replicate entire environments.
  - IMO proves the need for something similar but better and multi-cloud/multi-service

- Lots of seed-stage startups "doing kube for you"
  - There is fragmentation in the “we do Kubernetes for you” market
  - These companies are managed kube companies as well.
  - Distinction: Kubernetes is invisible under the hood for Okteto. It is an implementation detail where none of the concepts pierce the abstraction layer for the developer.
  - I believe that’s a good thing. It makes Okteto the “Heroku” to most Kube startups’ “AWS.” There is room in the market for both “expert tools” and “easy tools.”

Releaseapp.io, Coder.com, Env0
 - (notes heavily edited here for competitive reasons)
 - a few differences with some of these tools:
   - Coder is focused on being your all-in environment; Okteto is bring your own editor
   - Releaseapp is closer to something like managing your kube - helping you promote an environment from dev to stagint o prod
   - Env0 is very focused on infrastructure management

Rumored upcoming Hashicorp product
  - great, but if Okteto were for non-Hashi users only, it would still be a big enough market

Revenue
--
none/little

Fundraise
--
Okteto is raising a $2M seed round. They previously raised a $300K pre-seed with $150K from Y Combinator and the rest from friends and family.

Haystack has a signed TS with them at (redacted). The Okteto team prefers a small investor base, as well as investors with relevant experience in developer tools / cloud infrastructure. We would be seeking to put in half the round or slightly more.

Diligence
--
**Eng Manager at pre-IPO tech co, also formerly at well-known unicorn, infrastructure**
 - their team has this problem in spades
 - Built an internal tool
_one recurring thesis I have is any company that has massive resources building a major tool, where this is not their core competency (unlikely to commercialize) reveals an opportunity for the 99% of developers. eg: hosted git, CI, tailored for software project management tools_
 - Project was “very expensive” - in fact multiple large, expensive projects
 - the syncing, hot reloading, the web UI to see what services you’re running, autoscaling with usage, etc
 - lots of fiddly work, a million ways for things to go wrong
 - if something breaks N>=1 engineers are very blocked
 - Hosting costs expensive
 - Unlimited budget exists for this problem, because CEO adamant that company developers are revenue generating

**Founder/CTO of important devtools company**
 - Built own implementation
 - “Because nothing else existed yet”
 - This is a popular problem to try to solve

**CTO important devtools company, former CTO other important devtools company**
 - Loves the pitch
 - Lots of ideas on how to make this big
 - Interested in the idea of having permalinks to ephemeral environments
 - Easy to monetize and grow if billing is based on usage
 - Github button for deploy would be super popular, esp if low-config
 - Wants to talk to Ramiro to maybe invest

**Eng Manager at company founders worked at**
 - Important idea, most companies need it
 - Very large companies maybe will build in-house
 - Current company would do this if they could do kube config, or if Okteto would make it zero-config; they’ve been evaluating options in this space
 - Ramiro was well-liked at the company, coworkers had great reviews for him
