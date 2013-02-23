Archive Team Warrior buildpack for Heroku
=========================================

This buildpack can be used to run warrior projects on Heroku. It includes the Python seesaw kit, a recent version of Wget+Lua and an Rsync binary compiled for Heroku.

Use an empty Git repository for your application; you don't need any code.

Specify this buildpack when you create your Heroku application:

    heroku create app --buildpack https://github.com/ArchiveTeam/heroku-archiveteam-warrior-buildpack.git

You'll need to set two configuration variables (with heroku config:set):

    WARRIOR_PROJECT      the URL to the Git repository of the project
    WARRIOR_DOWNLOADER   your nickname

You can optionally set:

    WARRIOR_CONCURRENT   the number of concurrent items (default: 2)
    WARRIOR_MAX_ITEMS    the number of items to download before
                         restarting the instance (default: 100)

To start an instance:

    heroku ps:scale seesaw=1

