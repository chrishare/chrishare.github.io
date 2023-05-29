---
title: "Generalist AIs and You"
excerpt_separator: "<!--more-->"
categories:
  - Machine Learning
tags:
  - Machine Learning
  - PyTorch
  - Generalist
  - Artificial Intelligence
---

A month or so ago, Deepmind published a paper demonstrating success in training a 'Generalist' agent that they call [Gato](https://www.deepmind.com/publications/a-generalist-agent), which is a single neural network that can perform many tasks - including robotic joint manipulation tasks, playing video games, captioning images and so on. Should you be afraid that this marks a step towards muscular Austrian-accented cyborg stealing our motorcycles? Is this a step forward at all?

<!--more-->

{% raw %}<img src="https://blog.chrishare.net/assets/images/gato-arch.png" alt="Gato Architecture">{% endraw %}

Well, certainly I don't think you should be afraid, but you should be aware and alert to the societal impacts that general AI agents can and will have, as the technology improves, just as you should for all traditional software products you use.

You shouldn't be afraid, because this paper is an excellent feat of engineering but not an enormous leap in theory. Putting aside that similar results have been shown before, it is an excellent demonstration that singlular networks can perform many tasks - more than has been shown before. However, it perhaps raises more theory questions than it answers, noting that is still really valuable. 

These questions include whether the 'huge-single-kitchensink' model approach is fundamentally better than stitching together niche models, with perhaps some overarching, learned, policy orchestration - in terms of training time and data efficiency, task performance, and inference efficiency. Along the same lines, it poses the question of whether this model type might be another 'foundation' model. Perhaps more crucially, it poses the question - what general actually means. Is Gato general in the AGI sense? 

I think so. AGI really means human-level performance across the same breadth of challenges that humans face in normal life. Gato is certainly a (small) step towards that over models we've seen in the past that achieve super-human feats in exactly one (very well-specified) task, like playing an Atari game. But that isn't something to be concerned by - it's actually very inline with what would be a very useful agent - it's only the I in AGI that is scary.

{% raw %}<img src="https://blog.chrishare.net/assets/images/gato-loss.png" alt="Gato Loss Plot">{% endraw %}

The I in AGI is intelligence, which is what is special about human beings. Most human beings. It's the ability to apply and acquire knowledge, but also the requirement of or key to being able to reason, understand, plan, and ultimately to self-awareness. We aren't overly afraid of individual humans being intelligent, because no human is that much smarter than any other human, and their agency is limited by the rules of society (democracy, laws, etc) and their physical form. An AGI might not be so constrained, especially when they tick the G box - so a high I intelligent agent whose goals and moraily is not alligned with our could be dangerous.

But I digress. The point is, Gato is a step towards the G in AGI - perhaps not a step into the unknown, but a step nonetheless, and the questions it re-iterates are critical for the field to confront. I really enjoyed reading the paper, and found it very accessible as someone not in academia.

On a final note, the 'author contributions' part at the end of the paper is a great idea, and something I can see being valuable in things like project attributions and so on, rather than vague title-based lists of people.