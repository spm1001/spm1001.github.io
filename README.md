# spm1001.github.io

## What is this?

This is the code for my personal website. 

## Why did you make it?

Over the years, I've made a few little websites to host stuff I've written/presented, but never really kept them going for long. I'm having another go, but this time, I'm making a bit more effort and rounding up older pieces as well. 

I'm going to take a leaf out of Simon Willison's book by posting more frequently and worrying less about what I post. 

## How does it work?

It uses Hugo to turn a bunch of folders containing text files and images, and turns it into a static website, which is then hosted by Github at https://spm1001.planetmodha.com

It also produces an RSS export at https://spm1001.planetmodha.com/index.xml, with summaries of the articles. 

I use Zapier to watch this RSS and then cross-post to Linkedin, so that I don't have to do that manually. 

## Notes to self

In the front matter of each post, there's an option for both a `description` and a `summary`. The latter, if specified is what gets put into the RSS feed, although confusingly, Zapier calls it the `description`. 

If `summary` is unspecified it doesn't take the `description` - that would be too easy - it takes the first bit of the article itself instead. 

So in summary
- `summary` (if specified) is what will appear in the top of the LinkedIn cross-post as I've told Zapier to use it above the post URL
- `description` is what will appear in the card for the post on the site, and therefore will *also* appear in the LinkedIn post, because when it goes to grab the URL it takes the description. 

Hence here, the first bit is the `summary` front matter and the secon bit of text is from the `description`

![](in-buffer.png)

Whereas on the site itself, it will ignore the `summary` and use the `description`, so it makes sense to put (something like) the `summary` at the top of the article as well. 

![](on-site.png) 

### Submodule Handling

The git [help page](https://git-scm.com/book/en/v2/Git-Tools-Submodules) is surprisingly helpful and readable

#### When cloning

So if you clone from Github, it won't copy the files for the submodules

If you've cloned already then do

```
git submodule init
git submodule update
```

If you haven't cloned yet then add `--recurse-submodules` to make it work
```
git clone --recurse-submodules https://github.com/spm1001/spm1001.github.io.git
```

#### To update
`git submodule update --remote`



