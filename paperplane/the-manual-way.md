# Setting Paperplane Up the Manual Way

### Cloning the repository

Use the following command to clone the Paperplane repo to your machine.

```sh
git clone https://github.com/RaphielGang/Telegram-Paperplane
```

!> Don't change the cloned folder name (`Telegram-Paperplane`) unless you know what you are doing.

### Generating a session file

To run Paperplane, you should generate a session file. You can do so by following the commands below.

```sh
cd Telegram-Paperplane
pip3 install --upgrade python-dotenv telethon
python3 scripts/generate_session_file.py
```

!> When prompted, write the API Key and API Hash. Get those by following the instructions [here](/paperplane/before-starting?id=API_Key_and_Hash)

!> Replace `your-api-hash` and `your-api-id` with your API Hash and API ID respectively.


### Configuration

There are two possible ways of configuring your bot: a config.env file, or ENV variables.

The prefered version is to use a `config.env` file, as it makes it easier to see all your settings grouped together.
This file should be placed in the topmost part of the repo.
This is where your `API KEYS` will be loaded from, your `database URI` (if you're using a database), as well as most of your other settings.

An example config file(`sample_config.env`) is available on the Paperplane repo.

!> If you can't have a config.env file, or you missed to type something on `config.env` but then pushed it up, it is also possible to use environment variables.


### Bot Activities Logging (Optional)

Create an empty group, add Marie, or any forks, get the group id, copy it and set it as your `BOTLOG_CHATID`.

!> This variable is ignored if `BOTLOG` is set to `False`

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
python3 scripts/generate_drive_session.py
```

## Running locally

From here, you can choose to either run Paperplane locally (or on a VPS), or deploy it to Heroku. Check out the [Deploying to Heroku Manually](paperplane/heroku.md) page for Heroku, otherwise follow the steps below to build and run the Docker image on a PC or VPS.

### Building the container

Once you've set up your database and your configuration (see above) is complete, build the Docker image:

```sh
docker build . -t userbot
```

### Starting the bot

After building the image, simply run:

```sh
docker run userbot
```

!> If you get no response from the `.alive` command, make sure you generated a session and set the API Key and Hash correctly.

?> If you need more help, check the [FAQ](/paperplane/faq?id=frequently-asked-questions) or the [Portals](/paperplane/portals) for more support.