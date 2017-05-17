# Liquid Investigations: Roadmap

This file will list all development tasks, split in bite-sized chunnks, with their respective deadlines.

Also view the [roadmap for Hoover improvements](https://github.com/hoover/search/wiki/Roadmap).

## Immediate interest

- [ ] Create liquid-core superuser from given params in the initialize.d script
- [ ] Use that superuser to create OAuth2 applications for Hoover and Dokuwiki
- [ ] Use the OAuth key ids/key secrets created to by that superuser to automatically configure Hoover and Dokuwiki
- [ ] Initially, configure Hoover with OAuth2 login enabled: [load this app](https://github.com/hoover/search/tree/master/hoover/contrib/oauth2)

## Milestone: finish by 31 Jul 2017

- [ ] Integrate additional technologies into the bundle
    - [ ] Hoover
        - [ ] scripts to control:
            - [ ] set SSO client_id/secret/url
            - [ ] app url
    - [ ] DokuWiki
        - [X] add ansible role to download dokuwiki code to `/opt/dokuwiki` and install php7.0 and libraries
        - [X] initialize.d script to copy code over to `/var/www/dokuwiki` and set the right permissions
        - [ ] [manually configure dokuwiki](https://github.com/liquidinvestigations/liquid-dokuwiki) with the oauth plugin to work with liquid-core
        - [ ] scripts to control:
            - [ ] promote/demote users to admin
            - [ ] set SSO client_id/secret/url
            - [ ] set app url
            - [ ] set wiki name
    - [ ] Davros
        - [ ] add ansible role to download and install davros code to `/opt/davros`, with the data folder symlinked to `/var/davros/data`
        - [ ] initialize.d script (if needed)
        - [ ] implement authentication wrapper around Davros that works with liquid-core
        - [ ] scripts to control:
            - [ ] set SSO client_id/secret/url
            - [ ] set app url
            - [ ] set instance name
    - [ ] Chat
        - [ ] install both a Matrix.org server and Rocket.chat server on a Odroid-C2 or Khadas VIM
        - [ ] benchmark both for cpu and memory consumption using light (5-10) user base
        - [ ] add ansible role for chosen chat server
        - [ ] initialize.d script (if needed)
        - [ ] scripts to control:
            - [ ] promote/demote users to admin
            - [ ] set SSO client_id/secret/url
            - [ ] set app url
            - [ ] set instance name
- [ ] Bare bones Admin UI: add hooks to the Django Admin User page
    - [X] Use Django admin from liquid-core as Admin UI
    - [X] Add new user hook:
        - [X] hypothesis
    - [X] Delete user hook:
        - [X] hypothesis
    - [ ] Promote/demote user to/from admin hook:
        - [ ] run DokuWiki promote/demote
        - [ ] run Chat promote/demote
    - [ ] Change board name and/or URL hook: run all apps control script to change SSO id/secret/url and name
    - [ ] Automatically create `oauth2_provider` application records in liquid-core's initialize.d script for:
        - [ ] DokuWiki
        - [ ] Hoover
        - [ ] Davros
        - [ ] Chat
- [ ] Network discovery between devices
    - [ ] Decide on how the networking aspect is implemented
    - [ ] Implement network discovery method

## Milestone: finish by 31 Oct 2017

- [ ] Refine Admin UI
    - [ ] Change default django templates for the Users page
    - [ ] Admin page to start/stop different components and configure them
    - [ ] Admin page for networking aspects (network discovery, joining/leaving a network)
- [ ] Initial configuration
    - [ ] Make the ARM boards mount `/` as read-only and `/var` as a ramdisk
    - [ ] Step by step initial configuration UI
        - [ ] Ask the user to plug-in HDD
        - [ ] Detect HDD information (name, type, size, port etc)
        - [ ] Ask the user to plug-in USB STICK
        - [ ] Detect USB STICK information (name, type, size, port etc)
        - [ ] HDD: Format and encrypt with LUKS, mount to `/var`
        - [ ] Run `initialize.d` scripts so the data is moved to the new `/var`
        - [ ] Write all configuration files to `/var/liquid-config`
        - [ ] Write primary and backup LUKS encryption keys, Wi-Fi apn+password, login username+password to USB STICK

## Milestone: finish by 31 Jan 2017

