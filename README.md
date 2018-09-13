# THIS REPOSITORY IS ARCHIVED

For current Reggie configuration, see https://github.com/magfest/infrastructure

# Magfest-specific ubersystem production configuration
If you're trying to do an install for the first time, please ignore this repo and follow the instructions here: https://github.com/magfest/simple-rams-deploy

Magfest-specific puppet configurations.
THIS IS A PUBLIC REPO, contains magfest-specific settings.

However, you should NEVER check in sensitive or secret information into this repo, like Stripe / AWS API keys.  That information
should only ever live on the control server.

# Setup notes
If you want to develop on magfest events, here are some magfest-specific instructions.

Each copy of the ubersystem-deploy repo is a collection of the deploy+code+plugins for ONE event.  If you want to develop for two events, you will need two copies of ubersystem-deploy, one for magprime, and one for magclassic.

Follow the instructions below for EACH event:

# How to get the magfest-specific config
follow [the normal instructions](https://github.com/magfest/ubersystem-deploy) EXCEPT you're going to do two things differently:

1) On the step that says "edit fabric-settings.ini to your liking", you will add the following line into your fabric-settings.ini file:

```
git_regular_nodes_repo = 'https://github.com/magfest/production-config'
```

Here's a one-liner that will do this for you
```bash
cd puppet/
{ cat fabric_settings.example.ini; echo -en "\ngit_regular_nodes_repo = 'https://github.com/magfest/production-config'";  } > fabric_settings.ini
```

This will pull in magfest-specific config into your local project.

2) On the step that asks you for an event_name, you will put one of the following: ```classic```, ```magstock```, or ```prime```
