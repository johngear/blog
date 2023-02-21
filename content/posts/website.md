---
title: "Making this Website"
date: 2023-02-17T10:53:16-07:00
draft: false
tags: ["website"]
ShowToc: true
ShowBreadCrumbs: true

---

A lot of people who I look up to in tech have websites like this, where they talk about themselves a bit more than they’d be comfortable doing outside of interviews. I also wanted a place to write random thoughts, and I suppose that people in hiring positions look favorably on things like this. 

So, it was time to make a website again. I was aiming for the following:

1. Easy to add writings in markdown format
2. Quick to push updates
3. Not using a website-making-website

I'd done this before, using Bootstrap and AWS, but found the AWS experience pretty frustrating. Getting it all setup was a bit tedious, but my workflow for pushing updates had a lot of friction, which kept me from using it much. I don't dislike AWS as a service, it just is over-customizable for a small project that takes up minimal headspace. Bootstrap was fine, but formatting writings was slow. Again-- a high friction process soon gets avoided. Sure, I could've figured out a better workflow, but I'm not a webdev

So now, a few years later, I found Hugo was great for parsing markdown to HTML, I can easily pull up GEdit from terminal and write something and it will appear on my website! It's awesome. 

Last, I heard that Netlify was a great for getting the website online. Instead of dealing with the S3 buckets and cloudfront (or whatever strange names AWS uses now), Netlify was a quick way to get my domain back, and deploy directly from Github. So now, I can write something in markdown in my favorite text editor, save it and push to Github, and it shows up on the Internet in 2 minutes or so. Amazing!

I don't know the entire gamut of static website options, but I'd give a cautious recommendation to someone who is proficient at coding to use this combination of Hugo and Netlify. It can all be created in a day or two of reading docs and watching videos. 
