---
title: "First Post!"
date: 2021-04-17
categories: [Static Sites]
summary: "2025 Hindsight: A tradition of every attempt to rebuild my 'home on the internet' is one of these - a recursive, technical commentary on the process of building and testing the site."
description: "Explanation of how I built a version of my website in 2021 using Hugo."
image: hugo-logo-wide.svg
---

> _2025 Hindsight: A tradition of every attempt to rebuild my 'home on the internet' is one of these - some sort of technical commentary on the process of building and testing it.*_

## Introduction
I want to host articles somewhere I can link to, but I don’t want to bother with managing a site. So am setting up a static site using Hugo, and GitHub Actions so when I push a new markdown post, it automatically appears on site. 

Within the site there are a number of things I think I might like to have:

## Code blocks
I sometimes put code into things. It could be inline like `sudo make me a sandwich` or it could be a code block.
```
10 PRINT 'HELLO'
20 GOTO 20
```
Some themes make it easy to copy code and paste it. Some make it harder (Medium I'm looking at you). Some even have syntax highlighting which is pretty cool. 

##  Equations (even if theme doesn't support them)
Some suggest Katex is a good renderer for equations like this $$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$ because it is faster than others. 

So to get that working I needed to add to the theme I'm using, as it doesn't support by default. Fortunately there were a couple of helpful resources for this:

- There is a link [here](https://katex.org/docs/autorender.html) on the Katex site to a code block like the one below. Go get the version there as it might have changed. Apparently linking to javascript assets without integrity checks and frozen versions is a bad thing. Who knew? 

```zsh
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.13.2/dist/katex.min.css" integrity="sha384-Cqd8ihRLum0CCg8rz0hYKPoLZ3uw+gES2rXQXycqnL5pgVQIflxAUDS7ZSjITLb5" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.13.2/dist/katex.min.js" integrity="sha384-1Or6BdeNQb0ezrmtGeqQHFpppNd7a/gw29xeiSikBbsb44xu3uAo8c7FwbF5jhbd" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.13.2/dist/contrib/auto-render.min.js" integrity="sha384-vZTG03m+2yp6N6BNi5iM4rW4oIwk5DfcNdFfxkk9ZWpDriOkXX8voJBFrAO7MpVl" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
``` 
- This [blogger](https://kevcaz.github.io/notes/hugo/katex_and_goldmark/) managed to get past tetchy [threads](https://discourse.gohugo.io/t/use-goldmark-mathjax-extension/25721/12) on the Hugo discussion site, and came up with a way of telling Katex to 'listen' for the conventional delimiters `$$` and `$` by adding

```zsh
<script>
    document.addEventListener("DOMContentLoaded", function() {
        renderMathInElement(document.body, {
            delimiters: [
                {left: "$$", right: "$$", display: true},
                {left: "$", right: "$", display: false}
            ]
        });
    });
</script>
```

- And, to be fair, the theme maintainer has some handy hints [here](https://github.com/adityatelange/hugo-PaperMod/blob/exampleSite/content/posts/math-typesetting.md) but the amount to the same thing

1. Concenate the bits of code from above, and save as `math.html` in `/layouts/partials`. It'll look something like this
```zsh
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.13.2/dist/katex.min.css" integrity="sha384-Cqd8ihRLum0CCg8rz0hYKPoLZ3uw+gES2rXQXycqnL5pgVQIflxAUDS7ZSjITLb5" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.13.2/dist/katex.min.js" integrity="sha384-1Or6BdeNQb0ezrmtGeqQHFpppNd7a/gw29xeiSikBbsb44xu3uAo8c7FwbF5jhbd" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.13.2/dist/contrib/auto-render.min.js" integrity="sha384-vZTG03m+2yp6N6BNi5iM4rW4oIwk5DfcNdFfxkk9ZWpDriOkXX8voJBFrAO7MpVl" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>

<script>
    document.addEventListener("DOMContentLoaded", function() {
        renderMathInElement(document.body, {
            delimiters: [
                {left: "$$", right: "$$", display: true},
                {left: "$", right: "$", display: false}
            ]
        });
    });
</script>
```
2. Then make a copy of `extend_head.html`, from `/theme/PaperMod/layouts/partials`, put it in `/layouts/partials`  and add the line `{{ partial "math.html" . }}`. This is inelegant as it means we load `katex.js` on every page not just those with maths in, but for me that makes it simpler as I don't need to remember to put `math: true` in the front matter of the markdown of posts containing math. It does at least mean that, because the theme provides `extend_head.html`, the site won't break when the  theme updates. 

## Boring stuff to check the rendering of
I write things that are
- Sometimes in bullets
- Like this
And on other occasions
1. They
2. Are
3. Numbered

And below this is a horizontal rule - the rules for these are finicky - need a return before. 

---
## Sometimes pictures are nice
Here is hopefully a picture
{{< optimised_image src="https://upload.wikimedia.org/wikipedia/commons/d/d3/Turnip_2622027.jpg" alt="A picture of a turnip, used as a placeholder image for a first post." >}}

What else? Not sure. 

Here's a sentence with a footnote. Note that the horizontal rule below gets automatically (if it gets added). [^1]

[^1]: This is the footnote.

