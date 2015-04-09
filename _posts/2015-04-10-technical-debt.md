---
layout: post
title: Technical Debt
sortorder: 2015-04-10
---

**The topic of technical debt in software development comes up regularly in blog posts, podcasts or talks. I am highlighting some of the practical experiences in trying to reduce technical debt.**

I am not going to define technical debt. There are lots of definitions and developers and management always seem to embrace the one that goes well with their specific situation.

In general technical debt describes something not desirable, although it is possible to spin this into a strategy. If a development team decides to have a deliberate debt to meet some goals, most probably a deadline, then this can be considered a strategy. At least one could say so afterward.

The best projects I have been in is when a development team has trust of managers and on the other side is acknowledging project constraints like deadlines or budget. Such a team will make compromises which will result in technical debt.

The problem with the deliberate approach is that most of the time there is no planning for reducing this debt. Writing more tests to improve coverage, code reviews, refactoring as such are seen by many managers as unproductive and lost time. That those managers brought the project into problems by nurturing unrealistic expectations by stakeholders is a different problem. More serious is that many project managers themselves don't understand the need for a reduction of technical debt.

Another cause to come into debt is lack of knowledge in the technical team. I can count the projects of the last 20 years on one hand that had an architecture or design document. Most did not even have requirements written down or only a few of them from a time when the project started. The other extreme was one project with a preparation phase of half a year. In that time requirements were logically checked, development and production environments defined, namespaces discussed, a team structure built and a few prototypes designed - not coded. The astonishing fact was that this project actually bought an architecture framework, so this part was no issue at all from the start. At least the development team could write code without incurring too much debt, because the managers were supporting the idea of testing and refactoring.

I think that the development paradigm does not really have a positive or negative impact on technical debt. Waterfall or agile or anything in between all want to deliver the best quality. Where projects fail are impatience and money; the impatience of stakeholders who want to see something and budgets that don't have enough contingency baked in to cater for unexpected situations.

The software industry does not really have an answer to the biggest problems I have encountered all my career since the 80s: measuring development time, measuring productivity, reacting to changing requirements or features, explaining the process to non-technical stakeholders, estimating development time and thus budgets.

In this context technical debt is a logical consequence of deficiencies in the development process. For developers, at least for me, it is also a fuzzy term. If technical debt means worse than optimal quality then we have to ask when this debt starts and what is *optimal quality*?

The code I write today can be written better tomorrow when I have more knowledge. Code quality changes over time with advances in computer science, availability of tested libraries or new designs of programming languages. In my opinion technical debt never goes away, because the measuring posts move.

We have an agile development approach established, even in organizations where one would not expect it. Developers are now more in charge of databases and environments than a decade ago. It would be nice if developers would be trusted  to achieve the best quality as possible and let them design and refactor their code as they see fit.
