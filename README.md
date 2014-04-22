PriceHistoryInstall via Vagrant
===============================

This is the installation materials for the PriceHistory project, which consists of several repos.

Note: You must download and file the file solr-4.7.2.zip and put it in this directory.  This file is 
too big to be worth duplicating into github.  That is the only thing you need beyond this repo to build a vagrant-implemented PriceHistory.

This project exists to make it eaiser to install and set up a PriceHistory website.  It contains 
a Vagrant file.

You should in theory be able to pull this repo onto a local machine and perform:
> vagrant up

This will create a Vagrant instance of an Ubuntu box running a complete PriceHistory application.

To log into the site, use:
> houstonUser99
> RpG0pRDyIrhbcBK82a3hqjvir

The current instance was planned for the upcoming [City of Houson Open Innovation Hackathon](http://www.houstonhackathon.com), so it is uses Houston-specific usernames right now.  However, all of the data at the site is completely public.  There is currently no Houston data on the site.





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