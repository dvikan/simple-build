# Simple build

simple-build is a free and open source automation server.

It tries to be as simple as possible and is useful for users who are
familiar with linux and bash.

## Features

## Non-features (requires manual steps)

* ssh keys managment

## Modules

Core modules:

* git-fetch Fetch source codes from git repository
* composer-install Install composer dependencies
* php-lint Lint php source code
* tarball-create Create a tarball
* deploy-fs Extract a tarball into a local file system directory

Your custom modules can be placed in the contrib folder.

## Getting started

Clone this repository:

    $ git clone https://github.com/dvikan/simple-build

Place `./bin` in path: `PATH="./bin:$PATH"

Create a job:

    $ create-job first

List all jobs:

    $ list-jobs

Run a job:

    $ run-job first

Delete a job:

    $ delete-job first

Create a cronjob for the job:

    $ crontab -e
    /home/joe/simple-build/bin/run-job first

## Todos

* Web hooks
