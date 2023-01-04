---
layout: post
title: Movie Recommendation with Content-Based Filtering.
subtitle: We creating a system for recommending movies by their metadatas with using Content-Based Filtering and TF-IDF.
tags: [recommendation system, movie recommendation, movies dataset, tfidf-vectorizer]
comments: true
---

### Movie Recommendation with Content-Based Recommendation Method ###

When I see Movies Dataset at couple days ago, I decided to make recommendation system for recommending movies.
I created a system that can recommend you a movie by given movie title or description.

### First, What is Content-Based Filtering? ###

Content-based filtering. It is a recommendation system that takes the content you like before and offers you close content about the content you like.
***For example***, you liked an article on Medium and gave it a round of applause. On your next visit or on that page, medium will encourage you to read even more by suggesting new articles related to that article you applauded. This is the most basic definition of content-based filtering.

### So, How to Do That? ###

Content-based filtering basically requires a content. This content must be a text data. The title of a movie or the recipe for a dish, anything with text.
Since we are going to make a movie recommendation here, I have turned the titles and short descriptions of the movies into metadata. Our content here will be this metadata we created.

<iframe src="https://www.kaggle.com/embed/bilalelebi/movie-recommendation-content-based-method?cellIds=14&kernelSessionId=115496180" height="400" style="margin: 0 auto; width: 100%; max-width: 1000px;" frameborder="0" scrolling="auto" title="Movie Recommendation - Content-Based Method"></iframe>

Here it is. That cell shown to you how I created metadata of movies. I merge title and overview (movie description in imdb) and tagline in one text.

<iframe src="https://www.kaggle.com/embed/bilalelebi/movie-recommendation-content-based-method?cellIds=25&kernelSessionId=115496180" height="300" style="margin: 0 auto; width: 100%; max-width: 950px;" frameborder="0" scrolling="auto" title="Movie Recommendation - Content-Based Method"></iframe>

Here I am correcting the some corruption in the indexes after deleting some empty rows of the dataset.

<iframe src="https://www.kaggle.com/embed/bilalelebi/movie-recommendation-content-based-method?cellIds=26-27&kernelSessionId=115496180" height="250" style="margin: 0 auto; width: 100%; max-width: 950px;" frameborder="0" scrolling="auto" title="Movie Recommendation - Content-Based Method"></iframe>


Here, I turn my dataset into a matrix for content-based filtering with using TF-IDF Vectorizer. Then I group the data close to each other in this matrix with the cosine similarity algorithm.
And next cell, I created indices series for mapping. Why I need mapping? Because after recommendation algoritm we need the find which movie recommended to us and show it's title.


<iframe src="https://www.kaggle.com/embed/bilalelebi/movie-recommendation-content-based-method?cellIds=28&kernelSessionId=115496180" height="365" style="margin: 0 auto; width: 100%; max-width: 950px;" frameborder="0" scrolling="auto" title="Movie Recommendation - Content-Based Method"></iframe>


Here is the recommendation function. In that function, we taking a overview value and then we finding this overview index on index map that created previous cell. After finding the metadata itself in the data set, we go to the list we grouped with cosines-similarity to find the group this index is in. After finding group, first we sorting group with their distance to given overview value then we taking indexes of these returned values in representend real dataset.
And in last cell, we returning titles of movies by returned indexes from grouped data. In order to do this, it is enough to send these returned indexes to the data set, it will return us the title value in the desired index in the data set.

<iframe src="https://www.kaggle.com/embed/bilalelebi/movie-recommendation-content-based-method?cellIds=29&kernelSessionId=115496180" height="650" style="margin: 0 auto; width: 100%; max-width: 950px;" frameborder="0" scrolling="auto" title="Movie Recommendation - Content-Based Method"></iframe>

And here it is. This is the example that we tried. It's seems good. We give it American Psycho and then it returned to us couple of scary and scary-comedy movies and one or two thriller movie.

If you wanna try some movie for getting some recommendation you can try my kaggle notebook on [here](https://www.kaggle.com/code/bilalelebi/movie-recommendation-content-based-method).

Thx for reading. Have a nice day.:v:

