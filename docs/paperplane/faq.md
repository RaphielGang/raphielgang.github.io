# Databases connections are failing!

Try to check if: 

 1. Your config is incorrect
 2. Make sure in config.env, It must have MONGO_DB_URI. If you have DB_URI or MONGO_DB_URL please change it to MONGO_DB_URI
 3. You're entered invalid database url
 4. Make sure you followed all the steps mentioned under database setup

# How to make a new module?
Creating a module has been simplified as much as possible - but do not hesitate to suggest further simplification.

All that is needed is that your .py file be in the modules folder.

To add commands, make sure to import the the primary bot via

`from userbot.events import register`.

You can then add commands wrapping them under

```
@register(outgoing=True, pattern="")
async def some_function(e):
     Whatever here.
```


You can also set outgoing to incoming incase, you wanna make that command to parse the incoming message.

The command pattern will be case-insensitive regex. Hope you know it, else feel free to hop on [here](https://regexone.com)

Use asynchronous functions, and await the functions.

Should you need assistance with telethon library check out their [documentation](http://telethon.readthedocs.io/) or get support from [them](https://t.me/TelethonChat)
