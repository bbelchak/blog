+++
date = "2011-01-19"
slug = "2011/01/19/problems-with-facebook-api-and-m2crypto"
title = "problems with facebook api and m2crypto"
Categories = ["Technology"]
Tags = ["python django"]
+++

After doing some crypto updates to a django application that I am working on, I discovered that the Facebook API was dog slow for retrieving any query using HTTPS. Turns out that the M2Crypto library apparently hijacks the SSL processing of urllib and mucks everything up. Thanks to [this handy blog post](http://hustoknow.blogspot.com/2011/01/m2crypto-and-facebooks-sdk-hangs.html), I was able to fix my Python implementation of the Facebook API and get things speeding along again.

The fix is basically to add the following lines before any `urllib.urlopen()` call (in my case, I only have two - one for GET and one for POST):
```python
urllib._urlopener = urllib.FancyURLopener()
urllib._urlopener.addheader('Connection', 'close')
```
