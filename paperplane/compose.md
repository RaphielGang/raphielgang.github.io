# Initial bringups for Paperplane with Docker Compose

# Cloning Repo

    git clone https://github.com/RaphielGang/Paperplane-Dockerstation.git

!> Don't change the cloned folder name `Paperplane-Dockerstation` unless you know what you are doing.

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

?> For distros which don't ship docker-compose in the Package Repository (e.g : Debian), refer to https://docs.docker.com/compose/install/

?> Refer to your distro if yours isn't specified here.

### Configuration

Read about configuration settings [here](/paperplane/initial?id=configuration).

### Generating a Session file

Read about generating a session file [here](/paperplane/initial?id=generating-a-session-file).

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
