---
title: "Text you write"
date: "2024-01-16"
categories: [Magic Slides]
summary: "This was a rather optimistic attempt, as part of the Quarto version of my site, to try and teach some colleagues how to write slides in Markdown."
description:
  "Demonstration of building slides from Markdown - this is an example of the text you would actually write, where the other link shows you how that renders as a slide presentation."
image: mark.png
--- 

> _2025 Hindsight: This was a rather optimistic attempt, as part of the Quarto version of my site, to try and teach some colleagues how to write slides in Markdown._

So below is an example of the text you would write. It looks a bit dull, but in a way that's liberating - no more fiddling around with boxes and type sizes. You'd need to learn some of the conventions, but once you do, you can take the same text file and turn it into Powerpoint, slides, PDF or many other things. 

To see the slideshow that comes from this text go [here](/posts/2024/slides-you-get/).

```zsh
---
title: "Slides you get"
date: 2024-01-16
outputs: ["Reveal"]
categories: [Magic Slides]
summary: "Reveal Slide Presentation"
description: "This is meant to be a demo of how to get slide presentations embedded in my site, using a template that invokes Reveal.js"
---

# Hello there

This presentation will show you examples of what you can do with Reveal.js and Hugo.

- Bullets
- Images
- Videos
...and much more

---

# Slide 2

This is a slide.
Separated by `---`

---

# Hash means top level heading
- Here's a bullet point.
- And another.
- They appear instantly by default.

---

## Smaller title has two hashes
And you can add images
{{< optimised_image src="bandit.jpeg" alt="A picture of my cat, Bandit" >}}

---

# You can do builds

Here, we're using `class="fragment"` directly in HTML.

<ul>
    <li class="fragment">This is the first list item.</li>
    <li class="fragment">This is the second list item.</li>
    <li class="fragment">This is the third list item.</li>
</ul>

---

# You can present with notes too

This slide has speaker notes, which are hidden from the main presentation. They will appear in the separate speaker view when you press 'S' during the presentation.

<aside class="notes">
    Hello! Well done... you found me. 
</aside>


```