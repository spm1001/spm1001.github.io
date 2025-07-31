---
title: "Slides you get"
date: 2024-01-16
outputs: ["Reveal"]
categories: [Magic Slides]
summary: "Reveal Slide Presentation"
description: "This is meant to be a demo of how to get slide presentations embedded in my site, using a template that invokes Reveal.js"
image: bandit.jpeg
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

