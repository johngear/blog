---
title: "Chatting with a Philosophy Encyclopedia"
date: 2023-06-23T13:17:09-06:00
draft: false

tags: ['llms','alignment','philosophy']
ShowToc: false
ShowBreadCrumbs: true

---

<!-- # Hacking together a Philosophy Q&A Application! -->
# https://philosophy-chat.com/

Over the last few months, I've been working on a Q&A application for academic philosophy questions. I now have V1 deployed on the web! Please be patient, as it commonly fails after the first question and the runtime is ~10 seconds per question. But it works, and I'm proud of it.

This project was motivated by 1) my desire to personally use the site as a way to deepen my knowledge of philosophy and 2) as a proof-of-concept LLM application that can give sources and make up wrong information less. More than just giving an accurate answer, the program provides the sections of text that it references and links, so you could have a good jumping off point to clarify questions.

A slightly different (and older) version of the backend is publicly available on my [Github](https://github.com/johngear/Encyclopedia-GPT), and as I make the frontend and API code more readable, I may release it too. 

### A (short) technical description

I have an API written in Python Flask, which receives a question from a user, and returns a response. This is hosted on a Platform as a Service, and called from my Svelte frontend which is hosted via Netlify. 

Each paragraph from the Stanford Encyclopedia of Philosophy has been embedded and stored. When a user asks a question, it is embedded and compared to the entirety of SEP using [FAISS](https://github.com/facebookresearch/faiss), to find the most similar few paragraphs in our large dataset. A number of these paragraphs are appended to the question as factual context, and fed to the OpenAI API. The response is returned as well as a table of the paragraphs that were used as context for the model. 

Here's what it looks like (I'm clearly not a frontend guy ahah)
![Screenshot](/screenshot_new.png)