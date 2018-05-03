# CS 506 Crypto Counter - CRON #

This is a python program designed to gather economic and social data from various APIs for the Crypto Counter project found [here](https://github.com/trlee2/CryptoCounter/tree/master).

### What is this repository for? ###

I created this for CS 506 Software Engineering at UW - Madison as a way to help my team on the group project. We were a team of 6 guys which broke up into teams of 2. I was on the backend API team whose job it was to collect data and add it to the database. My partner, Kedi Cui, helped me do the research while I created and wrote the code.
The live site can be found [here](https://cccounter.herokuapp.com/).

### How do I get set up? ###

* This code will not work as a stand alone codebase and will need the addition of either the rest of the [CryptoCounter code](https://github.com/trlee2/CryptoCounter/tree/master) or changing the code to add your own databse.
* Python version 3.6.x
* [PostgreSQL](https://www.postgresql.org/download/)
	* You may encounter some initial problems with setting up the database for the first time, this may be because the default user can not be found. 
	* Also, look at the [CryptoCounter code](https://github.com/trlee2/CryptoCounter/tree/master) to see how to set up the database.
* Install the following libraries using <b>pip install</b>:
	* ```shell
		$ pip install requests
		$ pip install apscheduler
		$ pip install TwitterAPI
		$ pip install pytrends
		$ pip install praw
		$ pip install tweepy
* Add the following info to both cron.py and tweet.py
	* ``` shell
		Twitter API info -> tweet.py[10:13]
		database settings -> cron.py[5,60:67]
		newsapi keys - > cron.py[40], This is a string array of keys, add as many as you want.
		Reddit API -> cron.py[254:258]
		Facebook API access_token - > cron.py[312]		
* Run cron my using:
	* ```shell
		$ python cron.py
* Cron can also take arguments when ran
	* ```shell
		$ python cron.py -h
		----------------------------------------------------------------------------
		long argument   short argument  definition
		----------------------------------------------------------------------------
		--help             -h             Show this help message and exit
		--cron             -c             Enable cron mode
		--reset            -r             Truncate all tables that cron interacts with
		--test             -t             Start xUnit tests
		--history [days]   -p             Sets the number of days to go back in history
		                                    Default: 184 days (6 months)
		--debug            -d             Debug mode of testing as we code                                    
		-----------------------------------------------------------------------------
* When running cron for the first time, it may take over an hour or more to load in data. If it looks like the program is hanging, do not worry, this is just cron handling data. Twitter is also disabled for overall social and ICO social data on the backend, due to the time it takes to record the info. Instead it is recorded as a -1.

* The default for cron is 184 days of historical prices. To speed up cron, set historical days to a smaller number like 3 for an example.
	* ```shell
		$ python cron.py -p 3
### Notes: ###
* Like mentioned before, Twitter has been disabled for general and ICOs due to time it took to count the tweets.
* Facebook API stopped working due to a change on their end
* Remember to update the code before using it.
* You will need to add the tables in yourself if you are not using the [CryptoCounter code](https://github.com/trlee2/CryptoCounter/tree/master)
* I have 13 tests but should have more, I ran out of time during the class to implement them.

### Contribution guidelines ###

* If you would like to make edits, please create a pull request or make an new issue.

### Who do I talk to? ###

* Andrew Tomko
* tomand285@gmail.com
