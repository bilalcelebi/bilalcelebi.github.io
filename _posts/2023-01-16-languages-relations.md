---
layout: post
title: Analyzing Relations Between Human Languages
subtitle: In this post we gonna analyze relationship between human languages with using Python.
tags: [python, plotly, pandas, languages, linguistic, EDA, data visualization, data exploration]
comments: true
---

### Relations Between Languges ###

Many languages have developed throughout human history, we have developed thousands of languages in hundreds of ways to express each other. Language is a tool at the root of communication, and what we thought was made up of words actually started with imitating the sounds around us, and thousands of years later, here we are continuing to develop civilization with thousands of languages and tens of thousands of dialects and dialects (ağız) of those languages.

Although people see languages as separate things due to the difficulty of learning, all languages in human history are in some way related to each other. While some languages have reached the status of a language while being a dialect of another language, some languages have developed relationships such as giving words to other languages. Of course, we are the ones who do all this. We have to think of it as a process, the result of events throughout life that created these languages and they are here now and we are speaking.

But I will not describe the historical process and development of language here. Here, I will give you a general analysis of the relations between languages with a data set that contains a huge amount of data about the relations between languages.

Let's move this forward in a question-and-answer format, then.

***Which languages have the highest relationship to each other?***

<iframe src="https://www.kaggle.com/embed/bilalelebi/analyzing-relations-between-languages?cellIds=54&kernelSessionId=116453246" height="300" style="margin: 0 auto; width: 100%; max-width: 1500px;" frameborder="0" scrolling="auto" title="Analyzing Language Relations with Etymology"></iframe>

In the chart above, I have shown the first 20 language groups that are etymologically highly interconnected. As I observed in the dataset I created myself, Latin also shows itself in European languages. He seems to have had a great influence on English and Italian in particular. There is also a serious relationship between English and Ancient Greek, I wondered how this came about. Another situation seen in the graph is the relations of the languages themselves with their ancient or medieval versions. This is very normal, we have seen it in the previous dataset. A process is taking place, the society is constantly changing the language by speaking, although after a while languages become much different from their previous states, they maintain their relations with them both on the basis of derivation and meaning. The reason why Italian and Latin are so related is Rome (Indeed, all roads lead to Rome!.) again, because Rome was a state that was founded, developed and ruled on the Italian peninsula, so it is the Latin that was spoken by the Italian speaking people before. It makes sense to have a connection. People switch to a new language and come back with remnants of their previous language. In addition to all these, today's Italian was a Latin dialect spoken in Tuscany centuries ago.

##### Let's Looking for Turkish (My Language) #####

<iframe src="https://www.kaggle.com/embed/bilalelebi/analyzing-relations-between-languages?cellIds=56&kernelSessionId=116453246" height="300" style="margin: 0 auto; width: 100%; max-width: 1350px;" frameborder="0" scrolling="auto" title="Analyzing Language Relations with Etymology"></iframe>


The languages that Turkish is most associated with are Ottoman Turkish, Arabic and French, as everyone knows. The reasons for this are clear, our relations with the Arabs, our being a continuation of the Ottoman Society and our tendency towards French in the Tanzimat Period. But let's look at other languages. I think that the relationship between Serbian and Ottoman Turkish may have been caused by the Ottoman domination of the Balkans, which lasted for 600 years, and if we add to this thought the resettlement policy that started during the reign of Fatih Sultan Mehmet, it seems normal for such an event to occur. Turks who went to the Balkans with the resettlement merged with the Serbs in the process, so such a linguistic exchange makes sense. In addition, we can see the connection of both modern Turkish and Ottoman Turkish with the language that is shown as the origin of all Turkish called Proto-Turkic (a pure Turkish dating back to Altai and Uyghurs). Its relations with Turkish and other Turkic languages, Kazakh, Altai, are also visible. The connection of Ottoman Turkish with the languages spoken today in the lands under the domination of the Ottoman Empire (especially where it had long-term dominance) can be noticed here. Arabic, Serbian, Armenian and Romanian are some of them. Although not very high, the link between Turkish and Ancient Greek can be seen. Since the Hellenes are two nations with a long and serious dialogue, a linguistic exchange feels normal. Finally, the relationship between Azerbaijani and Bashkir, which is spoken by the ethnic population called Bashkirs, a people living in the Caucasus region of Russia today, is also high. When we look at these two languages, our ties with Azerbaijani are due to the fact that both languages have proto-turkic roots and Latin alphabet. I need to examine the connection with Bashkir a little more, let's do it then.

<iframe src="https://www.kaggle.com/embed/bilalelebi/analyzing-relations-between-languages?cellIds=60&kernelSessionId=116453246" height="300" style="margin: 0 auto; width: 100%; max-width: 1200px;" frameborder="0" scrolling="auto" title="Analyzing Language Relations with Etymology"></iframe>


As can be seen above, the two languages have a relationship stemming from their origins in Proto-Turkic, that is, Self-Turkish. Besides, Bashkir has acquired a lot of words from Turkish in terms of origin. Briefly, cognate_of explains that Bashkir has 597 synonyms from Turkish in terms of meaning/origin, while Turkish has 182 synonyms from Bashkir in terms of origin. But in general, we can say that their relationship stems from the fact that they are both languages coming from Main-Turkish (Proto-Turkic that mean Altai roots).



***What are the predominant types of relations between languages?***

<iframe src="https://www.kaggle.com/embed/bilalelebi/analyzing-relations-between-languages?cellIds=62&kernelSessionId=116453246" height="300" style="margin: 0 auto; width: 100%; max-width: 1500px;" frameborder="0" scrolling="auto" title="Analyzing Language Relations with Etymology"></iframe>

There seems to be a high degree of origin, derivation, and inheritance among languages. There also seems to be a high tendency to borrow from other languages. Speakers of the language take words from other languages (this is usually previous colloquialisms) in the same way in sound and translate them into the current language, a borrowing situation. If you look at the spelling and pronunciation of these words, you will see almost no difference. I think that's why it's called borrowing and not related or cognate.


***Which languages have stronger relations to each other than other languages?***

<iframe src="https://www.kaggle.com/embed/bilalelebi/analyzing-relations-between-languages?cellIds=9&kernelSessionId=116453246" height="300" style="margin: 0 auto; width: 100%; max-width: 1350px;" frameborder="0" scrolling="auto" title="Analyzing Language Relations with Etymology"></iframe>


Slovak and Serbian seem to be linked to many languages. While Slovak has more ties with French, German and English, it seems to still maintain its ties with the old German language. Serbian, on the other hand, has a serious connection with Ottoman Turkish, Arabic, Persian and Latin. We can see it as a result of the Ottoman, Arabic and Persian connections remaining under Ottoman rule for a long time. Latin, which shows itself in the whole of the European language family, also showed its effect here. While noticing the impact of political events on the language, we can better realize the impact of geopolitical events on the language by looking at the link between the Azerbaijani language and Russian, and considering that Azerbaijan remained under USSR rule until 1992. In addition, the strong connection between our Turkish and Latin is not overlooked, of course, since we use the Latin alphabet, this connection is logical, but it was surprising not to see the connections between French, Arabic and Persian, which have given Turkish a lot of words. I can attribute this to the limited content of the data in Turkish. (I used here different dataset that my own creation.)


***What is relationships between languages on the basis of relationship types***

<iframe src="https://www.kaggle.com/embed/bilalelebi/analyzing-relations-between-languages?cellIds=14&kernelSessionId=116453246" height="300" style="margin: 0 auto; width: 100%; max-width: 2000px;" frameborder="0" scrolling="auto" title="Analyzing Language Relations with Etymology"></iframe>

Above, I examined languages on the basis of relations. The ***RelatedTo*** relationship expresses that a word in one language usually has the same meaning or is used for the same purpose as a word in another language. When we look at the RelatedTo relationship, we can see that the link between Chinese and English is strong. This means that words in Chinese that directly correspond or are linked in English, we will show some of these words below.

<iframe src="https://www.kaggle.com/embed/bilalelebi/analyzing-relations-between-languages?cellIds=17-19&kernelSessionId=116453246" height="500" style="margin: 0 auto; width: 100%; max-width: 1200px;" frameborder="0" scrolling="auto" title="Analyzing Language Relations with Etymology"></iframe>


Another type of relation is ***Etymologically Derived***. This type of relationship means that a word in one language is derived from a word in another language. For example, there are many words derived from Arabic and Persian words in Turkish, as well as from French. The meanings of these derived words may be the same or different, the common point here is that they are etymologically similar to each other. In other words, they are almost the same in terms of spelling and pronunciation. In the graph above, we can say that all European languages have derived from Latin, besides, there is a serious derivational relationship between Latin and Greek. I think it's because of Rome. In addition to deriving the Roman Empire religion from Greek mythology, I think it may also have derived Latin from Greek. Also, considering Rome's connection to ancient Greek cities, this makes sense to me. English has made derivations from ENM (Middle Age English) and ANG (Anglo-Saxon English) languages, which are its very previous versions. Besides English, Norwegian and Dutch seem to be among the languages that have taken a lot of derivations from their predecessors. In Asian languages, there is an Indo-Sanskrit derivation relationship. Sanskrit is one of the oldest languages of the Indo-European language family.

<iframe src="https://www.kaggle.com/embed/bilalelebi/analyzing-relations-between-languages?cellIds=21-28&kernelSessionId=116453246" height="500" style="margin: 0 auto; width: 100%; max-width: 950px;" frameborder="0" scrolling="auto" title="Analyzing Language Relations with Etymology"></iframe>

***Etymologically Related*** is called the link between two different words derived from the same place. Two separate words can be in the same language or in two different languages, if they are derived from a word in another language or in the same language, then those two words are related to each other in terms of origin. Related words can have the same or different meanings. Languages often have a strong relationship to ancient or lost languages here. The links with the past versions of the languages are very strong. In addition, languages that are powerful in every sense in the historical process show themselves here as well. Like Latin, Greek. Such languages were the language of correspondence thousands of years ago, but instead of being lost to ancient languages like themselves, they have continued their existence indirectly by passing on to other languages. Of course, the reason for this should also be examined on the basis of historical events. For example, I can say that the reason why Latin is so strong on European languages is Ancient Rome. Or I could say that the etymological connections between Latin and Greek are due to the high trade and wars between Rome and the Greek city-states. It is necessary to examine the changes in languages from many perspectives.

<iframe src="https://www.kaggle.com/embed/bilalelebi/analyzing-relations-between-languages?cellIds=31-34&kernelSessionId=116453246" height="500" style="margin: 0 auto; width: 100%; max-width: 950px;" frameborder="0" scrolling="auto" title="Analyzing Language Relations with Etymology"></iframe>

Languages will always be interconnected. At least we can deduce that from these analyses. We have come to the end of this article. In my next article, I plan to examine the effects of other languages in Turkish Conversations and Speech texts, in daily speech, and the reasons for this effect.

And If you wanna see full notebook and using dataset for your work you can reach this notebook from [here](https://www.kaggle.com/code/bilalelebi/analyzing-relations-between-languages).

Thx for reading. Have a nice life :)


