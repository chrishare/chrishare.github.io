---
layout: post
title:  "Starcraft AI"
date:   2017-01-15 09:23:35 +1100
categories: blog
---
Recently, DeepMind - the British artificial intelligence research organisation - announced that they were working with Blizzard Entertainment to [provide a programmable interface for the videogame Starcraft 2](https://deepmind.com/blog/deepmind-and-blizzard-release-starcraft-ii-ai-research-environment/). In this post, I want to explore the merit of this work, and what avenues of research this could open or extend.

To begin with, what is [Starcraft 2](https://en.wikipedia.org/wiki/StarCraft_II:_Wings_of_Liberty)? Starcraft 2 is a popular multiplayer Real-Time Strategy (RTS) videogame that sees players amassing resources and armies to defeat opponents. Players choose from three distinct factions, each having different units and strategies they can employ. The game is played in real time, with fog obscuring unoccupied parts of the map, and ends only when a player concedes or is destroyed. Players must gather resources and research technologies in order to produce units that can fight and perform other abilities. The game is a sequel to [Starcraft Brood War](https://en.wikipedia.org/wiki/StarCraft:_Brood_War), which was one of the earliest games played profressionally as an eSport, is still played today. To get a feel for the game, I encourage you to watch a [top-tier Starcraft](https://youtu.be/iYYkS70OGpo?list=PL480BA4B952F7E005&t=114) match on youtube and listen to the commentary desribe the strategy and mechanics being used.

The RTS genre is dinstinguished by the strategies and tactics that can utilised to defeat the enemy. Many of the characteristics of this genre - such as imperfect information, rock-scissors-paper style compromise between different unit, and tradeoffs between short and long term objectives, serve to keep humans interested through 'depth' - the vast breadth of viable actions and scenarios that any given game instance could see.  

Putting aside that video games themselves are entertaining, and the [quality of videogame AI can greatly effect how fun a game is](http://www.gamasutra.com/view/news/269634/7_examples_of_game_AI_that_every_developer_should_study.php), how is this relevant to AI researchers and real world problems? Well, the game shares a number of problem characteristics that an agent would face in the real world, such as the following: 

**Partially Observable** - The 'Fog of War' limits map visibility to the area surounding the player's units, allowing strategies to be prepared and executed in secret, placing a premium on information gathering. Imperfect information is something that Chess and Go agents do not need to generally deal with.

**Multiagent, Adversarial** - The game involves more than just simple mechanics. To win, strategies must be employed that successfully exploit deficiencies in the opponents' strategy, and games often involve a series of counter attacks and skirmishes until one side is worn down. Mastering the game involves modelling not only the game itself, but other agents within the game.

**Stochastic** - Whilst most actions are deterministic, there are circumstances in the game that involve chance, such as firing up-hill. This chance obeys known probabilities, meaning that actions and outcomes can be reasoned about with reliability. Depending on your view about [physics](https://en.wikipedia.org/wiki/Determinism), 'chance' in the real world can be viewed as a mechanism that people use to cope with the near infinite complexity of our world. 

**Sequential** - Decisions made early have lasting consequences. For instance, an early failed attack may leave the player at a long-term resource disadvantage. This trade-off between short and long term goals is something that humans confront (or avoid) in their daily lives.

**Dynamic** - The environment changes over the course of the game - resources are mined out, map artefacts are destroyed, and so on.

**Continuous** - Players can issue commands continuously, and in parallel. The game is truly real-time in that the balance between time spent acting and thinking must be limited and compromised, and that multitasking is possible at both mechanical and strategic levels.

**Complex Environment** - Each race can produce many different units, each with their own strengths and weaknesses, and each unit has different abilities that can be employed to win. Different maps have characteristics that lend themselves to different strategies. The state space for the games is enormous; an exhasutive tree search is simply not possible with today's technology. The state space is larger than Go, for instance - since each game have have hundreds of units with can, in turn, take many unique actions.

**Replays** - Many thousands of replays will presumably become available for programmatic analysis. That is, previous game instances can be reloaded and interrogated interactively.

**Low System Requirements** - The game is computationally cheap to run, allowing the game and agent(s) to run quickly on commodity computers. Being a video-game, no 'real world' resources are required and nobody is endangered. Moreover, there is no real limit on the number of games that can proceed concurrently - noting that information about game co-ordination and licensing is pending.

**Accessible** - This is a game that people can intuitively understand even without being experienced gamers.

**Real Time** - The game is played in real-time, as opposed to games like Go that are played in discrete steps.


It is important to note that many games have these characteristics - and some of them have interfaces already. Specifically, Starcraft Broodwar has a programming interface called [BWAPI](https://github.com/bwapi/bwapi) that allows an agent to read game state and issue commands interactively. Furthermore, there is an existing community of students and AI researchers building agents using BWAPI, and ongoing [tournaments](http://sscaitournament.com/). So what new opportunities or challenges does this release provide?

To begin with, Starcraft 2 is a modern, mainstream game that is attactive to watch. That matters - at least in as far as publicity is useful as fuel for continued funding. Moreover - whilst we cannot know for sure how this interface will be implemented - there are strong indications that the interface being developed will be first-class - as one would expect given Blizzard's involvement. From the press release, we know that actions-per-minute will be limited, and that visual sensors will be supported - which are both critical for replicating agents with human-like constraints. We also know that a scenario-editor that is custom tailored to AI researchers will be developed, though the details are scarce at this time.

What we don't know is what other modifications will be made to assist AI research. Will the game be modified to allow the agent to block game progression, to allow more training time for online agents? How freely will this interface be available - and in what form? Will we need to buy a special version of the game. or pay licensing fees? Clearly there will be some controls developed to ensure that competitive human play is not ruined either by human-level bots, if they can truly be developed, or by sub-par bots. Starcraft 2 (presumably the latest expansion, Legacy of the Void, will be used here) does not run on Linux, whereas many GPU-based deep learning toolkits run exclusively on Linux, so having a bridge between the game and AI server may be necessary for some researchers.

All in all, I think this is a terrific development for the AI research community and I look forward to more details about the interface. In addition to initiatives such as [OpenAI Universe](https://universe.openai.com/), the number of avenues open to AI researchers is very broad, which helps ensure that tangible benefits flowing from research are less likely to be data-blocked, and less likely to be concentrated in the hands of a few.


Thanks for reading! Have any feedback about the article? Anything you'd like to see me write about next? Follow me on twitter at [@chrishare](https://twitter.com/chrishareau).