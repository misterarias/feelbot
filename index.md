---
title       : feelBot
subtitle    : or a love&hate story
author      : Juan Arias
date        : 11-Nov-2016 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

<style>
em {
  font-style: italic;
}
strong {
    font-weight: bold;
}
.title-slide { 
  background:url(http://www.schibsted.com/Global/LogoTypes/SMG_Logo_Small_RGB.png);
  background-repeat: no-repeat;
  background-position: top left;
  background-size: 50%;
}
</style>


## What if ...



we could amend a software decision **before** it turns out being *uncomfortable*?


---


## What if ...

we could amend a software decision **before** it turns out being *uncomfortable*?

we could pilot a new feature by avoiding *all the humps* in the road?

---

## What if ...

we could amend a software decision **before** it turns out being *uncomfortable*?

we could pilot a new feature by avoiding *all the humps* in the road?

we could focus on *what really matters* to our end-users?

---

## What if ...

we could amend a software decision **before** it turns out being *uncomfortable*?

we could pilot a new feature by avoiding *all the humps* in the road?

we could focus on *what really matters* to our end-users?

we could get feedback & insight *for free*, in an *scalable* way?

--- 

## What if ...

we could amend a software decision **before** it turns out being *uncomfortable*?

we could pilot a new feature by avoiding *all the humps* in the road?

we could focus on *what really matters* to our end-users?

we could get feedback & insight *for free*, in an *scalable* way?


we can?

--- 

## Enter the feelBot

* Track a series of public Schibsted sources **in real-time**
* Look out for community feelings about our flagship products: 
    * Platform features, 
    * Rocket components, 
    * Infrastructure improvements, ...

--- 

## Enter the feelBot

* Track a series of public Schibsted sources **in real-time**
* Look out for community feelings about our flagship products: 
    * Platform features, 
    * Rocket components, 
    * Infrastructure improvements, ...
* Start with a few, complement that using *Machine Learning*.
    * Massive data processing will help nail the correct topics to be aware of.

---

## Enter the feelBot

Take **actions**, based on detected **reactions**:
- Positive: 
    - Time to rush up that workshop? 
    - Publish new features on-the-works?
    - Release it!!! Release it now !!!

---

## Enter the feelBot

Take **actions**, based on detected **reactions**:
- Positive: 
    - Time to rush up that workshop? 
    - Publish new features on-the-works?
    - Release it!!! Release it now !!!
- Neutral: 
    - Do not relax, we want **HYPE!**
    - Pilgrimage time : we need to spread the word!

---

## Enter the feelBot

Take **actions**, based on detected **reactions**:
- Positive: 
    - Time to rush up that workshop? 
    - Publish new features on-the-works?
    - Release it!!! Release it now !!!
- Neutral: 
    - Do not relax, we want **HYPE!**
    - Pilgrimage time : we need to spread the word!
- Negative:
    - Careful here, there are many bright people that WILL see what we cannot.
    - Hack-a-ton time!! Invite people in to make it better.

---

## Enter the feelBot

Public face is a happy, servile and interactive Slack bot.
- It can answer many questions:
    - List of components being tracked.
    - Daily / Weekly / Historical sentiments.
    - Trending topics in Schibsted community.
    - It should be able to tell a joke. Even computers like jokes!

---

## Enter the feelBot

Public face is a happy, servile and interactive Slack bot.
- It can answer many questions:
    - List of components being tracked.
    - Daily / Weekly / Historical sentiments.
    - Trending topics in Schibsted community.
    - It should be able to tell a joke. Even computers like jokes!
- It could even spit out some cool, on-demand graphs
- It’s also a sign that we’re not **spying public channels**

---

## How does this work?

- We take all new messages from some selected Slack groups
- Group them by ID,
- and then analyze the topics they talk about the most: *top-10*, *top-5*, *historical-hate-list*, ...


---

## How does this work?

- We take all new messages from some selected Slack groups
- Group them by ID,
- and then analyze the topics they talk about the most: *top-10*, *top-5*, *historical-hate-list*, ...

A *topic* is a bag of words that tend to appear together, it has no special meaning to the machine but we, as humans, can label them manually and assign them some readable description.
   - With this, we can have an idea of what conversations lean towards the most.

---

## How does this work?

- Next step is to compute general sentiment towards these topics: whenever we read a new message, we’ll associate it to one or more bags, with a certain probability: 
    - “This dev is 60% talking about Spark, but 90% talking about Analytics”

---

## How does this work?

- Next step is to compute general sentiment towards these topics: whenever we read a new message, we’ll associate it to one or more bags, with a certain probability: 
    - “This dev is 60% talking about Spark, but 90% talking about Analytics”
- We then apply sentiment analysis algorithms and compute a **score**.
     - Scores will rank from very negative to very positive, with a pretty large middle ground that should be the “no worries” zone.

---

## How does this work?

- Next step is to compute general sentiment towards these topics: whenever we read a new message, we’ll associate it to one or more bags, with a certain probability: 
    - “This dev is 60% talking about Spark, but 90% talking about Analytics”
- We then apply sentiment analysis algorithms and compute a **score**.
     - Scores will rank from very negative to very positive, with a pretty large middle ground that should be the “no worries” zone.
- Upon hitting a threshold, we might want to take some actions on the matter.
     - Before doing so, **re-analyze** with a larger sample of data! 
     - Make sure we’re not being scammed, and to double-check possible outliers.

---

## Where do robots come from?

I. **Create** *feelBot*'s database, after selecting the most appropriate data sources for the topic modeling algorithms:
   - Some of the most common, English-language, Slack channels.
   - Only were tech is being discussed
   - Avoid spreading too much, do not become the Big Brother.

---

## Where do robots come from?

I. **Create** *feelBot*'s database, after selecting the most appropriate data sources for the topic modeling algorithms:
   - Some of the most common, English-language, Slack channels.
   - Only were tech is being discussed
   - Avoid spreading too much, do not become the Big Brother.

II. **Label** a few topic-bags, and start streaming in:
  - Grab a few people only, so we can validate afterwards.
  - At the beginning scores will most likely drift a lot, wait for a plateau.
  - Graph *all the things*, they show trends human eye won’t catch.

---

## Where do robots come from?

III. **Validate** against the real user’s intentions
  - Adjust algorithm parameters
  - Do.Not.Overfit.
  - Rinse and repeat!

---

## Where do robots come from?

III. **Validate** against the real user’s intentions
  - Adjust algorithm parameters
  - Do.Not.Overfit.
  - Rinse and repeat!

IV. And **teach him** how to speak!
  - “Hey *@feelbot*, what’s next in line for Rocket?”
     - *“We’ll be releasing Messaging support on 14/02, and the new Image Service during Q1: see https://whatsnext.schibsted.com/rocket for details!”*
  - “I don’t know how new platform version is doing, maybe ask *@feelbot*?”
    - *“It’s doing pretty well, people are very excited about the speed of the new search engine! Check it out at https://scm.github.com/platform/v4”*

---

## But it can get better than this...

Carefully study more data sources:
  - Confluence docs & comments can provide valuable insights.
  - Git issues may focus on the areas that are giving the most trouble.
  - Spanish, French and Swedish/Norwegian channels might get in, **way too much people there** to be ignored

NLP is not the same problem in all languages, real challenge here.

---

## But it can get better than this...

Make it more and more intelligent:
  - “Did someone solve that annoying JSON-format bug in Emissary, *@feelbot*?”
     - *“Sure they did! Look at commit #abcdef1234 from 14/02/16.”*
  - “What did people talk about the most during this year’s Superweek, *@feelbot*?”
    - *“Top #3 technologies were Docker (again), Cassandra and Spinnaker, check out our timeline at https://twitter.com/spt/timeline?q=#superweek17”*

---

## But it can get better than this...

It'll setup a **great** codebase for real-time decission making
  - New features can be added anywhere over the same infra.
  - Could be included in the Rocket platform anytime.
  - Ground for endless code marathons

---

## Thank you

:-)
