+-----------------------------------------------------------------------------------------+
|                _    ____      _       ____ _           _    ___                         |
|               / \  |  _ \    / \     / ___| |__   __ _| |_ / _ \ _ __  ___              |
|              / _ \ | |_) |  / _ \   | |   | '_ \ / _` | __| | | | '_ \/ __|             |
|             / ___ \|  _ <  / ___ \  | |___| | | | (_| | |_| |_| | |_) \__ \             |
|            /_/   \_\_| \_\/_/   \_\  \____|_| |_|\__,_|\__|\___/| .__/|___/             |
|                                                                 |_|                     |
+--------+--------------------------------------------------------------------------------+
| README |
+--------+
|
|    PLEASE READ THIS README AND THE DOCUMENTATIONS CAREFULLY TO AVOID CONFUSION
|
|    This script extension for Hubot(https://hubot.github.com/) allows users
|    to use ARA features inside of various chat services supported by hubot.
|    This README will focus on Slack(https://slack.com/is)
|
+-----------+-----------------------------------------------------------------------------+
| 1.INSTALL |
+-----------+
|
|    #---------#
|     1.1 HUBOT
|    #---------#
|
|      To install hubot follow the official guide on github's page
|        https://hubot.github.com/docs/
|
|      Specify an adapter on install that supports your chat service.
|      For Slack and Atlassian HipChat, official adapters exist.
|
|        Slack
|          https://github.com/slackhq/hubot-slack
|        HipChat
|          https://github.com/hipchat/hubot-hipchat
|        The github pages provide guides on how to set them up and use them.
|
|    #-----------#
|     1.2 SCRIPTS
|    #-----------#
|
|      Move the content of the folder "installation_files" to your hubot root directory.
|
|      Install dependencies by running this commands once from your bot directory:
|         npm install --save hubot-auth
|         npm install --save async
|         npm install --save request
|         npm install --save async-polling
|
|	   Also you will need to add "hubot-auth" in your external-scripts.json in the folder
|	   Cleaning up the external-scripts.json to only contain scripts you want to use
|	   will prove helpful. You need to keep "hubot-help" and "hubot-auth".
|
|	   Remove hubot-scripts.json from the folder 
|
|      Make sure your hubot(node js) port(default: 8080) is open and unused.
|
|      To configure the Hubot listening port configure the following environment variable:
|        EXPRESS_PORT - the port number to use, e.g. "9090"
|
|    #-------------#
|     1.3 CONFIGURE
|    #-------------#
|
|      For the hubot script extension to work, configure the needed environment variables.
|      All unset variables will throw warnings into the console
|
|      Environment variables to configure:
|
|        HUBOT_ARACHATOPS_USERNAME
|          - of an admin user for your Automic installation, e.g. "100/ARABOT/AUTOMIC"
|        HUBOT_ARACHATOPS_PASSWORD
|          - of an admin user for your Automic installation
|        HUBOT_ARACHATOPS_APIACCESS
|          - the rest api base url, e.g. "http://<ARA server hostname>/ara/api/data/v1"
|
|        HUBOT_AUTH_ADMIN
|          - list of user ids with admin role and can give roles to other chat users
|
|      More hubot-auth documentation: https://github.com/hubot-scripts/hubot-auth
|
|	   Approvals can be made by the "approver" role(!) you will have to add these roles
|	   to users with the hubot-auth command "<user> has <role> role"(or similar)
|
|	   Optional:
|	   To persist data hubot gathers like user roles hubot-redis-brain is needed.
|      Hubot script:  https://github.com/hubot-scripts/hubot-redis-brain
|	   Redis itself:  https://redis.io/topics/quickstart
|	   For Windows: https://github.com/MSOpenTech/redis/releases
|
|	   Make sure to secure your redis server by following the steps in the redis quickstart
|	   (Linked above)
|
+---------+-------------------------------------------------------------------------------+
| 2.USAGE |
+---------+
|
|    #-------#
|     2.1 BOT
|    #-------#
|
|      Please refer to the hubot documentation for specific instructions
|        https://hubot.github.com/docs/deploying/
|
|      Configuring for different Adapters
|        https://hubot.github.com/docs/adapters/
|
|      Some available adapters might not be listed and have to be found manually online.
|
|      IMPORTANT: Specifying your adapter when starting your bot!
|
|      for slack you can start your bot using(no quotes):
|       "./bin/hubot --adapter slack"
|
|      Get a description on how to form your commands: "<your_choosen_bot_name> help"
|      Get help on getting started: "<your_choosen_bot_name> Hey"
|
|    #------------#
|     2.2 REST API
|    #------------#
|
|      To use notification abilities you can use these REST resources:
|        POST: <baseURL>/notification/<channel>
|        POST: <baseURL>/notification
|
|      just pass your message as application/JSON like this:
|      {
|         "message":"YOUR\nMESSAGE\nHERE"
|      }
|
|      It will be sent to your specified channel or all channels if you don't specify one.
|
|      HUBOT_ARANOTIFY_ROOMS
|        - default rooms to use when sending to all channels
|          You can specify multiple channel by separating them with a semicolon(';'):
|            "MyInternalChannelName;MyInternalChannelName2"
|
|      Specify internal channel names in the environment variable AND IN THE REST URL,
|      to get them use this command in your room:
|        "<your_choosen_bot_name> get internal room name"
|
+-----------+-----------------------------------------------------------------------------+
| LIBRARIES |
+-----------+
|
|    https://github.com/request/request
|    https://github.com/caolan/async
|    https://github.com/hubot-scripts/hubot-auth
|    https://github.com/cGuille/async-polling
|
+-----------------------------------------------------------------------------------------+
