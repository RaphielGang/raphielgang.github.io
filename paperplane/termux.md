•Lets setup the Bot•

Open Termux and paste the fllowing commands one by one

     1) apt-get update; apt-get upgrade

     2) apt-get install zlib zlib-dev curl wget libwebp libwebp-dev libjpeg*     

 (yes "*" is there)    

     3) pkg install clang curl python python-dev postgresql-dev libcrypt-dev libffi-dev openssl-dev libxml2-dev libxslt-dev libjpeg-turbo-dev ndk-sysroot make   

     4) pkg install curl git clang python

    5) pkg install clang python sqlite python-dev libcrypt-dev libffi-dev openssl-dev libxml2-dev libxslt-dev

    6) pip install --upgrade pip

    7) pkg install postgresql

     8) pip3 install --upgrade telethon

    9) pkg install clang python sqlite python-dev libcrypt-dev libffi-dev openssl-dev libxml2-dev libxslt-dev

    10) pkg install libjpeg-turbo-dev

    11) pkg install postgresql-dev python-dev make clang

    12) pip install psycopg2-binary

     13) pip install async_generator

     14) pkg upgate

    15) git clone --bare https://github.com/RaphielGang/Telegram-UserBot.git

    16) cd Telegram-UserBot.git 

         Now copy your repo link

          It should be like this         

   https://github.com/"your_username"/"your_repo_name".git

 

     17) git push --mirror "your repo link" 

    18) cd

    19) git clone "your repo link" 

     20) cd "your repo name"

    21) pip3 install -r requirements.txt

      Now wait it will download some packages. Don't close termux

    22) export API_HASH=your-api-hash

    export API_KEY=your-api-id

and now do 

    python3 -m userbot

Now it will ask for your mobile number give it with your country code like this +911234567891

Then type OTP and done.

Now you have successfully created your own userbot test it by typing .alive in any chat
 •How to Deploy to Heroku•

 After successfull login it will generete a session.

 Open a new session in Termux and type the following

    cd 

    ls

    cd "your repo name" && ls

make sure "userbot.session" is there

 Then type this

    curl --upload-file ./userbot.session https://transfer.sh/userbot.session

This will give you a link copy and paste it in chrome and download userbot.session

The link looks like this

    https://transfer.sh/xxxx/userbot.session

23) Now open your GitHub repo upload that userbot.session file in it and make sure that YOUR REPO IS PRIVATE!!

24) Go to  Heroku create a new app. Use desktop mode.

25) Go to Deploy click on GitHub and connect Github to Heroku

26) Now go to Termux and type the following

    27) pkg install nodejs (Alternative pkg install yarn)

    28) npm i -g heroku (Alternative yarn add global heroku-cli@latets)

     29) heroku login

 it will open your browser, simply click on login.

30)Go back to termux and type the following

    31) heroku stack:set container -a "your heroku app name"

    32) heroku addons:create heroku-postgresql:hobby-dev -a "your heroku app name"

33)Go to Heroku, Deploy tab, make sure Github is connected and proper repo is selected

34)Enable Automatic Deploys, select Master Branch and then click on Deploy Branch

35)Keep the tab open and look out for the build log, if it fails you fucked up something.

36)If the build succeeds then GG!

37)Now go to Resources Tab and refresh

 Clik on the Pencil Icon and Enable the Worker and save it

38) Your bot should be alive now

39) Check it by typing ".alive" in any chat

40) if its not alive, Open Termux, type

     heroku login

     heroku logs --tail -a "your heroku app name"

41) If it says "Your API_KEY and API_HASH Cannot be empty"

42) Go to Heroku, Your app, Then Go to Settings

43) Click on "Reveal Config Vars" 

 Click on the Left Empty box and type

 "API_KEY" and put the corresponding value in the right side box

 Same for API_HASH

 Click on the Left box, type "API_HASH"  and Put the value

 44) Refresh the page

45) Check logs again from Termux

 If the logs show no errors, your bot is alive

Yay! You did it! Your bot is now alive and running.
You can add more vars to get more features! 

Although your userbot is running, its features are limited, you can't add notes, filters etc. In order to get these features you need to add a database. Follow the steps given below to create a new DB


•    Go to https://www.mongodb.com/

•    Sign up and follow the tutorial to setup a new cluster

    In the left sidebar, go to Network Access, click on Add IP Adress and set it to 0.0.0.0/0
    Next go to Database Access, click on Add New User, put Username and Password, then select Atlas Admin and Click on Add User
    Now, go to Cluster, click on Connect, then click on Connect Your Application.
    By default node.js is selected, click on it and select Python, and in the version, select 3.6 or later.
    Below that, copy the DB URI
    It should be like this

    mongodb+srv://<username/admin>:<password>@userbot-yidbn.mongodb.net/

(Remove everything after the /)

•    Now go to Heroku Config Vars, Add a new key as MONGO_DB_URI and put the URI you just copied

    Replace username/admin:password with the admin and password you just made. Also remove the angled brackets while typing the password <>
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
