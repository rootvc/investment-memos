# Investment Memo for Esper (fka Shoonya)
Investment: Root Ventures (Kane) led the Seed round in February 2018 (with Lee participating as an angel investor, before he joined Root.) Root also co-led a subsequent Seed extension, and participated in the Series A and Series B.

_Note: A big part of Shoonya's pitch at the time involved providing low-cost hardware. In the first year, it became apparent that most customers wanted "bring your own device," and were primarily interested in Shoonya's software. This precipitated a change in focus and startegy from bundling hardware, OS, and cloud services, into providing pure software. Accordingly, Yadhu became CEO, and the company strategy shifted. More on that story in Avidan's tweetstorm here._

## Company
Esper provides secure managed embedded/thin (ie single-application) Google-certified Android. It also provides mobile device management (MDM), over-the-air updates (OTA) of applications and OS, one-click-provisioning, business analytics, and turnkey hardware. Esper allows enterprise customers to rapidly deploy Android apps on hardware endpoints without having to manage a hardware supply chain, OS-level security, or over-the-air updates of their devices.

## Founding Team
CEO [Shiv Sundar](https://www.linkedin.com/in/sundarashiv/)
-   Huawei (Director ‐ Global Business Strategy)
-   Cyanogen (Head of OEM Partnerships)
-   Samsung (Senior PM ‐ Mobile)
-   Microsoft (PM ‐ Mobile Partnerships)
-   BT, Electrical Engineering, Motilal Nehru NIT
-   MS, Electrical Engineering, USC.

CTO [Yadhu Gopalan](https://www.linkedin.com/in/yadhu-gopalan-5065164/)
-   Microsoft (Technical lead, Windows CE Kernel)
-   Amazon (Technical lead, Amazon Fire OS, Amazon Go, AWS HW fleet engineer)
-   MS, EE, Auburn
-   BS, EE, University of Maine

## Competitors
Since the unprecedented rise of Android as an embedded/thin OS, there have been a few products developed for Android MDM:
-   [Android Things](https://developer.android.com/things/index.html) - AT is Google’s first-party solution for managing embedded Android. It is primarily focused on original device manufacturers (ODMs) who want a way to manage Android OTA updates for their products:
-   It was originally an internal project for Google devices, before being made available to the public due to a deluge of low-end Android TVs “polluting” the Android ecosystem
-   It recently saw a resurgence due increased interest in smart devices running Google Assistant
-   Only reference system-on-chip (SOCs) are supported, with no turnkey offerings; this implies the user will build custom hardware around SOCs
-   MDM, reporting, and analytics are sparse and only allow users to manage different product groups, rather than individual devices or user-defined groups by business logic
-   OTA flashes entire OS; cannot update applications alone
-   Device provisioning is managed by a software engineer
-   [Mason](http://bymason.com) - Y-Combinator-backed (2015) embedded Android MDM company run by former Cyanogen employees. Mason has not publicly raised money since 2015, but closed a $3M round last year on $300K ARR. Unlike Android Things, Mason provides turnkey and ODM solutions, and allows device-level management based on business-logic-definitions. Like Android Things, OTA updates to client devices require an entire OS update. It is unclear how well maintained the OS is.
-   Knox/MobileIron/etc - MDM products for corporate BYOD. These products create a secure partition on a consumer Android phone or tablet. While this sandboxes select applications and data, these MDM products operate at the application level and cannot ensure OS security. These MDM products are also designed to operate alongside consumer apps, and are expensive because they are priced as white-collar corporate SaaS.
-   Vertical-specific cos eg. Zebra, NCR. - there are legacy companies that ship embedded devices for specific industry verticals. While they lack MDM sophistication, they have sticky channels and long sales histories.
-   Custom - for those that have no other choice, custom embedded Android systems exist. Engineers work with ODMs to integrate Android for custom devices, and then have to rework the OS for their hardware every time Google updates Android. Expensive. Painful. The new Square POS uses custom embedded Android.

![](/images/esper1.png)

## Considerations
Within the embedded/thin Android market, Esper only really competes with Mason because of Android Things’ focus on the custom hardware/ODM market for the reasons stated above. However, there are a few reasons to believe that there might be competition from Android Things in the future:
-   It appears that AT may be building partnerships with other SOC vendors (Qualcomm recently [posted a job](https://www.theladders.com/job/software-engineer-iot-qualcomm-santa-clara-ca_35848739) specifically naming Android Things). This might only be intended to broaden chip support for Google Assistant devices, and nothing has been publicly announced.
-   Google recently hired [Injong Rhee](https://www.reuters.com/article/us-alphabet-cloud/google-hires-former-samsung-executive-to-coordinate-internet-of-things-projects-idUSKBN1FX0CQ), Samsung’s former CTO, to run its IoT business. Rhee was involved in a lot of projects, including Samsung Knox, its BYOD MDM product.

However, there is also an opportunity for Esper to take some of the custom hardware market away from Android Things - ironically, because of recent changes in core Android. “Treble” was a major re-architecting of hardware abstraction in Android 8.0:

![](/images/esper2.png)![](/images/esper3.png)

If Esper was founded prior to Treble, it would have to work with ODMs to customize its OS in order to offer turnkey hardware. Esper would have to re-work the OS for its turnkey hardware every time Google updated Android (what every custom Android device maker currently has to do, and why so few Android devices - phones included - are updated). While Esper might be able to sustainably support a few turnkey devices, it would be very difficult to scale hardware support because it would have to maintain an operating system variant with every new piece of customer hardware. Its market would be limited to users of its turnkey offerings, or it would have the inventory risk/unfavorable economics of an ODM in order to support more customers.

The Esper team waited until Treble was finished to found the company. The Esper OS, built on Treble, will ship with two turnkey offerings (phone and tablet), but more importantly, it can be licensed and deployed on any Android 8.0+ device. This means that Esper can compete with Android Things to support customers that build custom hardware (ie, the customers only license Esper OS and MDM and manage their own hardware supply chain). Furthermore, Esper can offer these customers features beyond AT (eg. business logic, device-level management, in-place application updating, one-click provisioning, etc). With Treble, Esper’s economics are more analogous to a true SaaS business than an ODM.

Treble also gives Esper an advantage over its closer feature-competitor, Mason. Mason was founded between releases of Android 5.0 and 6.0. Like Esper, its turnkey solutions have to be maintained in-house. However, unlike Esper, it is burdened by supporting legacy OSes for customers who utilized their ODM offerings between 2015 and the release of Android 8.0 at the end of 2017. The founder, Jim Xiao, came well referenced but is a solo founder and is not technical.

The TAM for Esper is embedded OS devices that are either app-driven or have a display. Where power constraints, absolute performance, or exotic hardware is used, real-time Linux will remain the OS of choice. Otherwise, Android’s portability, rapid bring-up time, standardized APIs and SDK, UI frameworks, and breadth of out-of-box driver support make it a natural embedded OS.

More than a million Android devices are activated a day, with embedded Android devices seeing 26% YoY growth. Within some industries such as material handling, Android accounts for almost 100% of new embedded devices shipped. The growth of embedded Android will not only manifest in new embedded devices, but also in the cannibalization of market share from tens of millions of aging Windows Thin Client, Windows Embedded, Windows CE, and (some) Linux systems. Windows CE is nearing end-of-life, leaving OEMs scrambling to upgrade tens of millions of embedded devices and opening a huge opportunity for Esper where the TAM is at least all Windows CE devices. Embedded Android is growing fastest in areas where Windows has generally outperformed Linux, including “automotive infotainment, medical devices, military handhelds, and to a lesser extent, retail and signage.”

While Esper faces some potential near-term threats as well as advantages over Android Things and Mason, there are two long term opportunities Esper has penciled out which could significantly differentiate it. The first is operating as an mobile virtual network operator (MVNO); all embedded/thin clients require reliable, cheap, and secure connectivity. Offering Esper data plans as an MVNO meshes neatly with its existing value propositions of deployment convenience and security, while conveniently adding high-margin recurring revenue. The second differentiator is CTO Yadhu’s extensive, highly relevant personal network in Windows CE, Android MDM, and hardware fleet management. Given the impending opportunity in Windows CE end-of-life and the explosive growth of embedded device deployments, we believe that Yadhu senior management and IC experience with both Windows CE and Android MDM at Amazon allows him to recruit top talent in a way that his competitors can’t.

Even setting aside the fact that Android Things is primarily ODM focused and Mason is lacking the technical sophistication of Esper, it’s hard to imagine the sheer growth of embedded Android captured by a winner-take-all MDM; the use cases are too varied. Verticals and opportunities will emerge for Esper to exploit.

Growth of embedded devices:

![](/images/esper4.png)

## The Raise
Root will be joined by Haystack, Ubiquity, Pathbreaker, several great angel investors including Andrew Lee, and this one mediocre one named Lee Edwards.
