+++
author = "giannoug"
date = 2016-04-12T21:12:02Z
description = ""
draft = false
image = "/images/2016/04/your-own-facebook-messenger-bot-powered-by-nodejs.jpg"
slug = "your-own-facebook-messenger-bot-powered-by-nodejs"
title = "Your own Facebook Messenger bot powered by NodeJS"

+++


A few hours ago Facebook released it's own bot API for the Messenger platform. Nothing fancy like the stuff Microsoft showcased at Build 2016, but it's something. Messenger is used by 900.000.000 people, too. The Messenger bot API is available, ready to be used and the accompanying documentation has been published. You can read the [official Facebook Messenger bot getting started guide](https://developers.facebook.com/docs/messenger-platform/quickstart) to help you bootstrap the appropriate Facebook application, pages and permissions.

I believe the guide is a bit unclear code-wise, or should be more generic. The do show code, but do not mention the required dependencies. Why bother sharing undocumented snippets that rely on specific dependencies, Facebook? I've uploaded a complete project using `express` and `request`, totally based on the code Facebook provides. You can use the "Getting Started" guide posted above along the code found on the repository to bootstrap your own bot in less than 30 minutes.

After cloning [this repository](https://github.com/giannoug/facebook-messenger-bot), you'll need to run `npm install` to get the appropriate dependencies locally. Fill the appropriate details in `index.js`, specifically the `token` and `verify_token` variables must be set to your own. Start the application by running `npm start` on your server and make a redirection rule from your https-capable web server to `localhost:1337`. Setting the webhook URL in the Facebook application will complete succesfully, indicating Facebook was able to connect to your server. Send a message to your page, the bot will reply! Note that if you want others to access your bot, the application should be either public, or give the people specific access as administrators, developers or testers. Happy chatting!

> **Update 13/04/2016** - You can use the following directive on your https-enabled nginx server. Alternatively, just host the app on Heroku or your favorite app engine.

    location / {
        proxy_pass http://127.0.0.1:1337;
        proxy_redirect off;
    }

