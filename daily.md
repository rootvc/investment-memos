# Investment Memo for Daily
## Background
Root Ventures originally invested in Daily when it was called Pluot, and coming out of YC. Pluot provided a hardware enterprise video conferencing platform, and later an enterprise software service for video. In mid-2019, Kwin told us about some early customers of a pure API product, and we felt like there was something worth investing in here, both from insiders and potentially new outside capital. In order to make the decision to invest in the new direction, we decided our practice should be to write a new deal memo as if this were an existing investment. In other words, prospective investors saw Daily’s pitch as an API company. If we were to see that pitch for the first time, would we invest? This was a bit easier for me (Lee,) as I joined Root after the initial Daily investment.

## Overview
[Daily](https://daily.co) had previously built a hardware product for enterprise video conferencing, and then a software-as-a-service solution for enterprise video calling which competed with WebEx, Zoom, etc. These large competitors have continued to grow, but a few months ago, Daily began selling the video chat backend as a service via API to a few customers who asked for this. Daily has a small handful of notable customers so far.

## Team
We know the Daily team well, through our previous investment in 2017, when the company was a hardware-focused teleconferencing business called Pluot, graduating from YC.

CEO Kwindla Kramer previously founded [Oblong](https://oblong.com), which raised over $100M after it spun out of the Media Lab.

## Tech
Daily’s API is built on [WebRTC](https://webrtc.org/), an open standard and protocol created and supported by Apple, Google, Microsoft, and Mozilla. WebRTC is powerful, and well-supported, but my diligence calls with engineering and product leaders at a number of early, growth, and late stage tech startups and public companies suggest that building a good product on top of WebRTC is harder than it seems. In fact, rather than do it internally, Slack paid millions to acquire Screenhero, whose integration also ended up being over budget and behind schedule. Daily has demonstrated that even with a small team, they can execute better and faster than many of these companies who are trying to build on top of WebRTC for themselves internally.

Daily’s tech extends or builds on top of WebRTC video rendering, using server-side technology to focus on the video conferencing use case of WebRTC. Daily’s servers provide video buffering, graceful degradation, latency detection, compression, and optimization on top of client-side WebRTC for rendering and communication layer. This server-side optimization is part of what makes for the wide variance in call quality across video call providers you have used.

The choice for developers will be between using lower level WebRTC APIs and building conferencing features and optimization on top of the open protocol, or paying to use Daily and integrate in minutes, while still having access to lower level protocols for any domain-specific customization they may need. Sustained engineering costs will be reduced to zero (whereas for example, Slack has a standing team,) and the last 20% of quality (see for example, the difference in quality and reliability between Skype and Zoom) will be solved.

## Product
The Daily product is a client-side API that can be invoked with a few lines of code, similar to Stripe, Twilio, or Elastic Search, combined with a web-based platform for management, customization, metrics, and insights. The intended user for all of these features is the software development and product teams. No specific knowledge of WebRTC or specialized skills in video/audio are required.

Daily allows for customization of the UI in and around the video, including white labeling and branding. A number of Daily’s customers, in fact, talk and create content around the quality of their video (which is in fact powered entirely by Daily,) but the integration is so seamless, the customer never knows. Contrast this to an application that linked out to a Zoom video., forcing the user to switch context, be exposed to Zoom’s branding, and potentially download an app.

Video is a core and necessary technology for all of these customers, and they choose to use Daily. Each Daily customer’s offering is a UI on top of and around video communication; their differentiation is the custom user experience built on top of this video. This is in some ways analogous to how e-commerce companies have moved to Stripe and Shopify, even though their main revenue stream is digital payments, because it allows focus on their real differentiation - the physical products they sell.

## Market
Daily’s business is a bet on the proliferation of real-time video communication in the future. The why-now is clear: constant connectivity and increased bandwidth has quickly created user expectation of high quality video. People are using FaceTime to communicate, and are using work product with video every day: Slack, Google Hangouts, Zoom, and some people are betting on products like Tandem for real-time remote work, and Loom for sharing asynchronous video artifacts. Even TurboTax and Intercom are integrating video to meet the consumer expectation of face to face communication. Telemedicine is a growing industry, that medical experts predict will continue to grow - driven by changes in insurance policies to optimize costs, DTC medical products like Romans/Hims and SmileDirect/Candid, and the cannabis industry.

## Competition
TokBox
* Owned by Vonage
* Formerly OpenTok
* Name doesn’t come up often
* OpenTok community doesn’t much exist anymore

Twilio Video
* Twilio has a Video API that generates about $15M/yr in revenue with a small team based out of Eastern Europe
* Somewhat neglected - team is not growing, perhaps shrinking
* Based on diligence, not a core focus for Twilio. It builds on IP connectivity, not telecomm, which is where Twilio’s natural expansion is

Zoom?
*  Will Zoom video add an API at some point in the future?
* Probably - but they may focus the API on adding value to the existing Zoom platform, rather than helping developers build software _off-platform_
* Zoom has a best in class enterprise go to market motion, but no develop motion to speak of

Agora
* Large, multi-$B company
* Quite complicated API (think Braintree vs. Stripe)
* Privacy, HIPAA concerns, given presence in China, tech built on Chinese cloud providers

Mux
* Multi-way video broadcast API
* Can co-exist with Daily easily
* Multi-way broadcast good for e.g. the next Twitch, the next creator-focused social media platforms like TikTok
* Not the ideal technology for peer-to-peer or small group video conversations

## Revenue
For the API: Small to date, as this business line is three months old. 

## Diligence Calls
Engineer at Slack
* Slack bought ScreenHero to solve video on the platform
* Integration was hard, expensive, buggy, took twice as long as planned
* Video isn’t well-used on Slack right now
* Lots of users just pointing to Zoom links in chat
* Slack happy to push this off to plugin providers
* If they built it first party, it would be buy > build

former engineer at Intercom
* Intercom has a few video plugins (turns out Daily is one!)
* If they were doing video natively, they’d buy rather than build for sure

Early startup engineer
* tl;dr If they end up doing video natively, they’ll buy rather than build

former Twilio engineer
* Twilio video API makes around $15M/yr
* Supported by ~5 engineers in Europe
* Initial launch was bad, product offering not good, pricing bad - PM replaced
* Not a huge focus area, but thinks Twilio has a leg up on everything they do
* Though in theory he thinks someone could out execute them
* Online learning has been a big customer

Current pilot customer
* “Our video works 80% of the time on modern browsers. We are very good at writing software. We know the last 20% of reliability will be very, very hard. I suspect this is the on-ramp to what Kwin has built: folks who stub their toes then go looking for a solution.”
* Loves Daily API
* Evaluated Twilio Video API, but:
* No low-level API access: we basically only want call setup, stream management, and eventing—their API makes it hard to built the UI/UX we want
* No server-side access: we want to be able to capture the raw streams, live, on our server and apply some processing to create more value for users

## Other reading
https://www.uctoday.com/unified-communications/cpaas/twilio-and-vonage-lead-cloud-comms-apis/

https://www.twilio.com/video

https://www.vonage.com/business/api/

https://investors.twilio.com/all-news/press-release-details/2019/Twilio-Announces-Third-Quarter-2019-Results/default.aspx

## Funding
Root is looking to lead or participate in the next round of financing, which will fund the goal of achieving Series-A level revenue as quickly as possible.
