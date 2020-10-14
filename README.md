# Simple build

simple-build is a free and open source automation server.

It tries to be as simple as possible and is useful for users who are
familiar with linux and bash.

## Features

## Non-features (requires manual steps)

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

Create the folder to store all jobs: `mkdir /tmp/jobs`.

Create the job folder:

    $ mkdir /tmp/jobs/first/
    $ mkdir /tmp/jobs/first/workspace
    $ mkdir /tmp/jobs/first/builds

Create the job's build script: `vim /tmp/jobs/first/build`:

    echo Hello world

Run the job:

    $ JOBS=/tmp/jobs simple-build/run-job first

Create a cronjob for the job:

    $ crontab -e
    JOBS=/tmp/jobs /home/joe/simple-build/run-job first
