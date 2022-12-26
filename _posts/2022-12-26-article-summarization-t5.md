---
layout: post
title: Article Summarization with Long-T5
subtitle: In this Post you gonna see summarizing PDF Articles with Long-T5 and Thoughts about selecting articles for Reading.
tags: [summarization, t5, article summarization, pdf summarization]
comments: true
---


### First, How I decide to do this? ###

I realized that I couldn't read a lot of articles because I started working intensively in the last months. There is no problem with reading books. Because for me, the act of reading a book is about thinking about what I read, as well as imagining it, and I can do this very comfortably. That's why people usually read their books before going to bed.
But reading articles is not like that. There is an action that is done and tried to be described in the articles, there is an idea being defended and you should be able to understand it. Using your knowledge and trying to read and understand properly, you have to think about what you want to give in the article, otherwise there is no point in having read it. An article is not read like a child who repeats words in first grade or like a bookworm who reads to say I have read it.
However, the energy and time it takes to read an article makes it an activity that is not/done very often by people. I read a lot of articles. But now I can't read much due to my busy schedule, and I can't understand much from what I read in my time slots. I have to read the article, understand it and think about it. I have to link to a new idea by taking the idea given in the article. This is my method.
Besides, that's not the whole problem. In addition to reading articles, it is very important for me to decide which article to read and to read effective articles. People are writing a lot of 'Viral' Articles these days.
I think I have taken the first step to find good articles and to get ideas from them without reading the article, although perhaps it is not a holistic and all-encompassing solution to the problem. And I'm going to show you that here today.

### So What did I do? ###

2 years ago, a model was introduced by Google that includes popular language model functions. T5.
The T5 language model can perform many functions on texts. It can abbreviate them, translate from one language to another, Check if a text is written correctly. It is a model that arouses excitement among engineers when it really came out.
And many engineers have prepared and trained datasets to fine-tune it to make it more suitable for their own purposes. Of all the fine-tuned models made, one model caught my attention a few weeks ago. The LongT5 is an extension of this model T5 and the idea came directly from Google. Normally, all language models can work on texts of a certain size/length. On average, 512 is a maximum of 1024 tokens. If you give it to the model to process a text longer than that, it will most likely give you an error.
However, LongT5 can work on all texts up to 30 thousand tokens long. The LongT5 model was prepared and presented months ago. A few weeks ago, I saw a HuggingFace member fine-tune the new LongT5 model, training and improving its function to shorten the given text, and that's when the idea came to my mind. ***Shortening articles***.


###  So, How I Did It? ###

I usually read my articles in PDF format. That's why what I'm doing here is by pulling data from PDFs but also from web pages and giving it to the Model, or let's say anything that contains Text. We can scrape articles from Medium or any website. I will do this in the future, but today I went through PDFs to take the first step.

First I scraped texts from PDFs. You just need to get the raw text. No templates, images, or other UNICODE stuff.
Then I started cleaning the raw text I got. I deleted URLs, deleted special characters, deleted what we call punctuation (characters like ?,!,(),[]). And I made the text so that I can give it to the model. You can actually give the raw text, but it will hinder the quality of the output, so it is necessary to overhaul the texts.

After clearing my texts, I made my model ready. I made the model usable in two ways. The first is the 'pipeline' function, which is a convenience offered by the transformers library, and the other is a slightly more technical way, which I think gives better quality outputs. Pipeline is a little more ready-made way.
The last step is easy, you give the texts to the model and it gives you a text that tells you in just a few sentences what is being said in that long text you gave.

### Let's Go Deep, Shall We? ###

<iframe id="rendered-kernel-content" src="https://www.kaggleusercontent.com/kf/114783188/eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0JDLUhTMjU2In0..kiE-7pu-rNOswjgLSZHETg.bwXF_9gz4f1asAwRjif-nuMzMx9YFYd_n0wJK-ODrVphoBEsjuJBd-iWWDbrpdBnHLHoTRHtZtaXiPoGf5s8aM7Dmcjn-4f82VcnfrcW9ucQ-mU8DyGG7ozuGOfsINFc78jrxqaVHWiSQyN4AAVwbUtm8PtXelQo7guCQO6p76cdJENydKyxSqVXoIxgdulopJfz9aH9AJEqihADUxtQnTIw78BuNM-5NmCkUAjKPDYYdDxn4gTl69_XBaiQDxr3qmh5wI4fdZZCdEPi0c43GHpBR6ohDOWjulj1Eqjgzfy_3v193nQfUoto8DJDEu4qq5zId4AeY_wOWP5LynT08QMFoq8E4CdN6-oVIIdiRPPoqFJ1EPiGNrXnAJtOajpqNKoLHmTHDSf37IP0ipy1S1hFxPaHG_I9Jvu1I408ownNFcAnqKvlNABgDUCifDQSUzF7qcAp09OLJcf4y3U6qk7xFgEMgwx8S5NELLGnjHQw7RvDUp-0f5pcOmB7MwW9f7bsM-QsIW8Iwn2Fwboa5qr-FuNHe-TIuiPWTb-xHHDtVYKv1gT2kPC2nlccbkjvv-Cm8KoTdad2rkJCHOwTdSvfy40HUha32zuRGu_APW3IE-etuYJH1OW5wAquaLpzgNU7WWuCUuWgTLknTt2LktJEoTqSARtuaj75nMWIxxAPEKzKBUgVDBdv2fTyuXi9.kJua3V91iBsJUsdfpsL-fQ/__results__.html" scrolling="no" title="Main Notebook Content" class="sc-BSOkt cnNisg" style="height: 11882px; display: block;"></iframe>

So that you seee!
