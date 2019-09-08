# Initial bringups for Paperplane with Docker Compose

# Cloning Repo

    https://github.com/RaphielGang/Paperplane-Dockerstation.git

!> Don't change the cloned folder name `Paperplane-Dockerstation` unless you know what are you doing

Get your api-id (called `API_KEY` in this bot) and `API_HASH` from my.telegram.org.

Install Docker from your appropriate package manager

### Bot Activities Logging (Optional)

Create an empty group, add Marie, or any forks, get the group id, copy it and set it as your `BOTLOG_CHATID`.

!> This variable ignored if `BOTLOG` is set to `False`

# Configuration

There are two possible ways of configuring your bot: a config.env file, or ENV variables.

The prefered version is to use a `config.env` file, as it makes it easier to see all your settings grouped together.
This file should be placed in the topmost part of the repo.

An example `config.env` is available on Dockerstation repo.

!> If you can't have a config.env file, or you missed to type something on `config.env` but then pushed it up, it is also possible to use environment variables.

### Getting Session

```sh
pip3 install python-dotenv telethon
python3 generate_session_file.py
```

### Getting Google Drive Session (Optional)

```sh
pip3 install PyDrive
python3 generate_drive_session.py
```

### Database

For the database part, it's already configured, by default, persistence isn't enabled by default, to enable it, edit
`docker-compose.yml` to :

```yml
    mongoserver:
        ...
        volumes:
            - /path/to/mongodb-persistence:/bitnami
        ...
```

Or if you want to leave docker-compose to make a Volume for you, edit `docker-compose.yml` to :

```yml
    mongoserver:
        ...
        volumes:
            - /bitnami
        ...
```

# Starting the bot

Once you've setup your database and your configuration (see below) is complete, simply run:

```sh
docker-compose up -d
```

### Debugging the bot

If you can't start the bot, run

```sh
docker-compose up
```

This will show the console logs of the Docker


# FOR DEVELOPERS

If you decided to going bleeding edge or want to help us debugging issues on Pre-production,
edit `Dockerfile` to :

```Dockerfile
RUN git clone ... -b staging /app
```