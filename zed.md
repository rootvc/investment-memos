# Zed

Pitch memo (Redacted: Zed had a pitch memo rather than a pitch deck!)
[Demo Video](https://www.loom.com/share/d165fd054a294d8a8587807bcc50c885) very old demo!

## Summary
Zed is a text editor or IDE (integrated development environment) for developers designed with speed and collaboration as the primary considerations. Today’s most popular IDE is Microsoft’s VSCode, which came out of nowhere in November 2015 to now hold 51% market share, a dark horse particularly among web developers who had never been fans of its predecessor, Visual Studio. VSCode is mainly beloved for its ease of use, extensibility, and broad polyglot support owed to its innovative Language Server Protocol system which allows language developers to ship plugins that run in their own threads, doing things like syntax highlighting and real-time error checking. VSCode is also feature rich, shipping a steady stream of lots of nice features like allowing you to edit files on a remote SSH server seamlessly within your local copy of VSCode, and a fully featured built-in terminal.

But all this comes at a cost, VSCode is slow, often painfully slow, even on small projects. Given that it is built using web technologies in Electron, the performance ceiling seems already hit. It’s pretty silly that $4k MacBook Pros have a hard time running VSCode, Slack, and Chrome at the same time.

Further, VSCode hasn’t done much to innovate on what an editor could do if you re-imagined it. Repl.it is a web-based editor that *has* innovated on real-time collaboration features for teams, but it hasn't seen much adoption inside of companies yet, where those collaboration features would shine. There is still plenty of opportunity to be the first highly performance, real-time, collaborative text editor.

## Team
**Nathan Sobo**: Nathan joined GitHub in late 2011 to build the [Atom text editor](https://en.wikipedia.org/wiki/Atom_(text_editor)), and led the Atom team until 2018. He also co-led development of [Teletype for Atom](https://blog.atom.io/2017/11/15/code-together-in-real-time-with-teletype-for-atom.html), pioneering one of the first production uses of conflict-free replicated data types for collaborative text editing. Prior to GitHub, he was an early employee at [Pivotal Labs](https://en.wikipedia.org/wiki/Pivotal_Labs) (😄) and directed engineering at an education startup called Grockit. He’s been dreaming about building the world’s best text editor since he graduated from college, and is excited to finally have the knowledge, tools, and resources to achieve this vision.

**Max Brunsfeld**: Max joined the Atom team in 2013 after working at Pivotal Labs (👋). While driving Atom towards its 1.0 launch during the day, Max spent nights and weekends building [Tree Sitter](https://tree-sitter.github.io/tree-sitter/), a blazing-fast and expressive incremental parsing framework that currently powers all code analysis at GitHub. Tree Sitter has 4.3k GitHub stars and [was recently featured at the top of Hacker News](https://news.ycombinator.com/item?id=26225298). Max currently leads GitHub’s semantic analysis team.

**Antonio Scandurr**: Antonio joined the Atom team in 2014 while still in university after his outstanding open source contributions caught the attention of the team. He later joined Nathan in architecting Teletype for Atom and researching the foundations of what has turned into Zed. For the last two years, he’s become an expert in distributed systems and conflict-free replicated data types through the development of a real-time distributed, conflict-free database implemented in Rust for [Ditto](https://ditto.live).

## Product
Today, this is the very basic [Demo](https://www.loom.com/share/d165fd054a294d8a8587807bcc50c885). It’s essentially prototype-level of readiness, not even quite ready for dogfooding. The team estimates that milestone is 10 months out.

Is speed enough of a differentiator to build a new text editor? Maybe. Superhuman has so far showed there is at least some segment of professionals who spend several hours a day in their email inbox who are willing to pay $30/mo. to use the Superhuman client. Originally, it was marketed heavily as a speed-up, both in terms of performance and usability (these go hand in hand.) It was never clear to me as a user that Gmail was slow until I used Superhuman, and now I can't go back. Slowly, [they rolled out more features by studying what this pro segment of users wanted](https://review.firstround.com/how-superhuman-built-an-engine-to-find-product-market-fit), with [frequent releases](https://new.superhuman.com/?utm_medium=widget), ignoring many features they viewed as either unnecessary or not “for” this power user segment. So while speed may not be the only feature, it may be a very good one to start with.

Collaboration and remote work: The jury is still out for most industries on what remote work will look like post-pandemic, but the software engineering industry has built tooling for remote programming arguably since ssh and tmux, and the first multi-user version control dates back to the 1970's. Most companies will at least support remote work, or multiple offices for engineers - as they mostly have even before the pandemic.

But even though our work is highly collaboraive, our text editors are all single player. How can a text editor enable the kind of experience you have when you call a coworker over to your desk to help you with some code? Or at the extremes, support remote pair programming? GitHub enables collaboration between developers, but not in realtime. A GitHub code review involves one person making what is essentially a pre-release candidate, fully baked, and asking for asynchronous review. It is asynchrous, lumpy, collaboration. Today, only repl.it is really working on this Figma-like multiplayer experience for developers.

The UX design of this product is key. For example, how should video chat work as a collaboration feature? Do you link out to Zoom? Integrate [Daily](https://daily.co) above the user’s cursor like Pitch (a “Superhuman for Powerpoint”,) or allow ad hoc room creation like Screen Hero did? Getting these details right will be the difference between an NPS of 6 and an NPS of 9. Nathan is deep thinker on the user experience of the text editor. To say he's a philosopher on the subject is not an exaggeration.

## Technology
Zed is built on Rust for thread safety, performance, portability, and GPU acceleration. This is an uncommon choice, but clearly the right one for this project.

It also uses a client side UI framework today called GPUI that allows the team to build applications quickly.

## Market & Competitors
[Stack Overflow Survey on Text Editors and IDEs](https://insights.stackoverflow.com/survey/2019#technology-_-most-popular-development-environments)

This market feels like the worst possible market:
* Highly fragmented - 22 players that have 0.2% or more market share
* But still has an elephant, VSCode, which has 51% market share
* And most of the products are free
* Strong moats in existing players through strong affinity, e.g. “editor holy wars”

**But** I still believe there is opportunity. 😂 A quick overview of the landscape. (Note: I edited a lot of these to remove what I view as their weaknesses, because I don't want to talk smack. I love and respect all your projects, folks. Really.)

A free product, **VSCode** is part of Microsoft’s overall strategy to become the #1 name among developers. Microsoft also owns the #2 IDE **Visual Studio** at 31% (note that most developers use more than one text editor or IDE, so these numbers don’t add to 100.) These products can probably be considered a loss leader for Microsoft, but they are very actively developed and the team is quite innovative...and they are free and benefit from distribution and an ecosystem effect.

**Vim** is the most popular OSS text editor today at 25% usage. It has been around since the 80’s, and is really the hard mode of text editors. But it is fully customizable, and free/OSS. (This was my favorite editor for a decade or more.)

__Notepad++__ is a free and OSS text editor supported by ads on the website, and donations, but is Windows only. It is often compared to GitHub’s Atom (also Microsoft!, but no longer developed,) which supports every OS and is about 13% market share.

**Repl.it** is a well-known web-based IDE. It started as a sort of runnable code-snippet app, and pivoted into aiming to be a serious tool for development. It’s Bloomberg Beta backed, pretty well liked, and innovative.

**Glitch** is Joel Spolsky’s web-based product, that wants to be even more than an IDE. It wants to host and serve your application, and be a marketplace for apps. But I agree with Joel’s husband, that Glitch refuses to brand itself as a professional tool, hamstringing its own ability to grow. It raised money on Joel’s star power, but the new CEO is a terrible manager, and doesn’t seem to even desire to build a business. The few people that do pay for Glitch pay for hosting. I expect that Netlify will subsume Glitch for this use case.

I don’t believe that web-based editors will dominate the market. In fact, I’m pretty bearish. Today, they are not widely used, and I don’t think many people want that, even though several options exist. [Scientific Twitter poll](https://twitter.com/terronk/status/1364806451231748106?s=20). I think these web-based IDE companies are building with web technologies, because that enables easy collaboration. But native desktop can do all that, without sacrificing performance to the chromium process, and meets the developer where they want to be to interact with code - on their own computer.

**IntelliJ IDEA** is the ground-breaking IDE that really set that bar, back in the late 90’s. IntelliJ has a lot of knowledge of the Java programming language, and is able to do things like syntax highlighting and errors/warnings, which at the time was novel. Rob Mee at Pivotal told me that bringing IntelliJ to their first client (Google) made them look like geniuses, and all the Google engineers quickly adopted the IDE to make their lives writing Java boilerplate a lot easier. IntelliJ’s parent co, JetBrains, now makes editors built on the IntelliJ engine like RubyMine, GoLand, and PyCharm. JetBrains has also begun building a suite of other products around their editor suite, like Space, a project management tool.

This is a pretty sizeable business. [JetBrains reportedly](https://news.ycombinator.com/item?id=21796793) has $270M revenue on 6M users and 405k paying customers, 33% growth and $100M net income and $134M FCF...with $0 raised over 20 years. ($666 ARPU if you count only paying customers, which suggests many people pay for more than one product - each product costs $499 for a company, $149 for an individual.)

**Can you make money selling a text editor?**

Well, JetBrains suggests you can, but I’d also suggest so does Superhuman. If people who spend 8 hours in their inbox are willing to spend $30/mo for a superior experience to the free version, the same should be true for people who spend 8 hours a day in their text editor.

There’s also a strategy to expand from the editor to other tools as well, such as the CLI. Multiple VC-backed startups exist in the CLI space.

## Fundraise
Nathan isn’t exactly fundraising right now, but had inbound interest, so he asked Pivotal CEO Rob Mee for help, and he sent Nathan my way.

I think we should offer him (redacted) on (redacted) postmoney cap and bring in some complementary angels or small funds.

## Diligence
(simplified a bit, lol)

CTO at a previous company
* Big fan

CEO/Founder of a previous company
* Big fan

One of my best former coworkers, now a Director at GitHub
* “I would bet on him to build the future”
* “Nathan is a legit genius”
