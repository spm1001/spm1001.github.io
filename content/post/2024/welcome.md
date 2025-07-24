---
title: "Welcome"
date: "2024-01-01"
categories: [Notes to self]
description:
  "Over Christmas I decided to dig out old articles and speeches etc and put them online. For fun, I did it in Quarto, with an automated CI/CD pipeline. Here's a dull description of how..."
--- 

> _2025 Hindsight: Another in the fine tradition of technical blog setup notes from previous attempts at reboots. I've often wanted to do more posts like this for obscure technical things I figured out which I might need to remind myself of, but that's an exercise for another day._

## Setting up a Quarto blog on Github

![Quarto Logo](https://quarto.org/docs/blog/posts/2023-05-15-get-started/get-started-video-cover.png)

Useful resources are Github's [Pages setup](https://pages.github.com) guide and the Quarto's [Github Pages guide](https://quarto.org/docs/publishing/github-pages.html)

Or you could follow these steps which condense the bits that mattered to me.

Broadly we're trying to create a blog that can work with github-pages, or with that and Quarto - to have some options. 

@. On Github, make a new repo called `<username>.github.io` - pick a `.gitignore` template (e.g. the Python one)

@. Navigate to an empty directory on your machine and run the following:

```zsh
git clone https://github.com/<username>/<username>.github.io
cd <username>.github.io
```

@. Tell Github we don't want to use Jekyll thank you

`touch .nojekyll`

@. Append ignores for built site so we don't check it in to the repo as that's annoying

`echo -e "/.quarto/\n/_site/\n" >> .gitignore`

@. Make a default Quarto blog and push it to the repo

```zsh
cd ..
quarto create project blog <username>.github.io
cd <username>.github.io
git add .
git commit -m "Commit default Quarto blog"
git push # may trigger GCM
```

@. Check to make sure `git` is clean

`git status`

@. Now create a `gh-pages` branch, initialise it and then flip back to `main`

```zsh
git checkout --orphan gh-pages # switch to gh-pages
git reset --hard # make sure all changes are committed before running this!
git commit --allow-empty -m "Initialising gh-pages branch"
git push origin gh-pages
git checkout main
```

@. Publish once manually

`quarto publish gh-pages`

@. Then create the Github Action per the instructions on the Quarto page. It's just creating a file in `.github/workflows` called `publish.yml` with the following contents. The magic with the curly brackets automatically populates with a secret when a Github machine runs it. Which is cool. 


```yaml
on:
  workflow_dispatch:
  push:
    branches: main

name: Quarto Publish

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - name: Check out repository
        uses: actions/checkout@v4

      - name: Set up Quarto
        uses: quarto-dev/quarto-actions/setup@v2

      - name: Render and Publish
        uses: quarto-dev/quarto-actions/publish@v2
        with:
          target: gh-pages
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

@. With any luck your blog should now be visible at `https://<username>.github.io/` and any changes you push to the repo should automatically appear on the published website after some minutes. 
