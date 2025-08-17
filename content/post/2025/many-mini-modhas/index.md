---
title: "Many Mini Mes"
date: 2025-08-17T22:46:51+01:00
categories: [Moar employees]
summary: "OMG, yet another middle-aged bore who spent the weekend mucking about with Claude Code ffs"
description: "I was talking to Gemini the other day. My eldest overheard me and said 'God, dad, it sounded like you were trying to raise yet another Modha child...'"
slug: Many Mini Modhas
image: duplicator.jpeg
---

> OMG, yet another middle-aged bore who spent the weekend mucking about with Claude Code ffs

My mind is glowing.

Prob not one the Prodigy's most [memorable lyrics or perhaps even tracks](https://genius.com/The-prodigy-claustrophobic-sting-lyrics) but it's pretty much how I'm feeling after about 8 hours of working intensely with Claude Code.

Sorry-not-sorry for another late-to-party post, but I've built something it would have taken me weeks to do, if I'd even have managed at all. It was like having tens of Mini Modhas running around which some people would find horrifying 🙀

Made me think of what other people have been saying - the machines are employees now too, and need the same support. Kinda.

I know that sounds weird, and I haven't "fallen for Claudette" as my family keep teasing, but in terms of managerial discipline and organisation, there's consonance.

I'm reminded of an old mnemonic I got taught - SAFE

- Set expectations
- Allocate work fairly
- Feedback and coaching
- Evaluate and reflect

And here's how it played out

1. **Set expectations** - thorough briefing on objectives, helping form a plan and then providing useful resources are all crucial. I did all the obvious things like write a specification, and also spent a ludicrous amount of time debugging the set up of an MCP server so the model could read the Workspace API documentation itself efficiently. To do that I had to get Claude itself to rewrite the broken [MCP implementation from Google](https://github.com/googleworkspace/dev-assist). Even the model started pushing back saying we should just get on with the development task, but it paid off later on when it had ready access to all the docs.

See also [these people](https://stackbench.ai/) who will get a machine to assess whether other machines find your docs legible or not. It's like Google's [PageSpeed Insights](https://pagespeed.web.dev/) but instead of assessing how good your site is for humans it's assessing its readability for machines.

2. **Allocate work fairly** - which is happening automatically too - the Sonnet model I was using knocked back a lot of basic tasks to a more junior model without my knowledge. I guess it's efficient for Anthropic too. But as the manager, I had to talk a lot to the model about how it was managing sub processes (in code) and sub agents as well, when I could see it wasn't helping. e.g. don't spawn a thread to wait for something, because you won't get control back until it times out.

3. **Feedback and coaching** - at different levels at different times along the process; reflecting e.g. on how it keeps making the same mistake with not escaping spaces in path names because it's assuming Linux not Mac, then making sure that that goes in the notes the system uses to startup a new session.

And feedback is both ways right? I often asked for a process to go more slowly so I could learn what was going on, especially with the darker forms of `git` magic, and then to document the learnings for me in a separate note. Which you can see in the Repo if you're bored. - yeah all it does at the moment is change every occurrence of Arial in a Google Slides presentation to Comic Sans - but it does it all automatically...

4. **Evaluate** - happens throughout of course, but the bit I'm proud of is that this repo can self-reflect rapidly. The loop from pushing code into Apps Script, to running that code to change Slides, to reading the logs off GCP, to pushing adjusted code again takes 20 seconds. Which is extraordinary in a way - 20s for a whole bunch of cloud infrastructure to interact like that. Which means that when I get into more actual development, my ability to iterate will be super-human.

What's it all for? Well, if you keep an eye on the repo you'll see, but the basic idea is to have something that can go through a Slides doc and systematically change everything to be consistent with a corporate template. I know that that's pretty dull in some ways, and it may even be that a harness like [this one](https://github.com/taylorwilsdon/google_workspace_mcp) will eventually do away with this sort of thing anyway, but at the moment it looks like that simply lets me make slides. Not fiddle about with them endlessly with the power of my mind, which is usually where all the damn time gets sucked...
