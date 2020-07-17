# Deploying to Heroku Manually

After doing the initial configuration, you can deploy Paperplane to Heroku.

### Before you start

Make sure to create a new Heroku app at https://dashboard.heroku.com and remember the app name.

### Installing Heroku CLI

Ubuntu 16+:

```sh
sudo snap install --classic heroku
```

TermUX (or other Operating Systems with nodejs support):

```sh
npm install -g heroku
```

Standalone installer(required sudo):

```sh
curl https://cli-assets.heroku.com/install.sh | sh
```

?> Read more about installing Heroku CLI [here](https://devcenter.heroku.com/articles/heroku-cli#download-and-install).


### Configuring the app

First, login to Heroku CLI

```sh
heroku login
```

Make sure you are in the cloned repository's folder (Telegram-Paperplane).

Then, tell Heroku to use container stack (replace "app name" with your Heroku app's name in quotes in this and future commands):

```sh
heroku stack:set container -a "app name"
```

Add the Heroku remote to the git project:

```sh
heroku git:remote -a "app name"
git fetch heroku
```

Commit your userbot.session, client_secrets.json and secret.json(if they exist):

```sh
git add -f userbot.session
git add -f client_secrets.json
git add -f secret.json

git config --global user.name "Your name"
git config --global user.email "your_email@example.com"
git commit -m 'Commit userbot.session and secrets for deploying'
```

!> If you are using a config.env file instead of Config Vars in Heroku, stage your config.env file too by using `git add -f config.env` command.

### Pushing to Heroku:

After making a commit with your session and other configurations, follow the steps below to push everthing to Heroku:

```sh
git push heroku master -f
```

### Turning the Dyno on

After the deployment finishes, go to dashboard.heroku.com, choose your app, open the Overview tab, click Configure Dynos, and turn on the worker dyno by pressing the pencil button, turning the toggle on, and prssing Confirm. Then click the More button on the top right corner and click Restart all Dynos.

After turning the dyno on, wait a few seconds for Paperplane to start, then try `.alive` on any chat in Telegram to check if Paperplane is working.

!> If you get no response from the `.alive` command, make sure you set the API Key and Hash correctly.

?> If you need more help, check the [FAQ](/paperplane/faq?id=frequently-asked-questions) or the [Portals](/paperplane/portals) for more support.

