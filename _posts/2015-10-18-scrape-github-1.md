---
layout: post
title: "Scraping Github - The Setup (Part 1)"
date: {}
author: Ratul Minhaz
summary: Learn to scrape data from API using Python
categories: learning
tags: 
  - scraping
  - python
  - API
published: true
---


Data science is a buzzword these days and everyone is asking how to be a data scientist. A data scientist's job is definitely awesome, because if anyone is close to predicting the future, they are the ones who probably do it. But what does a data scientist actually do? The process of "data science" roughly consists of three things: mining, analysis and visualization. Each one of these three segments is interesting in it's own right. In data mining you get to collect data from large data sources, mostly from the Internet using clever techniques like scraping.

Many websites provide `API` so that other people can collect data from those sites to use in their work. For example you might want to know a Facebook page's growth over a certain period of time. Facebook made an API just so that you can get the data to do the analysis needed to answer your question. This sort of API is provided by Github and Twitter too. You can not imagine how vastly useful this public data is, they even came in handy as much as [detecting earthquakes](https://blog.twitter.com/2015/usgs-twitter-data-earthquake-detection) faster than the U.S. Geological Survey!

![]({{site.baseurl}}/assets/images/earthquake_technology.png)

Enough talk, let's have some action! In this tutorial, I will get you started with scraping data from API using Python. We will use Github's API as data source and keep the scr![earthquake_technology.png]({{site.baseurl}}/assets/images/earthquake_technology.png)
aped data in a database called RethinkDB. Don't worry if you have never heard of it before, it's pretty cool. If you want to try out other databases, you will just have to tweak a few lines of code. Let's set up the necessary softwares.

# Setup
You will need these softwares, preferably in a Linux workstation. I am going to use Ubuntu.

- Python 3
- RethinkDB 2.0.x
- Sublime Text 3 or any good text editor for coding

__Python 3__
Depending on your Linux distro, you might have Python 3 already installed. Check it using this command in your terminal:

{% highlight bash %}
python3 --version
{% endhighlight %}

If you don't have Python 3, then installing it is breeze:

{% highlight bash %}
sudo apt install python3
{% endhighlight %}

__RethingDB__
If you are new to Ubuntu or Linux, installing RethinkDB might be a little bit complicated for you. Nothing you can't do though, just a few lines of extra codes to copy and paste.

{% highlight bash %}
source /etc/lsb-release
echo "deb http://download.rethinkdb.com/apt $DISTRIB_CODENAME main" | sudo tee /etc/apt/sources.list.d/rethinkdb.list
wget -qO- http://download.rethinkdb.com/apt/pubkey.gpg | sudo apt-key add -
sudo apt-get update
sudo apt-get install rethinkdb
{% endhighlight %}

You will also need the client drivers so that you can connect to RethinkDB through your Python code.

{% highlight bash %}
sudo pip install rethinkdb
{% endhighlight %}

Then fire up a Python shell and try out these commands to see if RethinkDB works or not. (Code taken from RethinkDB's official [documentation](https://www.rethinkdb.com/docs/), it's good so read it too!)

{% highlight python %}
import rethinkdb as r
r.connect('localhost', 28015).repl()
r.db('test').table_create('tv_shows').run()
r.table('tv_shows').insert({ 'name': 'Star Trek TNG' }).run()
{% endhighlight %}
