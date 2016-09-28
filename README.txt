////README////
***CONTENT***
1.About
2.Install
3.How to use


/**1.ABOUT***/
PLEASE READ THIS README AND THE DOCUMENTATIONS CAREFULLY TO AVOID CONFUSION

This script extension for Hubot(https://hubot.github.com/) allows users
to use ARA features inside of various chat services supported by hubot.
This README will focus on Atlassian HipChat(https://www.atlassian.com/software/hipchat)
and Slack(https://slack.com/is)


/**2.Install***/
This part of this README file will guide you throught the installation of included files.

->Install hubot(https://hubot.github.com/docs/)
To install hubot please follow the official guide on github's page(linked above)
Please note that, when promted for an adapter you will need to specify
an adapter that supports your chat service.
For Slack and Atlassian HipChat there are official adapters by the creators of these services

  Slack -> https://github.com/slackhq/hubot-slack
  HipChat -> https://github.com/hipchat/hubot-hipchat
  On the github pages for these adapters you will find detailed guides on how to set them up and use them

-> install the scripts
Move the content of the folder "installation_files" into your chosen hubot root directory

to install dependencies run the commands once from the root directory of your bot(without quotes):
"npm install --save request"
"npm install --save async"
“npm install --save async-polling“
"npm install --save hubot-auth"

IMPORTANT: you also want to make sure your hubot(node js) port(default is: 8080) is open and unused.
To configure the Hubot listening port configure the following environment variable:
EXPRESS_PORT – the port number to use, e.g. "9090"

->Configure
For the hubot script extension to work you will need to configure the needed environment variables.
All unset variables will throw warnings into the console

Environment variables to configure:
ATTENTION: PLEASE MAKE SURE YOUR URL DOES NOT END WITH A '/' CHARACTER AS THIS WILL BREAK THE BOT

HUBOT_ARACHATOPS_USERNAME - the username of an admin user to use on your Automic installation, e.g. "100/ARABOT/AUTOMIC"
HUBOT_ARACHATOPS_PASSWORD - the password to use on your Automic installation
HUBOT_ARACHATOPS_APIACCESS - the rest api base url, e.g. "http://<ARA server hostname>/ara/api/data/v1"


/**3.How to use***/
Please refer to the hubot documentation on further instructions(starting the bot)
Windows: https://hubot.github.com/docs/deploying/windows/#starting-stopping-and-restarting-hubot
Unix: https://hubot.github.com/docs/deploying/unix/#starting-stopping-and-restarting-hubot
Heroku: https://hubot.github.com/docs/deploying/heroku/

Please refer to Hubot documentation (https://hubot.github.com/docs/adapters/) for more information on how to configure Hubot for different chat clients. Or do a Google search as there are many tutorials available, .e.g. "Hubot Slack Tutorial".

IMPORTANT: You will have to start your bot with specifying your adapter

for slack you can start your bot using(no quotes): 
 "./bin/hubot --adapter slack"

For a detailed description and information on how to form your commands please type in "<your_choosen_bot_name> help"
For help on how to get started please type in "<your_choosen_bot_name> Hey"

To use notification abilities you can use these REST resources:
POST: <baseURL>/notification/<channel>
POST: <baseURL>/notification

just pass your message as application/JSON like this:
{
   "message":"YOUR\nMESSAGE\nHERE"
}
and it will be sent to either your specified channel if you do so, or all channels if you don't specify one, configured under the environment variable HUBOT_ARANOTIFY_ROOMS
In this variable you can specify multiple channel by separating them with a semicolon(';') example: "MyInternalChannelName;MyInternalChannelName2"
You will need to specify internal channel names in the environment variable AND IN THE REST URL,
to get them use the command: "<YourBotName> get internal room name"(without quotes) in the room you want to get the name of

//////////////
Used Libraries
https://github.com/request/request
https://github.com/caolan/async
https://github.com/hubot-scripts/hubot-auth
https://github.com/cGuille/async-polling
