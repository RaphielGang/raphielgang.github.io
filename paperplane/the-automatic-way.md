# Deploying Paperplane the Automatic Way (Heroku)

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/RaphielGang/Telegram-Paperplane)

To Deploy to Heroku automatically using the button above, follow the guide below. Before starting, you'll need API Key and Hash, a MongoDB URI and a String Session. Read the [API Key and Hash](/paperplane/before-starting?id=api-key-and-hash) and [Database](/paperplane/before-starting?id=database) guides to get API Key, Hash and the MongoDB URI. You can find more about getting String Session below.

## Getting a String Session

To get a String Session, you need to have a working Python environment. You can find how to install Python on the [Git and Python](/paperplane/before-starting?id=git-and-python) page.

After having Python installed, you can either use Git to clone the Paperplane repo, or alternatively, download the script manually. To download it, you have 2 options:

- (Recommended for Windows) Open https://raw.githubusercontent.com/RaphielGang/Telegram-Paperplane/master/scripts/generate_string_session.py in your web browser and then **right click>Save as...** Save the file on your Desktop.
- (Recommended for Linux (including WSL), macOS, TermUX) Use one of those commands:
    ```sh
    wget https://raw.githubusercontent.com/RaphielGang/Telegram-Paperplane/master/scripts/generate_string_session.py
    ```

    Or, if you don't have wget installed (e.g. on macOS or some Linux distros):
    ```sh
    curl -O https://raw.githubusercontent.com/RaphielGang/Telegram-Paperplane/master/scripts/generate_string_session.py
    ```

After downloading the script, you need to run it. To run the script, you need to have Telethon installed. Use the commands below on your Terminal (or Command Prompt on Windows):

```sh
pip install telethon
python generate_string_session.py
```

?> Depending on your environment, you may need to use pip3 and python3 instead of pip and python respectively.

After running the commands, you will be prompted to enter the API Key and Hash. After entering them, you will be prompted with your String Session.

!> This line of string is very powerful: if someone has it, then they can log in to your Telegram account, change settings or even delete your account! So, make sure not to give it to anyone and be very careful when you write it somewhere. Paperplane is not responsible if you leak it to someone.

## Deploying

After getting everything required, you can now press the Deploy to Heroku button in the top of this page (or in the GitHub repo). Register or log into Heroku, then on the next page, fill all the required fields. It's recommended to fill all fields if you want to use every feature of Paperplane. After you are done, press 'Deploy app'.





