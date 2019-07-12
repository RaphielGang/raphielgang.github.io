# Initial bringups for Paperplane

### Before you start

Clone this repo `git clone https://github.com/RaphielGang/Telegram-UserBot`

Get your api-id (called `API_KEY` in this bot) and API_HASH from my.telegram.org.

Install Docker from your appropriate package manager

Optional: Create an empty group, add Marie, or any forks, get the group id, copy it and set it as your `LOGGER` (in case you want logging).

Since its fully dockerized, the setup is just building the docker image
```
cd Telegram-UserBot
docker build . -t userbot
```

### Database

Spin up a mongodb cluster from cloud.mongodb.com, and then follow these steps:

- In the left sidebar, find network access, you can grant access to IP-specific or more easier put it to 0.0.0.0/0
  (Heroku guys, you need to use 0.0.0.0/0)
- Next go to database access, create a new user, and password, with the level of atlas admin
- Now grab your python connector srv link from the connect button on your cluster
- Make sure to choose the latest version driver
- Replace admin:<password> with the newly created user
- Now add this to your config.env

### Configuration

There are two possible ways of configuring your bot: a config.env file, or ENV variables.

The prefered version is to use a `config.env` file, as it makes it easier to see all your settings grouped together.
This file should be placed in the topmost part of the repo.
This is where your `API KEYS` will be loaded from, as well as your `database URI` (if you're using a database), and most of
your other settings.

An example `config.env` file could be:
```
    API_KEY=123456
    BUILD_CHOICE="bleeding"
    API_HASH='4588acb1863ead924119c885dfffba2'
    BOTLOG_CHATID=-1001200493567
    BOTLOG=True    #Incase you want to turn off logging, put this to false
    PM_AUTO_BAN=True
    CONSOLE_LOGGER_VERBOSE=True
    SCREEN_SHOT_LAYER_ACCESS_KEY="get from screenshot layer website google it "
    OPEN_WEATHER_MAP_APPID="get it from openweather site"
    MONGO_DB_URI=
```

If you can't have a config.env file, or you missed to type something on `config.env` but then pushed it up, it is also possible to use environment variables.


## Starting the bot

Once you've setup your database and your configuration (see below) is complete, simply run:

`docker run userbot`
