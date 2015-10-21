---
layout: post
title: "Scraping Github - Fetching Data from API (Part 2)"
permalink: scraping-github-2
date: 2015-10-19
author: Ratul Minhaz
summary: Learn to scrape data from API using Python
categories: learning
tags:
  - scraping
  - python
  - API
published: true
---

This is the second of a three part tutorial series on getting started with scraping data from Github: 
1. [The Setup]({{ site.baseurl}}/scraping-github-1)
2. [Fetching data from Github's API]({{ site.baseurl}}/scraping-github-2)

Are you ready to begin scraping? Definitely you are, you have set up all the tools needed. But the question is, what are you going to scrape? Remember the API I talked about last time?

## Exploring Github's API
Websites like Github and Facebook have API or Application Programming Interface so that you can interact with their services and data through your programs. They usually have extensive documentation on how to do this. In Github's [API documentation](https://developer.github.com/) you will see how to send requests to Github, what you will get in reply and how you can filter the reply for your specific needs. How about you check it out? Open up a new tab in the browser and go to the address _https://api.github.com/users/username_ with your own username in place of "username". You will see something similar to this:

{% highlight json %}
{
  "login": "mnzr",
  "id": 1234482,
  "avatar_url": "https://avatars.githubusercontent.com/u/1234482?v=3",
  "gravatar_id": "",
  "url": "https://api.github.com/users/mnzr",
  "html_url": "https://github.com/mnzr",
  ... ... ...
  ... ... ...
  "type": "User",
  "site_admin": false,
  "name": "Ratul Minhaz",
  "company": "",
  "blog": "",
  "location": "Dhaka, Bangladesh",
  "email": "minhaz.ratul@gmail.com",
  "hireable": false,
  "bio": null,
  "public_repos": 31,
  "public_gists": 7,
  "followers": 15,
  "following": 35,
  "created_at": "2011-12-01T20:29:31Z",
  "updated_at": "2015-06-24T18:56:46Z"
}
{% endhighlight %}

This is what I see when I visit the address with my username: [https://api.github.com/users/mnzr](https://api.github.com/users/mnzr). I just left out a few lines so that it's easier to read. If you look carefully you will notice it consists of valuable information regarding my Github account: when it was created, how many public repositories I have, even how many people I am following.
