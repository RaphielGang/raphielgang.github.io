Setup Paperplane using TermUX, Step-by-Step
===========================================

### Before you start

Get your api-id (called API_KEY in this bot) and API_HASH from my.telegram.org.

### In case you want Logging support (optional)
Create an empty group, add Rose, or any bot, get the group id, copy and keep it (will be used in the next steps).

### TermUX setup, generating a session

Open Termux and paste the following commands one by one, pressing Enter after each line:
```TermUX
    apt-get update -y; apt-get upgrade -y
    apt-get install zlib zlib-dev curl wget libwebp libwebp-dev libjpeg* -y
```

!> Yes, "*" is there.

### Installing Packages
```TermUX
    pkg install git clang python libcrypt libffi openssl libxml2 \
    libxslt ndk-sysroot make sqlite -y
```

### Updating pip and upgrading Telethon and Async module
```TermUX
    pip install --upgrade pip
    pip3 install --upgrade telethon async_generator
```

### Upgrading TermUX Packages and cloning Paperplane
```TermUX
    pkg upgrade -y
    git clone https://github.com/RaphielGang/Telegram-UserBot.git userbot
```

### Bringups Paperplane and installing Requirements
```TermUX
    cd userbot
    pip3 install -r requirements.txt
```

!> Wait while it downloading some packages. Don't close TermUX.

After it finishes, get your API_KEY and API_HASH. Then, type these 2 lines, replacing your-api-hash and your-api-key with your API_HASH and API_KEY respectively(no quotes are needed).

```sh
    export API_HASH=your-api-hash
    export API_KEY=your-api-id
```

And now type:
```TermUX
    python3 -m userbot
```

Now it will ask for your mobile number, write it with your country code like this:+911234567891.
Then, type the Login code you received.
Enjoy!

Now you have successfully set up Paperplane. Test it by typing .alive in any chat.

# How to Deploy to Heroku

After successfull login it will generate a session.
Open a new session in Termux and type the following

```sh
    cd
    ls
    cd "your repo name" && ls
```

!> Make sure "userbot.session" is there

### Uploading session file
```sh
    curl --upload-file ./userbot.session https://transfer.sh/userbot.session
```

This will give you a link, copy and paste it in chrome and download userbot.session
```sh
    https://transfer.sh/xxxx/userbot.session
```

Now open your GitHub repo upload that userbot.session file in it.

!> Make sure that YOUR REPO IS PRIVATE!!

### Heroku bringup

Go to Heroku create a new app. Use desktop mode.
Go to Deploy click on GitHub and connect Github to Heroku.

#### Install nodejs and npm
```TermUX
    pkg install nodejs (Alternative pkg install yarn)
    npm i -g heroku (Alternative yarn add global heroku-cli@latets)
    heroku login
```

It will open your browser, simply click on login.

#### Setting up heroku container
```TermUX
    heroku stack:set container -a "your heroku app name"
    heroku addons:create heroku-postgresql:hobby-dev -a "your heroku app name"
```

- Go to Heroku, Deploy tab, make sure Github is connected and proper repo is selected
Enable Automatic Deploys, select Master Branch and then click on Deploy Branch
Keep the tab open and look out for the build log, if it fails you fucked up something.

- If the build succeeds then GG! Now go to Resources Tab and refresh
Clik on the Pencil Icon and Enable the Worker and save it

- Your bot should be alive now
Check it by typing `.alive` in any chat

If its not alive, Open TermUX, type
```TermUX
     heroku login
     heroku logs --tail -a "your heroku app name"
```

If it says
```Heroku
    Your API_KEY and API_HASH Cannot be empty
```

Go to Heroku, Your app, Then Go to Settings
Click on "Reveal Config Vars"

Click on the Left Empty box and type
`API_KEY` and put the corresponding value in the right side box
Same for `API_HASH`
Click on the Left box, type `API_HASH`  and put the value

 Refresh the page.

Check logs again from Termux
If the logs show no errors, your bot is alive

Yay! You did it! Your bot is now alive and running.
You can add more vars to get more features!

Although your userbot is running, its features are limited, you can't add notes, filters etc. In order to get these features you need to add a database.

## Mongo bringups

- Go to https://www.mongodb.com/
- Sign up and follow the tutorial to setup a new cluster

- In the left sidebar, go to Network Access, click on Add IP Address and set it to 0.0.0.0/0
- Next go to Database Access, click on Add New User, put Username and Password.
- Select Atlas Admin and Click on Add User
- Go to Cluster, click on Connect, then click on Connect Your Application.
- By default node.js is selected, click on it and select Python, and in the version, select 3.6 or later.
- Below that, copy the DB URI. It should be like this :


    mongodb+srv://<username/admin>:<password>@userbot-yidbn.mongodb.net/

!> Remove everything after the /

- Now go to Heroku Config Vars, Add a new key as MONGO_DB_URI and put the URI you just copied

- Replace `username/admin:password` with the admin and password you just made. Also remove the angled brackets while typing the password <>

That's it!
Your bot will be re-start and will be alive within a couple of seconds.
If it still says Database Error check Heroku Logs

To check Heroku Logs, do the following

Open Termux and type

    heroku login

And follow the in screen instructions
Then go back to Termux and type

    heroku logs --tail-a yourappname

You will now see logs
