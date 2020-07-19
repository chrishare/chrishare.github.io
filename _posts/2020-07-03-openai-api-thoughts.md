---
layout: post
title:  "OpenAI API - First Impressions"
date:   2020-07-06 10:21:15 +1100
categories: blog
---

## OpenAI's API Business

Recently, OpenAI unveiled a new API that serves AI models developed by the company. They have a blog post [here](https://openai.com/blog/openai-api/) if you are unfamiliar with that work.

In short, the initial models seemingly offered behind the API are GPT-based language models that complete a prompt provided in the API request. For example, you feed it:

```
We’re releasing an API for accessing new AI models developed by OpenAI. Unlike most AI systems which are designed for one use-case, the API today provides a general-purpose “text in, text out” interface, allowing users to try it on virtually any English language task. You can now request access in order to integrate the API into your product, develop an entirely new application, or help us explore the strengths and limits of this technology.
```

and the model will complete that text:

```
The road to making AI safe and useful is long and challenging, but with the support of the developer community we expect to get there much faster than working alone.
```

How is this useful? Well, it can be used in a bunch of use cases. Per the [beta page](https://beta.openai.com), use cases might include chatbots for customer service, semantic text search, question / answer recall, and so on. Crucially, the model can be fine tuned on specific tasks. For example, the blog post demonstrates feeding some english language descriptions of linux commands, with the associated linux syntax, with the model then able to output linux syntax for new (unseen) descriptions with surprisingly strong accuracy.

The models that are being trained here, such as GPT3 models, are extremely expensive to train - even without including the enormous research and development costs leading to the model architecture and training code; this [Venture Beat article](https://venturebeat.com/2020/06/11/openai-launches-an-api-to-commercialize-its-research/) estimates training costs of $12 million USD, presumably on the final version of the model alone. Offering these APIs therefore is a way to commercialize the AI research being conducted to progress Artificial General Intelligence that they perform.

## My Impressions

I won't go into the merits of current-generation language models here; clearly they are capable of some extremely impressive performance on language tasks, and there are many use cases for these models. I personally do not think that simply scaling these models without applying significant architectural changes and cognitive biases will lead to 'intelligence' in a general or human sense - but that doesn't make this technology useless at all.

Rather, I want to talk about the commercial aspects of this work.

For background, I am an IT professional with limited (undergraduate, hobbyist) experience with AI and Machine learning technology. Something I often think about is how one can sustain a career in this field. There seem to be the following paths;
1. Become a researcher - typically requiring a PhD. You get paid to research and or teach this technology.
2. Become an ML engineer or data scientist. You work for a company solving business problems using AI/ML techniques by doing development, or configuration of ML software.
3. Build a product that uses ML techniques for product features, or to improve functionality.
4. Build and sell ML software that allows ML engineers to be productive.

OpenAI has traditionally taken approach 3 in a way, to much controversy. Initially it was founded to combat vested interests, to ensure safety (rogue AI, etc) and to ensure that the fruits of AI technology are shared fairly, with a $1 billion USD endowment from business people such as Elon Musk. Since then, to continue operation, OpenAI has taken on investment from Microsoft and others in lieu of philanthropic investment, at least to some degree under the promise that the results of AGI breakthroughs will be shared with investors such that the technology will make them money. Formally, that included transition from a non-profit to a capped-profit model. There is a great writeup [here](https://www.technologyreview.com/2020/02/17/844721/ai-openai-moonshot-elon-musk-sam-altman-greg-brockman-messy-secretive-reality/).

It's a difficult position for OpenAI to be in. AI research is expensive, and without market-leading products that can leverage byproducts of AI research, there is little they can do but make promises in order to get investments. One thing they can do is commercialize their models for others to leverage, which is where this API offering comes in. That seems like a win-win situation - OpenAI can financial offset research and compute costs, and organisations that could never hope to replicate/develop/run large and state of the art models such as GPT3.

There would be privacy concerns. These can be offset to some degree with transparency around data retention and storage policies, and with homomorphic encryption techniques.

There would be safety, bias and correctness concerns. We've seen very often that bias in training datasets, sampling techniques, researcher backgrounds and so on often lead to entrenched discrimination against minorities being perpetuated. We also know that the technology isn't perfect; it doesn't perfectly understand the text it is processing. It has no real conceptual understanding of what that text means. All these things mean that it often needs to be used as an aid for humans, rather than a replacement - or used for tasks where failure is sometimes acceptable.

Nonetheless, as a client, I'd be excited to explore this API. I think this technology in general will transform a bunch of tasks that people currently perform manually; I envisage that things like intelligent completions of things like code aren't going to drastically change how programmers work in the next 10 years. Moreover, it seems like all white-collar work, certainly mine, involves to some degree "dumb" pattern-maching based text processing - things like filling out request forms, transforming text, that should easily extrapolate from a few examples.

Perhaps more importantly, this gives me more confidence that there is a 5th way to make money in this industry; like 4, you develop ML software, but rather than shipping it for someone to incorporate in their software, they invoke it via AI. This is already done by organisations like Google and Microsoft for 'common' ML tasks, but I feel that determined players can find niches that are not being explored by the industry giants, because they are primarily focused on general-purpose technology that they can use in their first-class products, or by just offering something that is advanced like OpenAI are doing.

Even as I re-read this article for mistakes, it feels like I am doing something that an ML model could do for me, largely correctly. The future can't come fast enough.
