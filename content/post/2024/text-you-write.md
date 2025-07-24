---
title: "Text you write"
date: "2024-01-16"
categories: [Magic Slides]
description:
  "Demonstration of building slides from markdown - this is an example of the text you would actually write, where the other link shows you how that renders as a slide presentation."
--- 
So below is an example of the text you would write. It looks a bit dull, but in a way that's liberating - no more fiddling around with boxes and type sizes. You'd need to learn some of the conventions, but once you do, you can take the same text file and turn it into Powerpoint, slides, PDF or many other things. 

To see the slideshow that comes from this text go [here](/posts/2024/slides.html).

```
## Hello, There

This presentation will show you examples of what you can do with Quarto and Reveal
- Bullets
- Images
- Videos
...and much more


## Two Hashes means new slide
- and more bullets
- appear like this


## You can do builds
Which look a bit weird

::: {.incremental}
- Eat spaghetti
- Drink wine
:::


## You can present with notes
You just need to use that weird syntax again

::: {.notes}
Speaker notes go here. This uses the colon syntax and means they appear in the body of the text for longhand document but in speaker notes when presented as a slideshow. 
:::


## Or if you want to get clever
You can tell it to put your notes in the PDF, but hide them when presenting as a slideshow.

<aside class="notes">
Shhh, these are your private notes using the aside class. The syntax is clunky but it means that this text will go in speaker notes for slideshow and in the right hand side for document.
</aside>
```