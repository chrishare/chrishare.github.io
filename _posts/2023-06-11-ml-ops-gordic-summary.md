---
title: "ML Ops - What is it? Aleksa Gordic Notes"
excerpt_separator: "<!--more-->"
categories:
  - Machine Learning
tags:
  - Quick Tips
  - DevOps
  - Support
  - ML Ops
---

When I saw one of the best ML youtubers, [Aleksa Gordic](https://www.youtube.com/@TheAIEpiphany) has released a [video](https://www.youtube.com/watch?v=LdLFJUlPa4Y) about ML Ops, I jumped at the chance to watch, learn and share my notes. In this video, we learn about what ML Ops actually is; how we deploy, maintain and verify ML models in production that actually get used by people. Here we go.

Remember, ML is Machine Learning; the deployment of a deep neural network (or some other model) that does prediction/classification/redression/generation for a user given their user input. Ops here is support, just like supporting any other program - but with unique challenges for ML.

<!--more-->

## Important Links

The big takeaway of this video is to highlight some excellent videos. Here are some courses we can jump to for more information:

[MadeWithML](https://madewithml.com/) - Free and open text-based course courtesy [Goku](https://twitter.com/GokuMohandas). The most high-level course, and easy to get into.

[Full Stack Deep Learning](https://github.com/the-full-stack/fsdl-text-recognizer-2022-labs) - Free and open, youtube video-based.

[Deploying ML to Productopn](https://www.coursera.org/learn/deploying-machine-learning-models-in-production) - Free but requires registration, video-based. Courtesy Coursera.

[Machine Learning System Design](https://stanford-cs329s.github.io/syllabus.html) - Free and open course syllabus, so slides and lecture notes. Courtesy Stanford. The instructor [Chip Huyen](https://huyenchip.com/) has an excellent book that covers this content as well.


These courses are excellent. If you're completely new to ML and want to get busy, probably the Full Stack Deep Learning course is the way to go - but these are all excellent. If you want a more gentle introduction, the MadeWithML course would be the way to go. The Stanford course has the most advanced content, with theory explained.


## Challenges of ML Ops - Why Is It Even A Thing?

ML Ops is unique versus regular software support, because we have different concepts and challenges at play. We have a potentially expensive computation that we want run - model inference - which might be big enough to warrant specialized hardware such as GPU. Inference might be so expensive that we want to precompute a bunch of results and instead retrieve them at runtime, which isn't super common outside of ML - where traditionally datastore access is the slow part. We have data drift, where the quality of our model's predictions can change over time (imagine that new kinds of music become more popular; we would want to recommend different music to allow for that, in the absence of more information). We likely want to capture user feedback that tells us whether the model made a good prediction or not - and we may want to use that data for further tuning of the model.

Over and above that, we have the design time training requirements. How do we track the models we are producing? Do we version them? How do we track the expieriments that yield these models (hyper parameters, the training data we used, the training regime and so on)? If training a model will take a long time - how do we protect against loss, should a server or GPU fail partway through training? How do we alert ourselves to failures during training, let alone monitor metrics we care about like loss?

All of this is part of ML Ops, which is why it's a specialized role in large companies.

And on top of that, we have traditional challenges - exposing our app properly and securely over the network, being cost effective, managing failures and diasters, taking backups, managing code versions and deployments, and so on. Often that falls to the same people that have to run the ML Ops stuff.

Please note - a lot of these challenges are only hard and warrant special techniques when we have a medium to high-level of complex problem. That might be when we have lots of developers involved, lots of data, especially sensitive data, lots of machines and so on. If we have a simple task - then often we can get away with just skipping some of these techniques, like using AirFlow and special monitoring tools.

## Other Important Tips

First, do traditional software stuff well. Use standard libraries for code - e.g. FastAPI in python for exposing an API - as you would with traditional software. The field of software developers is much larger than ML experts, so we want to lean on that and use a stack that might be familiar and easy to use for those people. Use git, docker, do good documentation. Use code formatters, code versioning, local development support, versioning of your infra code (for the API server, etc) - all standard stuff. 

One thing I didn't know about - [Pre=Commit](https://pre-commit.com/) is a yaml-based DSL for specifying what stuff should run as part of a commit to verify the code commit is good before completing the commit. It uses git hooks to do so. Super interesting, to incorporate error checking that can be automated into our workflow.

For ML work, there is a growing field to special-built tools that can do a lot for us to save us time reinventing the wheel. As an example, let's imagine we have a data pipeline that takes gigs of data from Amazon S3, normalizes it locally, saves that data to a different S3 store, then triggers an ML process on a different server (with GPUs attached) to train a model on that new data. Well - we probably could write a custom program that calls these 4 processes sequentially - but that's error prone for long processes that we may want to start, doesn't suppoer distributed computation well (where we might want multiple servers doing different parts), means repetition, and so on. Instead, we might want to use a tool like [Kubeflow](https://www.kubeflow.org/docs/started/introduction/), which uses K8S techniques for ML problems, or [AirFlow](https://airflow.apache.org/), which is a more general graph-based (not ML specific) orchestration framework that do this stuff for us and save us time. Likewise, there are ML-specific API servers like 'TF Serving' for Tensorflow, and monitoring solutions like Tensorboard, that can save time versus even generic solutions, since they have bells and whistles for ML contexts. 

## Conclusion

That's it for the video. There is a second video in the series, where he goes on to show [StreamLit](https://streamlit.io/) which is a Python framework for quickly authoring data-based applications (visualizations, data interactions, etc) as shareable (online) web apps. The value-add is that it lets you skip a lot of boilerplate work and get straight to the interesting work of building the data rendering, and so on. I personally wouldn't use this for a production app that was customer-facing, but it sounds great for internal tools or low-importance apps that are self-contained, rather than part of a broarder app. Having said that - I am no expert.



And that's it for this post? Found it interesting? Please share or tell me about it on Twitter.