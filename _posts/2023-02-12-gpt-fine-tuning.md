---
layout: post
title: Fine-Tuning GPT-2 For Idea Generation
subtitle: We fine-tuning GPT-2 with Huggingface Transformers Trainer for generating Business and Startup ideas.
tags: ['gpt2','trainer','huggingface','fine-tuning','transformers','startups','idea-generation','text-generation']
comments: true
---

### Fine-Tuning GPT-2 Base ###

You've heard of the GPT-2 Model. A language model for generating text data. The GPT-2 model is currently available via Huggingface. The current GPT-2 model trained with a given dataset will give you the usual answers on the data it was trained on. But what if we want the model to produce answers on a more specific topic and in a more specific way. There it will be necessary to do what we call fine-tuning, namely feeding the model with our own data.

***What is Fine-Tuning and How We do That?***

Fine-tuning basically means training/feeding a model (can be text or image any model) with the data you have (models are usually already trained on a particular dataset, the dataset you have must be different from the dataset from which the model was trained.)
The GPT-2 model will already derive an answer, but if we want it to respond in a more fictional story style, for example, we'll have to train it in that direction. We can do this, for example, by feeding it with fictional texts.
So how does the process work? First, we process the data we have and turn it into a HuggingFace dataset, then we pass the dataset through a function that translates the data we call tokenization into a language that the model can understand, and then the model is trained with this processed and tokenized data.
There are more manual, medium manual and almost automatic ways to do this. We'll go mid-manual and build our model with Trainer, a function offered by HuggingFace. With the Trainer function, our model will be automatically trained and saved with the data we process, but of course, we have to process the data ourselves.

***So, Let's do It***

In today's article, I will train the GPT-2 model to generate startup ideas for me with a dataset that already has more than 30 thousand startup ideas.

```python
train_size = int(len(data) * 0.8)
train_data = data[:train_size]
test_data = data[train_size:]
len(train_data), len(test_data)
```

First we splitting our data. Trainer need 2 pair data. One of them training data for training/feeding model and the other test/validation data for testing model effiency. In the code in above we splitting our pandas dataset two dataset, train and test.

```python
from transformers import DataCollatorForLanguageModeling, DataCollatorWithPadding, GPT2Tokenizer, GPT2LMHeadModel, Trainer, TrainingArguments, AutoConfig
from datasets import Dataset

model = GPT2LMHeadModel.from_pretrained('gpt2')
tokenizer = GPT2Tokenizer.from_pretrained('gpt2')
```

We download our model and our Tokenizer. We will tokenize our dataset via the tokenizer, but first there are a few more steps we need to do.

```python
bos = '<|endoftext|>'
eos = '<|EOS|>'
pad = '<|pad|>'

special_tokens_dict = {'eos_token': eos, 'bos_token': bos, 'pad_token': pad}
num_add_tokens = tokenizer.add_special_tokens(special_tokens_dict)

config = AutoConfig.from_pretrained('gpt2',
                                    bos_token_id=tokenizer.bos_token_id,
                                    eos_token_id=tokenizer.eos_token_id,
                                    pad_token_id=tokenizer.pad_token_id,
                                    output_hidden_states=False)

model = GPT2LMHeadModel.from_pretrained('gpt2', config=config)
model.resize_token_embeddings(len(tokenizer))
```

We pass some custom tokens to the tokenizer so that we can notify the model of the beginning and end of each text data, and then re-adjust the model to fit with the new tokenizer.

```python
def prepare_data(data):

    response = []

    for pair in data:

        new_pair = bos + ' ' + str(pair) + ' ' + eos

        response.append(new_pair)

    return response

train_data = prepare_data(train_data)
test_data = prepare_data(test_data)
```

We wrote a function that will add the start and end tokens that we transferred to the tokenizer at the beginning and end of the text data, then we pass it through this function to adjust our datasets.

```python
train_data = pd.DataFrame(train_data)
train_data.columns = ['content']
test_data = pd.DataFrame(test_data)
test_data.columns = ['content']

train_dataset = Dataset.from_pandas(train_data[['content']])
test_dataset = Dataset.from_pandas(test_data[['content']])
```

the data we had was an array. We converted this array of data into a pandas dataframe, then converted the train and test dataframes into a HuggingFace dataset.

```python
def tokenize_func(example):

    return tokenizer(example['content'], padding = True)

tokenized_train_dataset = train_dataset.map(tokenize_func,
                                           batched = True,
                                           num_proc = 5,
                                           remove_columns = ['content'])

tokenized_test_dataset = test_dataset.map(tokenize_func,
                                         batched = True,
                                         num_proc = 5,
                                         remove_columns = ['content'])
 ```

We wrote a function to tokenize the text data, then using the map function of the huggingface dataset, we made each text data pass through this function and we tokenized our entire dataset.

```python
model_save_path = '/kaggle/working/fine_tuned_model'

training_args = TrainingArguments(
    output_dir=model_save_path,
    num_train_epochs=10,
    per_device_train_batch_size=16,
    per_device_eval_batch_size=8,
    warmup_steps=200,
    weight_decay=0.01,
    logging_dir=model_save_path,
    prediction_loss_only=True,
    save_steps=10000
    #report_to = 'wandb'
)

data_collator = DataCollatorForLanguageModeling(tokenizer = tokenizer, mlm = False)

trainer = Trainer(model = model,
                 args = training_args,
                 data_collator = data_collator,
                 train_dataset = tokenized_train_dataset,
                 eval_dataset = tokenized_test_dataset)

```

After creating the Trainer function with the TrainingArgument class, we created the arguments that the model will follow during the training, and we specified our model, datasets and of course our training arguments to this function.
But What is data_collator. Data Collator is for batching our datasets for training and evaluating process. It's like creating mini data pockets from our datasets and training and evaluating our model with these mini batches/pockets. If you looking full-manuel way of fine-tuning these language models you will understand what is batches.

```python
trainer.train()
trainer.evaluate()
trainer.save_model()
tokenizer.save_pretrained(model_save_path)
```

Above, we start the training process of the model by calling the train function of the Trainer class, and after the training is finished, we evaluate the model by calling the evaluate function and understand how good the model is, then we save the model and tokenizer in order to be able to use it later or upload it to the huggingface model hub.

Here is training metrics. Including training steps and and training loss.

|  500 | 8.586500 |
|-----:|---------:|
| 1000 | 2.486800 |
| 1500 | 2.390800 |
| 2000 | 2.292000 |
| 2500 | 2.254900 |
| 3000 | 2.195700 |
| 3500 | 2.146600 |
| 4000 | 2.123700 |
| 4500 | 2.070000 |
| 5000 | 2.053800 |
| 5500 | 2.031000 |
| 6000 | 1.990800 |
| 6500 | 1.982200 |
| 7000 | 1.970400 |
| 7500 | 1.946300 |

and there have evaluation metrics too in here.

```json
{'eval_loss': 2.634995460510254,
 'eval_runtime': 53.5724,
 'eval_samples_per_second': 117.747,
 'eval_steps_per_second': 7.373,
 'epoch': 10.0}
 ```


***Let's give a First Shot!***

```python
my_model = GPT2LMHeadModel.from_pretrained(model_save_path)
my_tokenizer = GPT2Tokenizer.from_pretrained(model_save_path)

input_text = my_tokenizer.bos_token
input_ids = my_tokenizer.encode(input_text, return_tensors = 'pt')
output = my_model.generate(input_ids, min_length = 20)
output = tokenizer.decode(output[0], skip_special_tokens = True)
real_output = str(output).split('.')
print(real_output[0] + '.')
```

In the code above, I loaded my trained model and adjusted tokenizer from my local folder, then sent the text data start token as an input to my model and cleaned and adjusted the result a bit, and here is the result.

```text
A startup that helps people find the best deals on flights,
hotels, and car rentals.
```

I think results are pretty good. My favorite thing about the trained model is that it completes the sentence because the normal model usually doesn't. And of course, what it derives from seems like a startup idea, not an irrelevant text.

For being sure lets making more generations. Here it is.

```text
A chatbot platform meant to help doctors make diagnoses.
It is a messaging platform with chatbots that is meant
to make patient care more efficient and less expensive.

A platform that helps people with their finances and personal goals,
allowing them to schedule their day and track their progress.
Using a mobile app, users can sign up and track progress and
earn rewards points based on that.

A company that helps companies create and customize video
advertising campaigns. They’re working on a new generation of
ad tech, taking it from simple to sophisticated ad software
to more sophisticated tools like Viacom advertising.
```
