# Before Starting

## Git and Python

For setting up and running Paperplane, python(>=3.6) is required to be present on your system. Here are some of the options you have:

- A Linux-based distro, as most of them come with Python preinstalled or have it one command away.
- A Windows or macOS machine, where Python can be installed with little to no effort.
- A Windows 10 machine with WSL or WSL2 (this is essentially the same as a Linux distro).
- An Android phone with TermUX (it's an app which can be downloaded from Play Store) and Python installed.
    * To install it on TermUX, execute the commands below:
    ```sh
        apt-get update -y; apt-get upgrade -y
        apt-get install python
    ```

(for The Manual Way only):
Git needs to be installed too, it's installed by default on most of the Linux distributions. It can be manually installed on Windows or macOS machines. To install it on TermUX, execute the commands below.

```sh
    apt-get update -y; apt-get upgrade -y
    apt-get install git
```

## Docker

(for The Manual Way only):

Even though Paperplane can work without Docker, it's highly recommended that Paperplane is run on Docker to provide a secure and working environment, specially created for Paperplane. Refer to https://docs.docker.com/get-docker/ for instructions on how to install Docker on your distro.

## API Key and Hash

To be able to connect to Telegram, you need to get your own API ID and API Hash from my.telegram.org and use them while setting up Paperplane. To get those 2 values, follow the steps below:

1. Head to my.telegram.org on your preferred web browser.
2. Input your phone number and press the 'Next' button
3. A confirmation code will be sent to your Telegram account. Paste that into the 'Confirmation code' field and press the Sign In button.
4. Click on 'API development tools' link.
5. If you see 'App configuration' instead of 'Create new application' page, skip to step 7.
6. On the 'Create new application' page, fill up 'app title' and 'short name' (other options can be filled, but are optional)
7. On the 'App configuration' page, find 'App api_id' and 'App api_hash'. Keep these values in a safe place as they will be used later during the setup.

!> The App api_id and api_hash values shouldn't be shared with anyone else and must be kept in secrecy. Make sure not to leak them!

## Database

Paperplane requires a working MongoDB database to start and function properly. To create one, you can use the free MongoDB Atlas service. To create a new database, follow the steps below:

1. Head to cloud.mongodb.com, sign up or log in.
2. On the 'Clusers' page, click on 'Create a New Cluster'.
3. Leave all the options as default and click 'Create Cluster'.
4. In the left sidebar, click on Network Access>Add IP Whitelist.
5. - If you know the IP address of the machine which will run Paperplane, it's preferred that you write it here.
- If you don't know the IP address(e.g. in Heroku), write '0.0.0.0/0'(without the quotes) in the 'Whitelist Entry' text box and press Confirm.
6. Next, in the left sidebar, click on Database Access>Add New Database User.
7. Make a username and password, and make sure to remember them and/or keep in a secure place.
8. On the Database User Privileges, leave the default option (Read and write to any database).
9. Click 'Add User'.
10. In the left sidebar, click on Clusters. Here you'll find the cluster created on steps 2-3 (should be named 'Cluster0' if the name wasn't changed). Press on the 'Connect' button below.
11. From here, choose 'Connect your application'.
12. Choose 'Python' as the 'Driver' and '3.6 or later' as the 'Version'.
13. Press the 'Copy' button next to the string below.
14. Replace <password> with the password of the user created on steps 6-9.
15. Delete the '/<dbname>?retryWrites=true&w=majority' part.
16. Save this edited string somewhere, it will be used during the setup.
