PriceHistoryInstall via Vagrant
===============================

This is the installation materials for the PriceHistory project, which consists of several repos.

Note: You must download and file the file solr-4.7.2.zip and put it in this directory.  This file is 
too big to be worth duplicating into github.  That is the only thing you need beyond this repo to build a vagrant-implemented PriceHistory.

This project exists to make it eaiser to install and set up a PriceHistory website.  It contains 
a Vagrant file.

You should in theory be able to pull this repo onto a local machine and perform:
> vagrant up

The initial execution of this may take an hour or more depending on your internet connection as it builds virtual machine.

This will create a Vagrant instance of an Ubuntu box running a complete PriceHistory application that should be reachable by browsing to: 
http://localhost:4567 on your own machine.

To log into the site, use:
> houstonUser99
> RpG0pRDyIrhbcBK82a3hqjvir

The current instance was planned for the upcoming [City of Houson Open Innovation Hackathon](http://www.houstonhackathon.com), so it is uses Houston-specific usernames right now.  However, all of the data at the site is completely public.  There is currently no Houston data on the site.

To begin coding, perform "vagrant ssh" and you will be logged into YOUR personal vagrant Ubuntu virtual machine.  If you cd to "PriceHistory", you should be able to begin poking around the code, possibly making a git branch and pull request!

Please contact <read.robert@gmail.com> for more information.

Houston Hackathon
-----------------

For the Houston Hackahton, I have entered 18 issues into this github repo, of diverse difficulties and types.  However, my main goal is to do what I call Project White Fountain.  The purpose of this is to make PriceHistory the opposite of a "black hole" --- a white fountain --- that makes public price history ifnormation freely available.

In order to do this, I believe we need to build an "ingest" API that allows anyone, but a municipality in particular, to freely publish to us price history.  We will also need to keep the registered data recorded in some way so that we can remove or disable the dataset.

In addition to programming in Python, this project also requires a certain amount of documentation, marketing, and other non-programming tasks.  The goal is not just to code, but to build a useful product---and that always requires a diversity of talent.


Demo Instance
-------------

Although this repo exists to make it easy for you to install PriceHistory yourself, you can use the demo
instance set up for Houston Hackathon:

[Try out PriceHistory](http://54.186.102.33/gui/)! 

However, understand that this instance has some limitations.  At present it contains only a small amount of data taken from USASpending.org, which
does NOT contain unit quantity information.  One of the main purposes of PriceHistory is to compare per-unit price and also to compare multiple 
sources/vendors, so this demonstration is weak compared to an instance loaded with proper data.

To log into this instance, please use the credentials:

> houstonUser99
> RpG0pRDyIrhbcBK82a3hqjvir

(This instance has been created primarily to support the upcoming Houston Hackathon (see below)). Feel free to create your own test portfolios.