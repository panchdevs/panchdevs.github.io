---
layout: post
title:  "Tweet cleaner upgrades"
date:   2015-03-19 10:16:23
categories:
---

Hey there!

If you've been following the blogposts, you know how much we've done so far.

In this post we'll be explaining exactly what we're doing to the tweets.
Right from when we get the tweets to how we process it.
On the whole, its simple, although it might get somewhat time consuming when we start processing the tweets in real-time.

Cleaning up of the tweets is necessary as

1. people tend to go overboard with the hashtags, they add many in the same tweet
2. they use in both uppercase and lowercase letters in the same word
3. they share links
4. they use short forms and abbreviations
5. they use emoticons

All of these will hamper the sentiment analysis.
They complicate matters unless we change the tweets in such a way that the analysis can be done a bit more easily.

As we have mentioned in the [previous post](/2015/03/13/the-progress-so-far.html), currently, we are doing the following

1. changing the entire case of the tweet into lower case
2. replacing the `@name` mention with `"AT_USER"`
3. replacing urls like `www.xyz.com` or anything starting with `http://` with `"URL"`
4. replacing the `#hashtags` with `"hashtags"`, removing the `'#'` symbol
5. removing additional punctuations and whitespaces

## Next Step

We are working out the details for cleaning the tweets based on the emoticons and the shortforms.
Emoticons will be easy to handle, we can replace them with `POSITIVE` or `NEGATIVE` along with a number representing the level of the sentiment follwed by `EMOTICON` based on the polarity of the emoticon.

For example

- `:)` will become `POSITIVE1 EMOTICON`
- `:D` will become `POSITIVE2 EMOTICON`
- `:(` will become `NEGATIVE1 EMOTICON`
- `:'(` will become `NEGATIVE2 EMOTICON` etc.

But the issue comes with the shortforms.
You see, shortforms, can be expanded into anything.
The simplest example would be, `atm` which can be expanded into `at the moment` or `automatic teller machine`.
Another issue with shortforms is that there are hundreds of shortforms, so each one has to be added separately. 

Another challenge comes in the form of non-english words, like words specific to some language, or words that make no sense, or images that are drawn using punctuations like, `Ciao`, `Sayonara`, `karazee`, `bloop`, `(^o^)`, `(^u^)` etc.

## Examples

Since the details are still in discussion, when it comes to the shortforms and non-english words, let me show you a few examples of tweets being cleaned using the methods described in the previous blogpost along with the emoticons being replaced.

> RIP to @robinwilliams, he was an INSPIRATION to us all, :(  :'( #restinpiece

This will be changed into

	rip to @robinwilliams, he was an inpiration to us all, :( :'( #restinpiece

then into,

	rip to AT_USER, he was an inspiration to us all, :( :'( #restinpiece

then,

	rip to AT_USER, he was an inspiration to us all, :( :'( restinpiece

and finally,

	rip to AT_USER, he was an inpiration to us all, NEGATIVE1 EMOTICON NEGATIVE2 EMOTICON restinpiece

> Lolzz @AIB Gr8 job making ur vids, they r awsm!!!!!!!!!!!!!!!! :D XD

Similarly the second example will be cleaned to
	
	lolzz AT_USER gr8 job making ur vids, they r awsm! POSITIVE2 EMOTICON POSITIVE3 EMOTICON

You can see that in both examples, we have non english words, namely, `restinpiece`, `lolzz`, `gr8`, `ur`, `vids`, `r` and `awsm`.

The words are non-english since they dont make sense when compared to a dictionary and since they are shortforms, they will have to be replaced too, to make sense of it.
restinpiece being taken as one word will be difficult for the algorithm to process.

This blogpost is basically to help you understand what problems we still face with the cleaning up of the tweets. but this algorithm we have uploaded now, is basically a protoype, we are still working on it to include all the extra features we have addressed in this post.

The next post will again address the different methods of performing the sentiment analysis, along with more techniques for it.

*Stay tuned for more!*
