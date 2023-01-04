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


<iframe src="https://www.kaggle.com/embed/bilalelebi/pdf-article-summarization-with-longt5?kernelSessionId=114783188" height="11175" style="margin: 0 auto; width: 100%; max-width: 950px;" frameborder="0" scrolling="auto" title="PDF Article Summarization with LongT5"></iframe>


First, we need the download our dependencies. We need ***Transformers*** for model and ***PyPDF2*** for extracting text from PDF's. You gonna see the other libraries I put them for other purposes that I will made in next couple of days or week... I don't know.
And then you seeing two functions, ***clean_text*** and ***get_text***. clean_text will cleaning text from urls, emojis, unicodes and punctutaions and get_text will reach the pdf, extracting text and then cleaning it.

***bulk_extract*** is the function for a stack task. You export as many files as you want to this function and it gives you the files in a list with all the text.

***get_pipeline*** will prepare model for-ready way. This is the first way to getting model from HugginFace and preparing it. It'e easy because of transformers library. pipeline method downloading model from huggingface and make ready for use. Once the pipeline is set up, all you have to do is give the text to the pipeline.

***summarize*** will summarize texts that you give it.

But. As I say past this is the easy way and less efficient/quality way. I'm liking more manual way. Here it is.

***load_model_and_tokenizer***  will download model and tokenizer files to local and prepared it for using.  We check whether the CUDA technology is suitable. CUDA makes processes faster, especially in machine learning. It is NVIDIA technology and therefore only available on NVIDIA GPUs. With this technology, machine learning, deep learning and studies related to sub-topics can become faster. Models can work quickly and be trained.

On the other hand, ***summarize_and_score*** will send the data given to it to the model and decode the data from the model and make it meaningful.

***summarize_long*** will encode the text given to it and then send it to the ***summarize_and_score*** method and get the output. The model will give more than one output related to the text given to it and each output will have a different success score. You will see a solution to this in the future.

***get_best*** and ***get_median*** is the two methods that sort outputs by score and return one of them as you want. ***get_best*** method give you the one that have most higher score than the others and ***get_median***  will return the middle one of the given output list (which will return as a json or dict).

***bulk_summarize***  will extract the texts from the given files and summarize them. This is the just extended version of ***bulk_extract***.

***apply*** is for you. You don't need prepare so much thing about this notebook. Just take pdfs into the your directory upload directory kaggle or google colab than give your directory path to this action with the other variables witch:

-	**method** for which way you wanna use 'pipeline' or 'other'.
-	**choose_method** which selecting method that you wanna use. for ***get_best*** use ***'best'*** for ***get_median*** use ***'median'*** .
-	**save** if you wanna save model outputs to the txt file. Just give that variable as ***True***.


### Conclusion ###

At the end of all this I gave the model a few PDFs and here are the results

> In this paper, the results of an experiment are not proven. A customer's perception of ad-interaction or personalization is inconsistent with experimental results from Wright and Campbell, Kurtz, and Alalvan. The effect of entertainment and credence on attitude towards advertisements also does not seem to be important in determining customers' attitudes toward ads. However, the study uses a theoretical framework to examine the relationship between these constructs and the influence of advertisement on purchase intentions in emerging market countries. This paper concludes by establishing that the most important theoretical contributions are to the understanding of the power of Facebook advertising upon purchase intention. It furthermore establishes that there are other characteristics that contribute to the impact of social advertising on purchasing intentions.

> In this paper, the effects of social media on purchase decisions are examined. The results show that brand trust plays a significant role in predicting purchases. Brand trust is also a strong predictor of purchasing decisions. This paper furthermore examines the effect of various features of social-media advertising on buying decisions. It finds that brandtrust is a key predictor for purchase decision.

> In this paper, Anderson focuses on three main areas of social science: advertising studies, technology adoption, and future research. He discusses the use of social co-gnitivity theory to explain why people act in certain ways.

> In this paper, Richard focuses on creating a culture in which employees are encouraged to learn and develop. He emphasizes the importance of having a learning environment at the organization where everyone is able to share success stories and learn from one another. He also discusses challenges that may arise when there is no formal training or development being carried out. These include lack of knowledge about the nature of training and how it is done; lack of incentive for employees to participate in training and improvement; and lack of information concerning employee training and developments. Finally, he suggests that managers should make sure that they have adequate access to information concerning worker training and development so that they can better inform their employees about these issues.

> In this paper, Richard focuses on creating a culture in which employees are encouraged to learn and develop. He emphasizes the importance of having a learning environment at the organization where everyone is able to share success stories and learn from one another. He also discusses challenges that may arise when there is no formal training or development being carried out. These include lack of knowledge about the nature of training and how it is done; lack of incentive for employees to participate in training and improvement; and lack of information concerning employee training and developments. Finally, he suggests that managers should make sure that they have adequate access to information concerning worker training and development so that they can better inform their employees about these issues.

> In this paper, Anderson focuses on the concept of "proactive development" and how it can be used to support employee growth. He discusses the importance of having employees have access to information about their future tasks and job options so that they can make informed decisions about what kinds of activities will be most beneficial for them. This includes providing employees with opportunities to develop themselves through formal and informal means. However, there are still some concerns about whether or not these forms of development are truly effective. For instance, an employee who completes a national exam may gain more knowledge than one who does not take the exam directly. Furthermore, social media such as Facebook and LinkedIn could lead to increased risk of mistrust among employees. Finally, Anderson suggests that employers should encourage employees to become more active in their professional endeavors.

> In this paper, we examine the effects of psychological and behavioural engagement on social-media engagement. We find that psychological engagement influences both behavior and engagement in the same way as those involved in physical engagement. This is interesting because it suggests that there may be a direct relationship between psychological engagement and behavior. Furthermore, we find that UGC exerts the strongest influence on psychological engagement. However, behavioral engagement does not seem to have any significant effect on either engagement or interaction.

> In this paper, we describe the use of a single-preferred variant as a predictor of future occurrences of arrhythmogenic myopathies. We discuss the pros and cons of testing for ACM-specific genetic variants in order to determine which ones are most likely to cause heart failure. The aim of this paper is to present a detailed description of the different types of cardiomyopathieses that can be associated with one another. These include left ventricular noncompaction, right ventricular conduction disease, acute myomyopathy, and barth syndrome.


I gave the model pages and pages of articles I got from ResearchGate on various topics, and it gave me these acronyms, each of which was relevant.

But, let's talk about the benefits of reading articles as well as other benefits.

The act of searching and finding for articles is very difficult especially when you want a good article about topic that you want. There are millions of articles on [ResearchGate](https://www.researchgate.net/) and [Academia](https://academia.edu/) and thousands of other websites. But that's not the most breaking thing about these articles. The uselessness of abstracts.
I think that this model's explanation of articles that can reach tens or even hundreds of pages in such a few sentences shows that this situation can be used in the writing of explanatory and short abstracts related to the articles.
And besides, I think that these summarizations, which cover the entire article, can be used as a parameter in the Search function within the sites for better Search exprience for user.

Thank you for reading. I leave the Kaggle link so that you can use the notebook I wrote below.

[My Notebook](https://www.kaggle.com/code/bilalelebi/pdf-article-summarization-with-longt5?scriptVersionId=114783188)
