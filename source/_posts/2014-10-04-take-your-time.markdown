---
layout: post
title: "Take your time."
date: 2014-10-04 21:38:56 -0400
comments: true
sharing: true
footer: true
categories: 
- Programming
- Patience
---

Yesterday, whilst browsing my usual slew of subreddits, I happened upon probably the best octopus related, github compatible, static blogging framework: Octopress. In my excited frenzy to whip together something that I could call a blog, no matter the quality, I failed to notice some very key details in my process. 

<!-- more -->

The first step in setting up an Octopress blog, according to the framework's website, is to clone Octopress, and run the commands like ```bundle install```, ```rake install```, and ```rake setup_github_pages```. All well and good, and what do you know, I have a blog up and running!

{% img http://i.imgur.com/9yxAMwX.png 640 360 A Default Octopress Blog%}

Not bad, and it only took about 5 minutes! But such a short time led me to make mistake after mistake, as I foolishly believed that every step and every customization would happen in the same timeframe. In retrospect, it really did take very little time to make changes, but I was just being stupid. You see, Octopress has three folders that contain files relating to your blog. Firstly, there is the source folder. *That* is where you would make your changes, and honestly, it would seem pretty intuitive. Then, there is the public folder, which in turn contains another folder, by default called github, which contained the compiled version of the source folder. And finally, there is the deploy folder, which is basically the public folder, but with a .git folder to sync with github pages. However, when I saw [MediumFox](https://github.com/sevenadrian/MediumFox), the beautiful theme by Adrian Artiles that this blog is currently using, I pounced on the installing themes link like a starving cheetah would a gazelle. But with a lot less blood and dying gazelle noises. Ok it honestly was more like clicking on a link, but it sure felt like I was devouring a gazelle. Anyways, after adding MediumFox as a git submodule and installing, I quickly deployed to my blog's github repo (which is a project repo, this is a fairly big detail) and marveled in my now responsive blog. But the 300.00 milliseconds of marveling was cut short by a few eyesores, namely the missing images that abounded the site.

{% img http://i.imgur.com/MiTa57P.png 640 360 Something's not right... %}

To Mr. Artiles' credit, it looked pretty good despite the errors. But little folded pages are not what I wanted for my blog, no siree, and so I set out to fix such a travesty in the same rapid manner I employed while setting up Octopress. After a hasty glance at MediumFox's readme, I gleaned something about a folder called "source". Hmm... That's probably the ```.source``` folder in the MediumFox folder! Right? Nope. But sadly that didn't occur to me at the time. Regardless of which folder I entered, the error was the same: MediumFox was referencing rooday.com/images, rather than rooday.com/blog/images. After making the necessary changes to the source files, I ran ```rake generate```, but as you probably guessed, nothing changed. So, the next logical step was to run ```rake generate``` another 13 or so times. A bakers dozen of repeating commands may not really be logical, but it seemed to be the only way, as it couldn't *possibly* be *my* error. Re-reading Octopress' configuration guide (which should've been the first step) revealed a root option for Jekyll to use on relative URLs. Of course, that didn't work either. So I emailed Mr. Artiles and called it a day. If you're reading this man, I'm sorry for bothering you!

{% blockquote Me, An Unnecessary Email %}
Is there a way to change what mediumfox thinks is the root directory? My octopress blog is a project page/subdirectory of my main site, and a lot of things don't load as they are trying to be loaded from the root folder. 
{% endblockquote %}

Early the next morning, I pondered on the issue. After some deep thinking and some chocolate milk, I got an idea. "Let's just replace your normal site with the blog, and bypass the relative URL issue!" So that happened, and the thing actually worked, and looked basically as it does now.

{% img http://i.imgur.com/DoDsMq0.jpg 640 360 Just in case I changed the theme %}

About an hour or so later, I became displeased with such an extreme compromise, that I put my [old site](http://rooday.com/) back, deleted everything relating to the blog, and started from scratch. You'd think that somewhere along all this deep thinking, I would've realized that I need to go through this process slowly, and carefully look at what I needed to edit. To make a 45 minute story into a 32 word sentence, I kept editing the wrong files in the wrong folder and ended up deleting and recreating my blog repo 3 times. It was only after all that and another impulsive email to [Brandon Mathis](https://github.com/imathis), creator of Octopress, that I discovered my folly. I had been editing the wrong source folder! When MediumFox's readme mentioned a source folder, it meant the source folder in the blog, not the one specific to the theme. You're probably thinking, "Rudy, you're stupid". And you'd be right! At least in this case...I think... And that's where the title comes into play. Messing with Octopress and making a blog reminded me of a very important rule: **Take your time!** Had I made sure to change the right files, I would've saved myself a ton of headache, and in the long run, a lot of time. Did I really have to write out a 5580 character markdown file to get this point across? No, but I sure as hell needed a first post on my blog. Thanks for sticking around! And please take this token of my appreciation:

{% img http://img.pandawhale.com/93002-reddit-silver-medal-meme-funny-B9d2.jpeg 420 420 Some Reddit Silver for you troubles%}