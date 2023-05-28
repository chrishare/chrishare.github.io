---
title: "Reflections on Log4J Security Issues"
excerpt_separator: "<!--more-->"
categories:
  - Security
tags:
  - Security
  - Open Source
---

The Java log4j 2 library is used in applications and appliances around the world to - funnily enough - log information that the application might want to record. Typically, that will mean writing a line to a log on the local filesystem with data about what a user did, or how the application is processing a request - but log4j supports a variety of complex record formats and output destinations, including output protocols like JMS and JDBC. Besides the ubiquity of Java, log4j is prominent because of its wide-ranging features, and that ubiquity is why the recent remote code execution vulnerability CVE-2021-44228 has impacted much of the IT industry. In this post, rather than look at the code flaw (I am not a security researcher), I want to look at the contention in commentary surrounding this issue in the week since it was revealed.

<!--more-->

## Background

On November 24, an Alibaba cloud-security researcher named Chen Zhaojun reported a serious flaw that had, unbeknownst to the world, long existed in some versions of the log4j 2 library that would, given the right log input and environment, allow an attacker to execute whatever code or script they like. An overview of the early report and investigation is given in this Bloomberg report (https://www.bloomberg.com/news/articles/2021-12-13/how-apache-raced-to-fix-a-potentially-disastrous-software-flaw). Later, and before a patch was ready, the flaw would go from limited awareness to common knowledge on the internet, at which point attackers were weaponizing the flaw and probing most of the internet domains and technologies for the weakness. In the week or so after the attack became common knowledge, multiple patches have been developed in response to the initial flaw and variants discovered since.

The global IT industry has not really been tested this way before. There was widespread commentary on the ability for open source to prevent and respond to these issues, about mono-culture in software, about transparency and authority during critical moments, and more. Let’s start with the debate about open source.

## Open Source: Equipped and Funded To Cope?

Log4J 2 is an opensource library developed by a small (in terms relative to its scale of deployment) team of, to my understanding, largely unpaid software engineers working in their free time, out of passion. https://logging.apache.org/log4j/2.x/team-list.html lists the core team. In addition, the core developer was receiving very little sponsorship for his effort in supporting this critical library.

This isn’t unusual. Critical internet infrastructure is often developed by passionate developers in their own time, as open source software, and then largely leveraged and taken for granted. See https://xkcd.com/2347/ and https://news.ycombinator.com/item?id=26449179 for commentary. It is a fortunate coincidence that open source developers are often some of the most skilled in our industry.

Is this a problem? I think so, but there seem to be no easy solutions. There is absolutely nothing wrong with people delivering and sharing value for free as a public good, but - rightly or wrongly - an expectation of pseudo-support comes with that. Specifically, many people have an expectation that the author(s) of an open source library will provide ongoing and timely support for problems with the library. People consume the library of capability as a black box, without understanding the code (who would have the time?) by instead relying on the authors. That reliance has been exposed here. The timeline does suggest to me that the initial fixes were slow to be delivered, and a lack of resources seemingly contributed to that.

To drive more investment - or, as some would say, fair compensation - there seems to be no alternative but to get funding. There are options here; licensing and charge-back models go against the intentions and beliefs of many open source developers, even when these are aimed at corporations. Corporate sponsorship seems to mostly succeed when the software in question is a crucial or ‘sexy’ element of its operation, as opposed to commodity infrastructure. Personal sponsorship seems to succeed solely based on the marketing abilities of the developer in question, and how sexy their software is - many excellent developers are underappreciated. There are success stories whereby corporations hire open source developers to work full-time on the projects that bring them to prominence, but this path is not common and not reliable, often coming after many years of unpaid toil.

In 2021, it is fair enough to say that there is no reliable path to financial stability as a full-time open source developer of library code, and no emerging options - particularly for core infrastructure like log4j.

It’s important to note that some developers do it without any desire for compensation. For instance, https://andrewducker.dreamwidth.org/4085856.html?thread=28352864#cmt28352864 is an illustration of this - but relying on passionate individuals alone certainly contributed to this problem.

If the log4j maintainers had been paid, full-time developers, would this have changed this problem? I doubt it would have prevented it, but certainly it might have improved responsiveness for getting fixes out and communicating the problem and workarounds. If at all the official communication from the log4j team on how the attack worked and could be avoided was lacking - you cannot really blame them, given they all likely had other software engineering responsibilities (in their minds, if not tasks to actually perform). For a security vulnerability of this nature, that is a bad, bad thing.

## Mono-culture

There have been RCE vulnerabilities before. One thing that is special this time, is the sheer breadth of software using this library. Typically, high levels of software reuse is an excellent thing, but there is no doubt that it has led to a bad outcome here. Let’s imagine that all software on the planet needs a logging library, and suppose there are two scenarios - in the first, there is exactly one library, and in the second, there are five with identical levels of developer support, and so on.

Which scenario fares better with regards to security vulnerabilities? In the mono-culture scenario, the software should theoretically be of higher quality, given the entire pool of developers, and testers (users) are all working against the one project - but the impact of a critical defect is huge, be it a security weakness or a feature defect. If we imagine that the level of code quality in the ‘competitor’ scenario with five libraries is the same, the likelihood of RCEs in each project is the same as in the single mono-culture scenario, but the impact and timing is spread. Putting aside security issues, the latter scenario with competition often yields the best features and innovation, through natural selection. However, it also dilutes any effort to fund the open source development efforts - given that licensing and support costs are a factor for competition (in a race to the bottom).

Overall, mono-culture in open source software is, I believe, largely a good thing, provided there is sufficient competition to drive innovation. Whilst the impact of issues at one given time is huge, the total overall impact should theoretically be slightly less. However, I think it is fair to say - when these critical libraries are supported by single-digit numbers of people - that appropriately staffing, testing and funding projects is a much bigger consideration than solution fragmentation.

## Communication

I think it is fair to say that communication about this issue lacked authority. While the Apache log4j 2 landing page (https://logging.apache.org/log4j/2.x/index.html) was updated with some security details as patches were released, that information was largely incomplete. The world would have benefited from central communication around the issue - how to mitigate it while waiting for a patch, how to detect the attack, and so on. There is a conflict here when there are security vulnerabilities - you don’t want to arm attackers with information that makes their job easier, but an information vacuum only serves to cause confusion, reduce confidence, and allow uninformed commentary. No doubt, some developers will have misunderstood whether or not they were impacted, and some will not have acted because they were confused. Clear instructions about what the issue was, how to identify impact and so on, would have helped here. However, for such a critical and complex issue and such a small maintainer team - you can hardly blame the people involved. During the period between the issue going viral and now, some security research firms (and companies) did share deep-dive information about how the issue worked and what mitigations there were - which is great, but an authoritative, central source of truth is better. Certainly that would help stop people taking advice from random people on Twitter.

Ideally, how should this work? Should some government-sponsored agency take responsibility? Which government, and when? What happens when this conflicts with state objectives?

One model I could see working is to convene a panel of public and private organizations that, while not normally contributing to the library code, do convene to support the core development team in assessing, managing and communicating in times of crisis - using official Apache communication channels. There is certainly incentive here for those organizations, even if those organizations don’t use the software in question - it’s excellent advertising, relatively low-cost (given it is typically not needed) and often helps their clients (in the case of cloud vendors).

## Summary

This issue is, in many ways, one of a kind - but sadly, many of the factors leading to it are difficult to solve. I can see events of this nature and impact happening more and more as software continues to eat the world. On a personal level, I can imagine it felt horrible when the developers involved learned about this. However, there is much we can learn and do to prevent future impact of world-scale issues like this - if we have the will as a community. Open source software is not going anywhere, so it is important that we set it up to succeed and not take it for granted.

Thoughts? Tell me what you think!