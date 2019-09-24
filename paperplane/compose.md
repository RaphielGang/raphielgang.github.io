# Initial bringups for Paperplane with Docker Compose

# Cloning Repo

    git clone https://github.com/RaphielGang/Paperplane-Dockerstation.git

!> Don't change the cloned folder name `Paperplane-Dockerstation` unless you know what are you doing

Get your api-id (called `API_KEY` in this bot) and `API_HASH` from my.telegram.org.

### Installing Docker (Compose)

Fedora :

```sh
dnf install docker docker-compose
```

Fedora (Silverblue) :

```sh
rpm-ostree install docker docker-compose
```

Debian :

```sh
apt install docker
```

!> For distros that doesn't ship docker-compose in the Package Repository (e.g : Debian), refer to https://docs.docker.com/compose/install/

!> Refer to your distro if yours isn't specifid here

### Bot Activities Logging (Optional)

Create an empty group, add Marie, or any forks, get the group id, copy it and set it as your `BOTLOG_CHATID`.

!> This variable ignored if `BOTLOG` is set to `False`

# Configuration

There are two possible ways of configuring your bot: a config.env file, or ENV variables.

The prefered version is to use a `config.env` file, as it makes it easier to see all your settings grouped together.
This file should be placed in the topmost part of the repo.

An example `config.env` is available on Dockerstation repo.

!> If you can't have a config.env file, or you missed to type something on `config.env` but then pushed it up, it is also possible to use environment variables.

!> If the config is there but python-dotenv can't read it. The encoding is wrong

### Getting Session

```sh
pip3 install python-dotenv telethon
python3 generate_session_file.py
```

### Getting Google Drive Session (Optional)

1. Go to APIs Console and make your own project.
2. Search for ‘Google Drive API’, select the entry, and click ‘Enable’.
3. Select ‘Credentials’ from the left menu, click ‘Create Credentials’, select ‘OAuth client ID’.
4. Now, the product name and consent screen need to be set -> click ‘Configure consent screen’ and follow the instructions. Once finished:

    - Select ‘Application type’ to be Web application.
    - Enter an appropriate name.
    - Input http://localhost:8080 for ‘Authorized JavaScript origins’.
    - Input http://localhost:8080/ for ‘Authorized redirect URIs’.
    - Click ‘Save’.

5. Click ‘Download JSON’ on the right side of Client ID to download client_secret_<really long ID>.json.

The downloaded file has all authentication information of your application.

!> Rename the file to “client_secrets.json” and place it in your working directory.

And then run the following command and follow the login instruction

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

# Updating the bot

In-case you want to update your deployed image, simply run

```sh
docker-compose build --pull --no-cache
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