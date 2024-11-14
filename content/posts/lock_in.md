---
title: "Lock In: an application to help you focus!"
date: 2024-11-13T22:57:15-08:00
draft: false

tags: ["llms", "hackathon"]
ShowToc: false
ShowBreadCrumbs: true

---

### An Anthropic and Menlo Ventures Hackathon Project

On November 2, I went to a Claude Hackathon hosted at the Anthropic HQ. I had worked on this project before, but it was a good chance to finish and demo it to others!

Large language models are smart, and immensely helpful. Oftentimes, I find that my progress on a problem is bottlenecked more by my ability to maintain a continuous stream of uninterrupted focus, rather than intelligence. More broadly, I believe that this executive functioning limits progress more than pure reasoning ability, and this will only continue to be more true as Claude continues to get better and better. 

It seemed intuitive to me that an LLM could be a great focus assistant, helping you stay on task and monitoring your computer usage for when you stray off task. Of course you can do this in a naive way (which I do), and use software that just blocks certain distracting site like Twitter or Youtube. But focus is context dependent! Sometimes I want to visit my Twitter bookmarks for an interesting thread or see a Youtube tutorial of some problem I am working on. In the same way your friend at the library might understand this, a good focus assistant should understand this too.

### Lock In
So I built [Lock In](https://github.com/johngear/lock_in).

Using Claude and Javascript, I built a Chrome Extension that you give a Goal and a time you want to work on it for. Whenever you change tabs, it will look at your new web page, compare it to the goal you've given it, and decide whether it should Nudge you (send a little message) to suggest you get back on task!

It does this with a long prompt, that updates as you change web pages, and returns JSON with a decision whether to notify the user, and if so, what message to show. Crucially, right now it just looks at the URLs being used. It could be improved by passing in the HTML, which would include things like the Youtube video title (which is needed for proper context) at the cost of a lot of tokens.

Here is the full prompt:
```text
`You are a productivity assistant. You will receive the following:
    - a User Goal that is being achieved over a set number of minutes
    - the current URL of the user
    - a list of all URLs that are open in Chrome
    
    You will be called each time the Current URL changes.

    You will respond with one of the following:
    - Nudge, and a short message. If the current URL the user just clicked on does not seem relevant to the goal, this nudge will send a little popup and show the message, which encourages the user to get back on task. Twitter and Reddit are almost always bad. Pages with chrome:// are good. Chatgpt and Claude are good.
    - Nothing. We don't want to bother our user, since this is for productivity. So if they seem to be working on their goal, you don't need to return anything!

    
    User Goal: ${goalText}
    Current URL: ${currentURL}
    All URLs: ${openUrls}

  Respond only with JSON format:
  {
      "Notify": boolean,   // Whether notification is needed
      "message": string,   // The message content for the user
      "rationale": string  // The reasoning
  }`;
```

Right now, this is far from a real consumer product. It's just a proof of concept for an interesting problem that I think a lot of people are facing! Others at the hackathon were working on similar products, so please reach out if you want to iterate on something like this!

### What it looks like:

#TODO push last updates to github
![Lock In's main interface](/lockin_UI.png)
![When the user is in focus mode](/lockin_UI_2.png)
![When the user gets notified](/lockin_nudge.png)
