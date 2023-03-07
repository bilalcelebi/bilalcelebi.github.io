---
layout : post
title : Trying Language Models with Using Haystack Library
subtitle : We trying language models with using python Haystack Library and getting results easily.
tags : ['python','haystack','langauge models','huggingface']
comments: true
---

### Haystack Framework for Language Models ###

Haystack framework is a Python library created by DeepSet company for you to use language models more easily and comfortably.
You can perform many language model functions on Haystack. Since Haystack has the Huggingface link, you can use all Hugginface's Publicly Available language models.

***Let's Dive, How We Can Use It?***

First of all, we need to convert the data we have into a DocumentStore. DocumentStore is a Haystack class that allows you to use the data you have for the model. Before you can use the language models on Haystack, you need to convert them to a Document hosted in the DocumentStore. But don't worry, it's easy.

```python
from haystack.document_stores import ElasticsearchDocumentStore docs = []
for value in  list(df['content'].values):
	doc = { 'content':value }
	docs.append(doc)
document_store = ElasticsearchDocumentStore()
document_store.write_documents(docs)
```
In the code block you see above, I convert the text data in the content column into Document data one by one in the pandas dataframe, and finally I write this converted data into my DocumentStore.


***Ok, How About Loading and Using Models?***

As I said before, you can use all models on HuggingFace, but Haystack has a unique structure. I will explain it now. As an example, we'll use a QuestionGeneration model and create a Pipeline to obtain a Model Pipeline that derives questions from the data we have.

```python
from haystack.nodes import QuestionGenerator
from haystack.pipelines import QuestionGenerationPipeline

question_generator = QuestionGenerator()
pipeline = QuestionGenerationPipeline(question_generator)
```

Here's how Haystack simplifies what would normally take lines of code. In the code block above, we loaded a default ***QuestionGeneration*** model, then we sent this model to the ***QuestionGenerationPipeline*** class and now we have a pipeline that generates questions. You can apply this for other models, more applications are available on Haystack's own [website](https://haystack.deepset.ai/tutorials).

Besides that, I tried HayStack's library based on a few issues. Now I will share their results with you.


***Question Generation***

```text
 Generating Questions for 0 : LONDON  —   Britain’s opposition Labour Party, already reeling after voters defied its advice and ch


Generated questions:
 - What happened to Britain's opposition Labour Party on Tuesday?
 - Who lost a motion to leave the European Union?
 - What was the result of Corbyn's vote?
 - How many votes did the measure pass?
 - What does the measure open the way for?
 - Who has refused to step down?
 - What percentage of Labour members and supporters voted for Corbyn to resign?
 - What did Corbyn say after the vote by Labour members of Parliament has no constitutional legitimacy?
 - What is the democratic party with a clear constitution?
 - Who has been hit by the mass resignation of most of his leadership team?
 - What was Britain's vote to leave the European Union?
 - What party did the majority of Parliament members oppose leaving the union?
 - Who was the prime minister when he announced he would resign?
 - When did Cameron announce his resignation?
 - What party has a power struggle over who will succeed Corbyn?
 - What are many Labour lawmakers worried about?
 - In what year did Corbyn win the election?
 - Who was elected by the overwhelming majority of party members and supporters?
 - How shallow was Corbyn's support among lawmakers?
 - What was the party's policy in the referendum on European Union membership?
 - Who is the shadow chancellor of the Exchequer and the party's top spokesman on economic issues?
 - What did Mr. Corbyn urge Labour supporters to do?
 - What has the top spokesman on economic issues said about Mr. Corbyn?
 - Who has vowed to run his campaign if there were a new election among Labour Party members?
 - What have supporters of Mr.Corbyn called on his critics to do?
 - What is the final choice for Corbyn under the Labour Party system?
 - Who is the party that decides the winner?
 - What party does the final decision lie with?
 - Despite some indications that support for him is weakening, he would win what?
 ```

Above I gave QuestionGenerationPipeline a news article about the Labor Party and it generated questions about it for me.


***Document Answering***

```text
'WASHINGTON  —   Congressional Republicans have a new fear when it comes to their health care lawsuit against the Obama administration: They might win.
The incoming Trump administration could choose to no longer defend the executive branch against the suit, which challenges the administration’s authority to spend billions of dollars on health insurance subsidies for   and   Americans, handing House Republicans a big victory on    issues.
But a sudden loss of the disputed subsidies could conceivably cause the health care program to implode, leaving millions of people without access to health insurance before Republicans have prepared a replacement.
That could lead to chaos in the insurance market and spur a political backlash just as Republicans gain full control of the government.
To stave off that outcome, Republicans could find themselves in the awkward position of appropriating huge sums to temporarily prop up the Obama health care law, angering conservative voters who have been demanding an end to the law for years.
In another twist, Donald J. Trump’s administration, worried about preserving executive branch prerogatives, could choose to fight its Republican allies in the House on some central questions in the dispute. Eager to avoid an ugly political pileup, Republicans on Capitol Hill and the Trump transition team are gaming out how to handle the lawsuit, which, after the election, has been put in limbo until at least late February by the United States Court of Appeals for the District of Columbia Circuit.
They are not yet ready to divulge their strategy. “Given that this pending litigation involves the Obama administration and Congress, it would be inappropriate to comment,” said Phillip J. Blando, a spokesman for the Trump transition effort.
“Upon taking office, the Trump administration will evaluate this case and all related aspects of the Affordable Care Act. ” In a potentially   decision in 2015, Judge Rosemary M. Collyer ruled that House Republicans had the standing to sue the executive branch over a spending dispute and that the Obama administration had been distributing the health insurance subsidies, in violation of the Constitution, without approval from Congress.
The Justice Department, confident that Judge Collyer’s decision would be reversed, quickly appealed, and the subsidies have remained in place during the appeal. In successfully seeking a temporary halt in the proceedings after Mr. Trump won, House Republicans last month told the court that they “and the  ’s transition team currently are discussing potential options for resolution of this matter, to take effect after the  ’s inauguration on Jan. 20, 2017. ” The suspension of the case, House lawyers said, will “provide the   and his future administration time to consider whether to continue prosecuting or to otherwise resolve this appeal.
” Republican leadership officials in the House acknowledge the possibility of “cascading effects” if the   payments, which have totaled an estimated $13 billion, are suddenly stopped. Insurers that receive the subsidies in exchange for paying    costs such as deductibles and   for eligible consumers could race to drop coverage since they would be losing money. Over all, the loss of the subsidies could destabilize the entire program and cause a lack of confidence that leads other insurers to seek a quick exit as well.
Anticipating that the Trump administration might not be inclined to mount a vigorous fight against the House Republicans given the  ’s dim view of the health care law, a team of lawyers this month sought to intervene in the case on behalf of two participants in the health care program. In their request, the lawyers predicted that a deal between House Republicans and the new administration to dismiss or settle the case “will produce devastating consequences for the individuals who receive these reductions, as well as for the nation’s health insurance and health care systems generally. ” No matter what happens, House Republicans say, they want to prevail on two overarching concepts: the congressional power of the purse, and the right of Congress to sue the executive branch if it violates the Constitution regarding that spending power. House Republicans contend that Congress never appropriated the money for the subsidies, as required by the Constitution.
In the suit, which was initially championed by John A. Boehner, the House speaker at the time, and later in House committee reports, Republicans asserted that the administration, desperate for the funding, had required the Treasury Department to provide it despite widespread internal skepticism that the spending was proper.
The White House said that the spending was a permanent part of the law passed in 2010, and that no annual appropriation was required  —   even though the administration initially sought one. Just as important to House Republicans, Judge Collyer found that Congress had the standing to sue the White House on this issue  —   a ruling that many legal experts said was flawed  —   and they want that precedent to be set to restore congressional leverage over the executive branch. But on spending power and standing, the Trump administration may come under pressure from advocates of presidential authority to fight the House no matter their shared views on health care, since those precedents could have broad repercussions.
It is a complicated set of dynamics illustrating how a quick legal victory for the House in the Trump era might come with costs that Republicans never anticipated when they took on the Obama White House.'
```

I asked a Document Answering pipeline I did above to return text for the word Washington, and it returned the text seen above.

***Machine Translation***

```json
{
	"real": "WASHINGTON — Congressional Republicans have a new fear when it comes to their health care lawsuit against the Obama administration: They might win. The incoming Trump administration could choose to no longer defend the executive branch against the suit, which challenges the administration’s authority to spend billions of dollars on health insurance subsidies for and Americans, handing House Republicans a big victory on issues. But a sudden loss of the disputed subsidies could conceivably cause the health care program to implode, leaving millions of people without access to health insurance before Republicans have prepared a replacement. That could lead to chaos in the insurance market and spur a political backlash just as Republicans gain full control of the government. To stave off that outcome, Republicans could find themselves in the awkward position of appropriating huge sums to temporarily prop up the Obama health care law, angering conservative voters who have been demanding an end to the law for years. In another twist, Donald J. Trump’s administration, worried about preserving executive branch prerogatives, could choose to fight its Republican allies in the House on some central questions in the dispute. Eager to avoid an ugly political pileup, Republicans on Capitol Hill and the Trump transition team are gaming out how to handle the lawsuit, which, after the election, has been put in limbo until at least late February by the United States Court of Appeals for the District of Columbia Circuit. They are not yet ready to divulge their strategy. “Given that this pending litigation involves the Obama administration and Congress, it would be inappropriate to comment,” said Phillip J. Blando, a spokesman for the Trump transition effort. “Upon taking office, the Trump administration will evaluate this case and all related aspects of the Affordable Care Act. ” In a potentially decision in 2015, Judge Rosemary M. Collyer ruled that House Republicans had the standing to sue the executive branch over a spending dispute and that the Obama administration had been distributing the health insurance subsidies, in violation of the Constitution, without approval from Congress. The Justice Department, confident that Judge Collyer’s decision would be reversed, quickly appealed, and the subsidies have remained in place during the appeal. In successfully seeking a temporary halt in the proceedings after Mr. Trump won, House Republicans last month told the court that they “and the ’s transition team currently are discussing potential options for resolution of this matter, to take effect after the ’s inauguration on Jan. 20, 2017. ” The suspension of the case, House lawyers said, will “provide the and his future administration time to consider whether to continue prosecuting or to otherwise resolve this appeal. ” Republican leadership officials in the House acknowledge the possibility of “cascading effects” if the payments, which have totaled an estimated $13 billion, are suddenly stopped. Insurers that receive the subsidies in exchange for paying costs such as deductibles and for eligible consumers could race to drop coverage since they would be losing money. Over all, the loss of the subsidies could destabilize the entire program and cause a lack of confidence that leads other insurers to seek a quick exit as well. Anticipating that the Trump administration might not be inclined to mount a vigorous fight against the House Republicans given the ’s dim view of the health care law, a team of lawyers this month sought to intervene in the case on behalf of two participants in the health care program. In their request, the lawyers predicted that a deal between House Republicans and the new administration to dismiss or settle the case “will produce devastating consequences for the individuals who receive these reductions, as well as for the nation’s health insurance and health care systems generally. ” No matter what happens, House Republicans say, they want to prevail on two overarching concepts: the congressional power of the purse, and the right of Congress to sue the executive branch if it violates the Constitution regarding that spending power. House Republicans contend that Congress never appropriated the money for the subsidies, as required by the Constitution. In the suit, which was initially championed by John A. Boehner, the House speaker at the time, and later in House committee reports, Republicans asserted that the administration, desperate for the funding, had required the Treasury Department to provide it despite widespread internal skepticism that the spending was proper. The White House said that the spending was a permanent part of the law passed in 2010, and that no annual appropriation was required — even though the administration initially sought one. Just as important to House Republicans, Judge Collyer found that Congress had the standing to sue the White House on this issue — a ruling that many legal experts said was flawed — and they want that precedent to be set to restore congressional leverage over the executive branch. But on spending power and standing, the Trump administration may come under pressure from advocates of presidential authority to fight the House no matter their shared views on health care, since those precedents could have broad repercussions. It is a complicated set of dynamics illustrating how a quick legal victory for the House in the Trump era might come with costs that Republicans never anticipated when they took on the Obama White House.",
	"translated": "Les républicains ont une nouvelle peur quand il vient à leur procès de soins de santé contre l'administration Obama : ils pourraient gagner. L'administration Trump entrante pourrait choisir de ne plus défendre la branche exécutive contre la poursuite, qui défie l'administration de dépenser des milliards de dollars sur les subventions d'assurance-maladie et les Américains, remettre à la Chambre républicaine une grande victoire sur les questions. Mais une perte soudaine des subventions contestées pourrait provoquer l'implosion du programme de soins de santé, laissant des millions de personnes sans accès à l'assurance-maladie avant que les républicains ont préparé un remplacement. Cela pourrait conduire au chaos dans le marché de l'assurance et déclencher un contrecoup politique juste au moment où les républicains obtiennent le plein contrôle du gouvernement."
}
```

Above, I gave an English news text to a Machine Translation pipeline and it returned me a French translation of that text. In the example above, you can see that the translation quality doesn't quite match Google Translate. Since it is Machine Translation, do not expect a very high quality translation, you can see a lot of incorrect translations, especially in texts that are not professionally written.


***Conclusion***

Frankly, I see Haystack as a Lego when it comes to using language models. You don't need to invent the parts, they come in the box. You just create pipelines by using these parts in the way you want, and you can get answers from this pipeline by giving a word, a document. This library that really makes things easy about Language models.
