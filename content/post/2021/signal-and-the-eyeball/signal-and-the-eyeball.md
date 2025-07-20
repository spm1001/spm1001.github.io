---
title: "The Signal and the Eyeball"
date: 2021-04-18
---
Paying to advertise is now as much about buying the targeting signal as the space in front of someone's eyeballs. But how will that play out over the next few years and what's a content owner to do?

<!--more-->

As the rest of the ad world chews through the impact of various privacy preserving changes that are happening, there’s an interesting piece [here](https://www.linkedin.com/pulse/what-audiences-inside-amazon-dsp-eldad-sotnick-yogev/) about Amazon’s DSP, from Eldad at *We Are Liberty*, which got me thinking again about signals and eyeballs. 

Amazon's targeting data is probably household level for the most part (unless you think people actually bother picking their way through Amazon’s two different, insanely fiddly methods of disambiguating members of a family) but it’s still a rich combination of media consumption and purchase interest (just like Google) gated behind the Amazon bidder and serving ads in a variety of places both on and off Amazon.

## Pubson's Choice
But who is making money here? If I'm a publisher, is it better for me to price my eyeballs using someone else's targeting signal and split the money with them? Or should I go it alone? Some people are peddling the idea that media money should only be spent on 'working media' i.e. on the space itself and not the signals.

That's clearly daft, but working out a sensible strategy is still hard because there's this shell game being played with the data and 'privacy' so it is hard to keep track. It makes me wish Bergemann and Bonatti would revisit their brilliant but brain-hurting (*enough alliteration - ed*) [2015 paper](http://www.mit.edu/~bonatti/selling_cookies.pdf), as there are some tantalising clues in there about how this might all play out. 

1. On the one hand, they find that if there are more data owners with data on the *same* people, then targeting signal prices will of course go down. However, to the extent that new data providers have data on *different* people, signal prices can actually go up, which would be bad news for those advertisers who think Amazon’s arrival in ads is necessarily going to ‘break the duopoly’ in a way that’s good for anyone but the platforms. 

2. And on the other hand, B&B show that if targeting higher value buyers is worth the cost of the targeting, then demand for advertising *space* (as opposed to targeting data) actually goes down. Which would be bad news for publishers who have lots of ad inventory but lack high-reach, high-quality targeting signals to go with them, because the data owner will tend to keep its signals exclusively attached to its own inventory rather than sharing the love. 

## Reading the Runes
So which way will it go? More value on the signal or the space? Hard to tell but there are some pointers, many of which have emerged since that paper was written. 

### Platforms curb over targeting
For a few years now we have seen platforms try to guide their trigger happy buyers away from over-targeting and toward more chunky, mid-sized, mid-funnel audiences with greater economic value, whether that is Google encouraging the purchase of larger bundles of words, or Facebook steering buyers toward larger audiences.

This suggests ‘positive targeting’ in the B&B sense is only gently positive in reality, which in B&B terms would suggest a *limit* on how much incentive the platforms have to bundle their space exclusively with their signals, because actual inventory still had significant value over and above the signal. That would push them to allow their signals to be bought elsewhere. 

### Focus on platforms' own properties
And of course we know Facebook has been inventory constrained for a number of years and while FAN was the source of top-up inventory in recent times, Apple’s privacy changes make that harder to some extent, because if you say ‘no’ on your phone then Facebook can’t activate your data on FAN.

This incentivises Facebook to have more functionality in the first party realm hence Zuck’s recent view that ATT might actually help their business not hinder it. We’ll see more shopping/transactional stuff of course, but what if FB became an app studio? What if there were hundreds of ‘Facebook’ owned first-party apps? Silly thought perhaps, but the drive here is for platforms to keep more in their O&O (owned and operated) stuff and *away* from other content owners. 

### Second-class targeting
Then there is the subtlety of which signals can be activated where. For a years now Google has been splitting the signals that can be used between a more limited set of ‘commodity’ stuff that can be used on publisher sites, and the juicy stuff which can only be bought when attached to Google inventory. The reasoning seems to have been to prevent leakage of sensitive signals like search, which would be an existential threat for the big G. Hence all that stuff about removing third party tagging from YouTube, so  sensitive signals could be activated there safely without risk of loss.

Now, however, with the tagging being done in browser and on-device (Floc et al) it is possible those signals could come out to play on third party publisher properties, which would suggest 50% platform take rate (to use the emotive terminology) is a *lower* bound

But it’s not the level of demand that people peddling the concept of ‘working media’ would desire. A number of different sources are pointing to a roughly 50/50 split in value between the targeting signal and the cost of the actual pixels in front of someone’s eyeballs. Garret’s roundup of cookie deletion studies and Facebook’s white paper have spookily similar findings. 

Now this is all being released to talk up the value of cookies in general to publishers but really what it shows is the value of *platform* data to publishers, as that’s the main thing that will survive the cookie-pocalypse. If you add in the fact that Google and Facebook already get about twice as much of the media money (80%) as they do screen time (40%) then I think that means the notional split on their own properties is even more towards the targeting signal

The B&B paper assumes that the data for exclusion targeting sits with the data owner, and therefore has a price. But while they may lack positive targeting data, the one thing many media owners can do now is provide some negative targeting at low or zero cost because they have managed to get some kind of login advertisers can link to, which lets them exclude existing customers. Publishers might know little *about* those people, but they do sometimes know *that* they are the same people. Google is encouraging a healthy publisher first-party data ecosystem and negative targeting will possibly be the biggest application. 

## Place your bets
So score 3 for platforms, 2 for publishers I think? So far so murky.

But of course framing it as a trade-off between publishers and platforms might be specious. It's perfectly possible (perhaps even likely) that publishers could make more money by selling their inventory with platform signals attached rather than going it alone. Or not. It is, as my old sociology tutor was fond of reminding me, 'an empirical question', or at least a question we could model the answer to. 

So Santa, if you’re listening, I’m hoping for an updated ‘Selling Cookies’ where the model:
- Splits knowledge about future purchase behaviour between data owners so the predictive power is partly split between them so they have (some) unique knowledge
- Allows advertisers to bring their own data to any medium for exclusion targeting of existing customers at zero cost
- And out of that produces an analysis of the split between the signal price and the price of the ad space when we maximise the total economic surplus.

