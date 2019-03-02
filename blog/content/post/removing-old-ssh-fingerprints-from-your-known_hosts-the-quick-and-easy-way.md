+++
date = "2011-01-27"
slug = "2011/01/27/removing-old-ssh-fingerprints-from-your-known_hosts-the-quick-and-easy-way"
title = "removing old ssh fingerprints from your known_hosts the quick and easy way"
Categories = ["'*NIX'", "Technology"]
Tags = ["*nix", "shell", "ssh"]
+++

Ever have this problem? You just rebuilt a machine, and when you go to SSH into it, you get the following message:


    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    @    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!


Many people just go edit their `~/.ssh/known_hosts` file and carry on. But there is a faster/better way!

OpenSSH comes with a command called `ssh-keygen` that allows you to generate and manage all your keys, including your ssh fingerprints.

Simple usage for this would be:


    ssh-keygen -R HOSTNAME
