Archive Team Warrior buildpack for Heroku
=========================================

This buildpack can be used to run warrior projects on Heroku. It includes the Python seesaw kit, a recent version of Wget+Lua and an Rsync binary compiled for Heroku.

You'll need the Heroku Toolbelt: https://toolbelt.heroku.com/

Create an empty Git repository for your application. You don't need any code.

```bash
git init yourapp
cd yourapp
git commit --allow-empty -m "First commit."
```

Create your Heroku application and specify this buildpack:

```bash
heroku apps:create --buildpack https://github.com/ArchiveTeam/heroku-buildpack-archiveteam-warrior.git
```

Set two configuration variables (with heroku config:set):

    WARRIOR_PROJECT      the URL to the Git repository of the project
    WARRIOR_DOWNLOADER   your nickname

e.g.
 
```bash
heroku config:set WARRIOR_PROJECT=https://github.com/... WARRIOR_DOWNLOADER=YOURNAME
```

You can optionally set:

    WARRIOR_CONCURRENT   the number of concurrent items (default: 2)
    WARRIOR_MAX_ITEMS    the number of items to download before
                         restarting the instance (default: 100)

                         set this to a lower value if the tasks
                         take a long time, or if you want to cycle
                         your instances faster.

Push your application to Heroku. You'll see the installation messages:

```bash
git push -u heroku master
```

Start an instance of the 'seesaw' process:

```bash
heroku ps:scale seesaw=1
```

Check the logs to see if your seesaw process works:

```bash
heroku logs --tail
```

