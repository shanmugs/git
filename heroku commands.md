env vars importing and exporting  
```
heroku config -s -a api-sample > api-sample-config.txt

cat api-sample-config.txt | tr '\n' ' ' | xargs heroku config:set -a  api-sample

````

Description 	Steps 	Expected Output

Start a detached heroku command so that it runs on remote dyno

and doesn't depend of bandwidth of your local computer
```
 heroku run:detached --app=spare-staging-monkey rake db:reset  	
```
Warning: heroku update available from 7.7.10 to 7.19.3
Running rake db:seedreset on ⬢ spare-staging-monkey... done, run.3613 (Standard-1X)
Run 
```
heroku logs --app spare-staging-monkey --dyno run.3613 
```
to view the output.

To check the status of the command being executed

DYNO ID will be the id received in output from executing first step
```
heroku logs -t --app spare-staging-monkey --dyno <DYNO ID> 	
```
-t → tails/streams the log output
To stop a process that you started 	
```
heroku ps:stop --app spare-staging-monkey --dyno <DYNOID> 	
```
this stops the process and kills the dyno gracefully


Ensure you have the Heroku CLI installed. Copy/paste below and replace the heroku-app-name with the name of your Heroku app.

```
$ heroku drains:add https://sss:ssssss@heroku.logdna.com/heroku/logplex?app=[heroku-app-name] --app [heroku-app-name]

heroku drains:add --app=graph-api-stg https://ssss:sssssssss@heroku.logdna.com/heroku/logplex?app=graph-api-stg

heroku drains:add --app=security-api-stg https://sss:sssss@heroku.logdna.com/heroku/logplex?app=security-api-stg

$ heroku drains:add https://ssssss:ssss@heroku.logdna.com/heroku/logplex?app=security-api-stg --app security-api-stg

```

## setting up specific version of addon(graphene db)

In order to create an add-on with specific version instead of latest version, we can use the following command.

This hold good for most of the addons.

``` heroku cli
heroku addons:create graphenedb --version v351 --app api-dev-1
```

## setting up logdna drains for heroku app

To setup log drains to logdna for a newly created heroku app you can go with the following commands

```
heroku drains:add --app=social-api-dev https://sssssssss:sssssssssss@heroku.logdna.com/heroku/logplex?app=social-api-dev
```

```
heroku drains:add --app=social-api-qa https://sssssssss:ssssssssss@heroku.logdna.com/heroku/logplex?app=social-api-qa
```

## setting up detached tasks on a heroku app

When there is a need to run some db seed/reseed/reset, you can run that in detached dynos so that it can run in background and not depend of user console being open for completion

```
heroku run:detached --app=spare-staging-monkey rake db:seed:perf_seeds
```

## tailing logs from a detached heroku task

Any background/detached task created can be looked up for logs using the following command

```
heroku logs -t --app spare-staging-monkey --dyno run.*
* - id for current run. you will get it from previous command
```

## setting up elastic search addon (specific version)

Elastic search addon can be setup using the followinf command.

we are specifying the size of instance by providing input `foundelasticsearch:dachs-ha` . We are specifying version of elastic search using input parameter `--elasticsearch-version` 

```
heroku addons:create foundelasticsearch:dachs-ha --elasticsearch-version 6.7.1 --app social-api-qa
```

## upgrading heroku stack version 

When an application stack(base image/container used by heroku app) needs to be upgraded,

```
heroku stack:set heroku-16 -a lab-monkey
```

## fetching heroku app config variables

When you want to import config variables of a specific heroku app

```
heroku config --json --app=lab-monkey
```



