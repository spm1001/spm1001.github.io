---
title: Test Page
description: "Page to test different template and Hugo functions"
date: 2025-07-26
draft: false
---

This should work as we have added `math = true` to the `params.article` section in `hugo.toml` thus

```
[params.article]
    math = true
```

Which means I can write this in Markdown

```
$$
    \varphi = 1+\frac{1} {1+\frac{1} {1+\frac{1} {1+\cdots} } } 
$$
```
And get this.

$$
    \varphi = 1+\frac{1} {1+\frac{1} {1+\frac{1} {1+\cdots} } } 
$$

Isn't that beautiful?

