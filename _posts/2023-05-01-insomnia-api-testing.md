---
title: "Insomnia API Testing"
excerpt_separator: "<!--more-->"
categories:
  - Insomnia API
tags:
  - Insomnia API Testing
---

I had a chance to try out Insomnia today. Insomnia is a REST (and gRPC, GraphQL and WebSocket) testing tool, similar to Postman, that is free to use for individuals (as of mid 2023, atleast). It has ~25k stars on GitHub and is open core, with pricing for teams and so on. It is developed by Kong, who makes the popular Kong API Gateway suite of products.

<!--more-->

{% raw %}<img src="https://blog.chrishare.net/assets/images/insomnia-main-screen.png" alt="Insomnia API Testing - Front Screen">{% endraw %}


In short, this tool lets you author REST API test cases. Imagine you are the developer of a backend API in your software company, and you want some re-usable tests that you can run manually to verify that your server is working okay. Insomnia is a good fit here, as the UI is clean and it provides many authentication schemes such as Basic auth, OAuth20 and so on. It also supports exporting the HTTP request to a programming language (as though we were coding a client making that HTTP request). Notably, that means supporting curl - so you can share a single request to someone through Slack.
Most of this is comparable to Postman, perhaps the most popular tool. Postman has these features plus some others, including custom code hooks that can run as part of tests. Insomnia seems to have a beta plugin system but the plugins don't seem high quality at present (though that might reflect the core product having most functionality out of the box). Postman, for instance, provides at least a hacky way of generating JWTs with RS256 signatures directly, where Insomnia uses the plugin system to do that indirectly:

{% raw %}<img src="https://blog.chrishare.net/assets/images/insomnia-plugins.png" alt="Insomnia API Testing - Plugins">{% endraw %}


My thoughts on Insomnia - it's pretty good. The UI was nice and clean, though a little clunky to use (creating requests and moving them between folders is painful). It has all the core features that 90% of people want to use, and it nice and fast on my meager laptop. I could see myself switching to using Insomnia from other tools like Postman and SoapUI.