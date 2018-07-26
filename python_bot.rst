.. header::

   Setting up the bot: a guide for newbies by a clueless fool.


Initial Setup
=============
1. Create a GitLab account.
2. Generate a SSH \key (TODO: guide)
3. Add the ssh \key to your account
4. (If you don't have Contributer access) Fork the bot


Windows 10
==========

Dev Environment Setup
+++++++++++++++++++++
1. Install Python 3.6  (`Download link <https://www.python.org/ftp/python/3.6.5/python-3.7.0-amd64.exe>`_)
2. Install (`Git for Windows <https://git-scm.com/download/win>`_)
3. Configure SSH (TODO: ssh config, ssh key, etc)

Download Bot and dependencies
+++++++++++++++++++++++++++++
.. code-block: powershell
   # Install pipenv
   py -3 -m pip install --user pipenv
   # Clone the bot (if you forked the clone URL will be your forked repository)
   git@gitlab.com:python-discord/projects/bot.git
   cd .\bot
   # Install bot dependencies
   pipenv install
   pipenv shell



NOTES
=====
Python 3.6-only?

Create a server
   Duplicate the channels
   Duplicate the roles
Create a Discord app
Create a bot on the app. 
modify the yaml:
   guild id
   bot token
   channel IDs
   the role IDs
   the URL
   the schema

Add the bot to your server.
   Disable the "Public" option for the bot.
   Set "permissions" to administrator
   Manually build a bot invite URL: https://discordapp.com/oauth2/authorize?client_id=470122641705926657&scope=bot&permissions=8
   Go to the url and authorize the bot to access the server.

Comment out the code with "config-default".

---- new stuff -----
setup pycharm to use pipenv virtualenv

Lemon: 

pipenv is veeery straight forward. just install it, run pipenv sync --dev in the folder with the pipfile to set it up, and then we've got these scripts in the pipfile that you can execute with it
at the bottom of the pipfile you'll see these
[scripts]
start = "python -m bot"
lint = "python -m flake8"
build = "docker build -t pythondiscord/bot:latest -f docker/Dockerfile ."
push = "docker push pythondiscord/bot:latest"
buildbase = "docker build -t pythondiscord/bot-base:latest -f docker/Dockerfile.base ."
pushbase = "docker push pythondiscord/bot-base:latest"
buildci = "docker build -t pythondiscord/bot-ci:latest -f docker/ci.Dockerfile ."
pushci = "docker push pythondiscord/bot-ci:latest"
and you can run any of these with pipenv run lint for example.
basically you should only need to do pipenv run start to get it started once it's set up

"if you need the database or the site, you will need to follow the Project Guide: Site to set up the site and rabbitmq and rethink via docker compose.

so you do need the server - but a server with a single channel is enough for most cases.

like, the reason we have all those IDs in our constants is because we need to specifically check those channels
or post to them
KnownErrorYesterday at 11:59 PM
I just duplicated all of them because I had no idea what the bot needed/didn't need
lemonYesterday at 11:59 PM
yeah.
July 25, 2018
lemonToday at 12:00 AM
well, the bot will be forgiving there. it doesn't try to assert that those channel IDs exist
you have to import them from bot.constants and use them manually before anything really happens
I mean, many of the bot commands will fail
but that's not important
not if you're writing bot.roll()
so perhaps that section could be a bit more like "if you want a complete duplicate server for testing, you can do this, but for most purposes a server with a single channel will do the job just fine."
the important thing is that they understand the relationship between the yaml and the constants import

yeah the roles are mostly used with the with_role decorator
to restrict some commands
if the IDs don't exist, the decorator will always fail
so the commands will be unavailable
but, again, to most contribs working on a simple feature, it doesn't matter if defcon works or not
you feel me?
Running the bot - The last step for running the bot requires commenting out the line of code with “config-default” in it, this is located within constants.py
this is not necessary
if you make a config.yml, it will use that.
and git will also ignore it
even if the default is there
you can also mix them. if you make a config.yml with only one role in it, it'll use that role and then the rest of config-default.yml



