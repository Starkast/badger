## Dependencies

### Redis

    brew install redis
    redis-server

### Environment variables

HipChat (`heroku config --app starkastbot`)

    HUBOT_ADAPTER="hipchat"
    HUBOT_NAME="Badger"

    HUBOT_HIPCHAT_JID="xxx"
    HUBOT_HIPCHAT_PASSWORD="xxx"

IRC (`heroku config --app starkastircbot`)

    HUBOT_ADAPTER="irc"
    HUBOT_IRC_NICK="xxx"
    HUBOT_IRC_ROOMS="#foo"
    HUBOT_IRC_SERVER="xxx"
    HUBOT_IRC_UNFLOOD="true"

__TODO__: `HUBOT_IRC_UNFLOOD` doesn't help (tested on QuakeNet).

Both:

    HEROKU_URL="xxx" # heroku keep-alive trick
    REDISTOGO_URL="xxx" # redis-brain.coffee

## How to start

This starts hubot using the shell adapter:

    bin/hubot

More info: https://github.com/github/hubot/blob/master/docs/README.md

## How to add a script

Find script at http://hubot-script-catalog.herokuapp.com/.

Add it to `hubot-scripts.json`.

Don't forget to add dependencies to `package.json` with

    npm install --save <package>

More info:

* https://github.com/github/hubot-scripts#installing
* https://github.com/github/hubot/blob/master/docs/README.md#scripting

### Script variables

Add variable with

    heroku config:add KEY=value --app starkastbot|starkastircbot

#### title.coffee

    HUBOT_HTTP_INFO_IGNORE_URLS="github.com|twitter.com|imgur.com"

## Deployment

You want these remotes:

    $ git remote -v
    hipchat git@heroku.com:starkastbot.git (fetch)
    hipchat git@heroku.com:starkastbot.git (push)
    irc     git@heroku.com:starkastircbot.git (fetch)
    irc     git@heroku.com:starkastircbot.git (push)
    origin  git@github.com:Starkast/badger.git (fetch)
    origin  git@github.com:Starkast/badger.git (push)
