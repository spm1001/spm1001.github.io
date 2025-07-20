---
title: "Fear Geeks Bearing Gifts"
date: "2015-10-13"
categories: Suckers
description:
 "Early ruminations on the 'openness' of AMP"
--- 


> _2025 Hindsight is not bad here actually. There definitely was more to AMP than met the eye - an early shot in Google's push to ad-tech dominance, just a couple of years before [Jedi Blue](https://en.wikipedia.org/wiki/Jedi_Blue). (Man, I really thought Header Bidding and Atlas were the mutts' back then.) That said, I later met some of the AMP folk, who genuinely believed - even under the application of alcohol - that they were doing it for the good of the publishers-formerly-known-as-print-pubs. Maybe they just didn't know about the plan to let AMP adopters rank higher. As usual on this blog views are my own and not any current or previous employer's. Quite pleased looking back at this though._

One of the best things about BlackBerry in its heyday was that it worked hard to make the best of a rubbish mobile connection. It gave the user an illusion of speed and control, and got on with sending and receiving stuff in the background when it could. In effect the device did the waiting for you. 

Flash forward a decade or so and we see Facebook and Google doing the same thing with Instant Articles and AMP respectively. 

## Atoms apiece?
Instant Articles is much commented on so there's not much I can add here, but the main thing to remember is that we are now seeing a separation of the discovery layer from the hosting of the content; separation of the headline and snippet, from the full article. It's as if the front page of the website has been ripped off, torn up and put somewhere else, the somewhere being a feed of some kind.

All the Buzzfeed articles for example, live on a website called, strangely enough, buzzfeed.com, but that is a matter of sublime indifference because almost no-one goes there to start with. That's just the place where the stuff is *hosted*. The place where people *see* all the headlines is Facebook, and Instant Articles is Facebook's Blackberry-like attempt to smooth the transition between the two because frankly, they are better at doing speedy mobile stuff than almost anyone else. 

Except maybe Google, which brings me to AMP. Took me a while to get my head round this, and understand what it actually is. For one thing, it is called Accelerated Mobile Pages, but of course, these days that's just like saying Accelerated Pages. Yes browser time might only be a fifth of the time we spend on our mobile devices but that's still an awful lot of time.

## Is AMP 'open'?
> Can't help thinking of Rubin's disingenuous tweet about how 'open' Android was. Obviously he's done worse since things since then, but the smugness and deceit of [that tweet](https://techcrunch.com/2010/10/19/andy-rubin-twitter) still sticks in my craw.

The other thing that confused me was all the stuff about how 'open' it was. Obviously, from a positioning point of view this spin is designed to engage to Publishers worried about Facebook's stranglehold on mobile attention in general and Instant Articles in particular. Note the wide range of launch partners they've signed up includes some of the online publishers who are most thoughtful about the technologies they use, such as the BBC and the Guardian. (If you don't believe me look at the [stats](http://www.nytimes.com/interactive/2015/10/01/business/cost-of-mobile-ads.html) the NYT did recently on page load times of different websites, and just read anything on the [BBC Internet Blog](http://www.bbc.co.uk/blogs/internet).)

In essence AMP is just some nice libraries and standards, which, if used and followed, make your site much more zippy than it would be if you tried to do it without Google's help. This is partly through Google's offer of free cacheing of the Publisher's AMPed stuff to deliver it more quickly, and partly by relaying a lot of what Google has learned about how to engineer for speed. Which is a lot. AMP provides a bunch of turbo-charged, Google-written libraries to do common things like display images, animations, videos and, oh look, advertising. 

Ah. 

## Control in the name of speed
If you look [here](https://github.com/ampproject/amphtml/blob/master/builtins/amp-ad.md) you can see the AMP library for serving ads. Still in its infancy, it uses tricks to tame all our greedy tracking code, but maybe this is where AMP becomes slightly less open. I could be being paranoid, but as you'll see if you follow the link, it is starting with a very select group of Ad Networks: AOL, Amazon, the somewhat less well-known AdReactor and, er, Google in both AdSense and DoubleClick flavours.

Admittedly, if the adblocking debates have taught us anything it is that we advertisers have corrupted the mobile Eden with our javascript serpents, lusting after Knowledge, but do we want Google to play God here? "On thy belly shalt though go, and dust shalt though eat all the days of thy life, and I will put enmity between thee and consumer and between thy code and her identity. And it shall bruise thy head, and though shalt buy only my audience targeting signals."