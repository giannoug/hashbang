+++
author = "giannoug"
date = 2016-08-07T14:16:00Z
description = ""
draft = false
image = "/images/2016/08/turn-your-pocket-chip-into-a-pokemon-go-bot-1.jpg"
slug = "turn-your-pocket-chip-into-a-pokemon-go-bot"
title = "Your Pocket C.H.I.P. plays Pokémon GO better than you"

+++


>Using bots can ruin the game for others (and you). Don't fight gyms and don't brag about the 2500 CP Dragonite you didn't catch yourself!

My Pocket C.H.I.P. arrived about 10 days ago and still I hadn't figured out anything cool and useful to build with it. During a visit on Reddit, I came across /r/pokemongodev/ and some threads about a Pokémon GO bot. I did some research and decided to try it out on a secondary account. The bot is written in Python so I decided to put the Pocket C.H.I.P. to the test.

Installation doesn't differ a lot from the official instructions. There are only a couple of extra packages needed. You can either use the Pocket C.H.I.P.'s keyboard to execute the commands or use SSH. I recommend the latter (don't forget to `sudo apt-get install ssh` first though, because it's not installed by default and also change the default password!). Before we begin installing the Pokémon GO bot, we are going to need some extra packages. The firmware I'm using for Pocket C.H.I.P. is the stock/official one that the device shipped with.

    $ sudo apt-get update
    $ sudo apt-get install git virtualenv build-essential python-dev

After everything is done, we can continue installing the bot. Commands are taken verbatim from the bot's wiki.

    $ cd ~/
    $ git clone --recursive -b master https://github.com/PokemonGoF/PokemonGo-Bot  
    $ cd PokemonGo-Bot
    $ virtualenv .
    $ source bin/activate  
    $ pip install -r requirements.txt

It will take some time, be patient. It compiles a lot of stuff (for some reason). One last step is to obtain the precious `encrypt.so` library. The file is needed for encrypting and decrypting(?) packets to and from(?) the Pokémon GO servers. I was unable to find a compiled version (GitHub project mods also deleted the file every time someone uploaded) and everyone seems to be begging for it in the comments. We will compile the file ourselves, forget the pre-compiled binaries.

    $ cd ~/
    $ wget http://pgoapi.com/pgoencrypt.tar.gz
    $ tar -xvzf pgoencrypt.tar.gz
    $ cd pgoencrypt/src/
    $ make
    $ cp libencrypt.so ../../PokemonGo-Bot/encrypt.so

Last but not least, the configuration file! Just copy the example and modify it to add your credentials. The `config.json` contains your bot's characteristics and its general behaviour.

    $ cd ~/PokemonGo-Bot/
    $ cp configs/config.json configs/config.json.example
    $ nano config/config.json

Every time you want to start the bot, you need to activate the Python environment and execute the run script.

    $ source bin/activate
    $ ./run.sh

![Pokemon GO bot in action](/images/2016/08/turn-your-pocket-chip-into-a-pokemon-go-bot-a.jpg)

Congratulations, your bot is now running and visiting PokeStops (amongst other things)! Let's move on to the web interface so we can observe what it does. Again, we need to configure the app with our credentials.

    $ cd ~/PokemonGo-Bot/web/config/
    $ cp userdata.js.example userdata.js
    $ nano userdata.js
    $ cd ../
    $ python -m SimpleHTTPServer

You can use whatever browser you like to see the map on the Pocket C.H.I.P.'s display. Just type `surf localhost:8000` on the console to see it working.

You are ready to roll!

