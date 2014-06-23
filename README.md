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

This morning, I mysteriously have a permission problem in the vagrant file.  Probably it is my fault somehow, but to get vagrant to work, I actually have to:

1) Do vagrant up.
2) SSH to the vagrant machine with "vagrant ssh".
3) Run SOLR as root: sudo java -jar /home/vagrant/PriceHistory/solr-4.7.2/example/start.jar >& solroutput.log &
4) Start the MorrisDataDecorator by hand after this by going into the 
MorrisDataDecorator directry and executing "bash run_all.bash".

I will explain all this in person to anyone at the Hackathon.  Sorry for the inconvenience.

Houston Hackathon
-------------

On June 1st (the National Day of Civic Hacking), I drove to Houston and participated in [Houston Open Innovation Hackathon](http://houstonhackathon.challengepost.com/submissions).

I had the pleasure of forming a team with Drew and David.  I created a not-yet-ready-for-prime-time data ingest API and GUI, and Drew and David created [Mr. CSV Transfomer](https://github.com/DeepInTheCode/mr-csv-transformer), a fork of "Mr. Data Transformer".  That project, taken togehter with my Ingest code, is a crude step toward being able to load data into PriceHistory without having to be a programmer at all.

The Hackathon also encouraged the City of Houston to further evaluate this code.



Demo Instance is currently available only to Houston Employees
-------------

Due to limited resources, and the fact that Houston is currently evaluating this, I have dedicated my server specifically to Houston for the extent of their evaluation.

[Try out PriceHistory --- except not now!](http://54.186.102.33/gui/)! 



