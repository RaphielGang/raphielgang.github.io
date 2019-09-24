# Initial bringups for Paperplane with TermUX

!> This Documentation isn't complete yet

!> Get your api-id (called `API_KEY` in this bot) and `API_HASH` from my.telegram.org.

### Installing requirements on TermUX

```TermUX
    apt-get update -y; apt-get upgrade -y
    pkg install git python
```

### Updating pip and upgrading Telethon and Async module

```TermUX
    pip install --upgrade pip
    pip3 install --upgrade telethon async_generator
```

### Cloning Repo

```TermUX
    git clone https://github.com/RaphielGang/Paperplane-Dockerstation.git
```

!> Don't change the cloned folder name `Paperplane-Dockerstation` unless you know what are you doing

!> Wait while it downloading some packages. Don't close TermUX.

After it finishes, get your API_KEY and API_HASH. Then, type these 2 lines, replacing your-api-hash and your-api-key with your API_HASH and API_KEY respectively(no quotes are needed).

```sh
    export API_HASH=your-api-hash
    export API_KEY=your-api-id
```

!> TO BE CONTINUED