---
layout: post
title:  "Collecting tweets"
date:   2015-02-12 19:12:23
categories:
---
*Good news readers!*

We have started programming.

A few days ago we finished writing a script which collects tweets from the [Twitter](https://twitter.com) API for us.
This is an important milestone for us because we need these tweets to prepare our training dataset.
The next step will be to label these tweets as positive, negative or neutral according to their sentiment.
We'll talk more about that in a later post.
Right now, we'll be telling you how our tweet collector script works and how we wrote it.

## How it works

The way the script works is quite simple.

- First it sets up a connection with the [Twitter Streaming API](https://dev.twitter.com/streaming/overview).
- The script then makes a request to the API asking for a sample of English language tweets.
- The Twitter API then proceeds to satisfy the request and sends us any public tweets like that as they come along.
- The script receives each tweet one by one, finds the data we need and then stores it in a database.

## Setting it all up

We had decided to program this in [python](https://www.python.org/).
But before we could start programming, we had to get an access token from Twitter first.
This is necessary to use the API.
This was easy to do and we won't describe the steps here.
However, if you're interested in knowing how to do this, you can find a helpful guide [here](http://www.74by2.com/2014/06/easily-get-twitter-api-key-api-secret-access-token-access-secret-pictures/).

The next step was to install the libraries that we were going to use.
We used [Tweepy](http://www.tweepy.org) for easy access to the Twitter API and [PyMongo](http://api.mongodb.org/python/current/) to use MongoDB with python.
We installed both of these with pip.

	pip install tweepy
	pip install pymongo

We chose [MongoDB](http://www.mongodb.org/) as our database because we felt a [schemaless database](http://blog.mongodb.org/post/119945109/why-schemaless) would be a better fit for the data than a relational DBMS like MySQL.
Also, we intend to use MongoDB's MapReduce capabilities at a later stage.

## Writing code

Now comes the programming part.

There are just two files that make up the whole tweet collection program.
We'll go over both of them.
You can find the complete code for both files in [the project's GitHub repository](https://github.com/panchdevs/twitter-analysis).

```collector.py```

Tweepy contains the ```StreamListener``` class to use with the Streaming API.
All we have to do is create an instance of this class to receive tweets.
We decided to create a subclass of this called ```TweetCollector``` and added the functionality to store tweets in the database to it.
You'll find four methods in this class:

1. ```__init__()```  
This is called when we create an instance of this class and is used to initialize the number of tweets to collect and what collection to store the tweets in.

2. ```on_status()```  
This method is called whenever we receive a tweet from Twitter. In this method we store the tweet in the collection and call ```limit_reached()``` to check if we have collected the required number of tweets. If this method return ```False``` we stop collecting tweets.

3. ```on_error()```  
This one is pretty obvious. If there is some error we simply print it to stdout.

4. ```limit_reached()```  
This method checks if we have collected the required number of tweets or not.

In the next file you will see we create an instance of this subclass to collect our tweets.

```tweet_collector.py```

This is file that we actually run to collect tweets.
In this file we,

1. import the necessary classes from different modules (including ```TweetCollector``` from ```collector.py```)
2. define our keys access tokens to use for authenticating with the API
3. set the host address and port number of the MongoDB database
4. add our keys to the OAuthHandler and set the access token
5. connect to the database and tell ```TweetCollector``` what MongoDB collection we are using to store the tweets
6. connect to the Streaming API and request a sample of English language tweets


*That's all for now. We'll continue collecting tweets with this script and start work on labelling them. As soon as there is some progress we'll have another blog post ready for you.*
