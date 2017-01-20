# Historical tweets crawler

### Author: Bisheng Huang


## Background
Twitter has released series of APIs for developers to get twitter data. But currently the twitter search API only provides 7 days of historical data related to a certain keyword. And it might be hard to get tweets earlier using this approach.

However, when searches are performed on the [Twitter search website](https://twitter.com/search-home), the returned results will contain tweets that come from many days and even months ago. 

## The hidden API
After studing the requests and responses of the search website carefully, a hidden API can be found at the URL: https://twitter.com/i/search/timeline

To use this API, one has to provide these parameters:
q: the query word and some search options
max_position: the upper bound of the tweet id that will return, and the request token

The API will return 20 tweets that satisfied these parameters. The result is in JSON format, and the tweets will be contained in the content of the key "items_html". These tweets contents in HTML format were intended to be inserted into the search page website to provide more search results, but now we just extracted from them the information we are interested in: tweet id, tweet text, tweet time, etc. 

Using the hidden API, for each keyword we search, we will get fewer search results (about several hundreds tweets per day) than using the official API (more than one thousand).

## Code Instructions

Up till now(2017-01-19), this hidden API still works.

```
python grab_historical_tweets.py
python combine_files.py
```

Check the code for more details. 