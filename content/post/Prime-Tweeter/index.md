+++
author = "Jonatan Holmgren"
title = "I tweet 24 times a day. Every single day."
date = "2022-03-23"
description = "I recently started tweeting prime numbers. Fun."
+++
## What?!
You hear me right, I tweet every hour the next prime number.

## Where?
[Here](https://twitter.com/JontesTweets)

## The Python script!
```python
import tweepy as tp
import time
import os

# credentials to login to twitter api
consumer_key = 'removed'
consumer_secret = 'removed'
access_token = 'removed'
access_secret = 'removed'

# login to twitter account api
auth = tp.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_secret)
api = tp.API(auth)

# checking for prime
def is_prime(n):
   if n <= 1:
      return False
   else:
      for i in range(2, n):
         # checking for factor
         if n % i == 0:
            # return False
            return False
      # returning True
   return True

def onsuccess(winner):
    file = open("lastprime.txt", "w")
    file.write(winner)
    file.close
    api.update_status("The next prime number is..."+winner+" Come back in hour for the next number!")

file = open("lastprime.txt", "r")
tempstring = file.read()
trynumber = int(tempstring)
file.close
success = False

while success == False:
  trynumber += 1
  if is_prime(trynumber):
   success = True
   onsuccess(str(trynumber))
```
## The breakdown of how it works
It opens the text file `lastprime.txt`, generates the next prime number by pure brute force, saves the "winner" number to `lastprime.txt`, and then tweets it!

## How I run it
I could've done this with an infinite loop and running it in a `screen`session like my other bots, but I felt like this was not required. So I made the following cron job!
```crontab
0 * * * * python3 /home/jonte/bot/prime-tweets/prime.py
```

## The API problems.
Dare I, without Twitter revoking my access, say that their API was HELL to configure. I had to apply for 2 different things, downgrade to API level 1 and do a bunch of different stuff with the keys seen above. But I think I have wrapped my head around it, so just contact me at [support@jontes.page](mailto:support@jontes.page) if you need this done.

## The conclusion
It was a fun afternoon project, and now it's going. I believe this is really really cool.

Kind Regards, Jonte.