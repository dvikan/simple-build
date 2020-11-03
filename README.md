# Simple build

simple-build is a free and open source automation server.

It tries to be as simple as possible and is useful for users who are
familiar with linux and bash.

Features:

* Logging of each job

## Non-features (requires manual steps)

* automatic job schedueling
* ssh keys setup

## Modules

Core modules:

* git-pull Fetch source codes from git repository
* composer-install Install composer dependencies
* php-lint Lint php source code
* tarball-create Create a tarball
* deploy-fs Extract a tarball into a local file system directory

Your custom modules can be placed in the contrib folder.

## Getting started

Clone this repository:

    $ git clone https://github.com/dvikan/simple-build ~/

Modify PATH: `PATH="$HOME/simple-build/bin:$PATH"`

Create a job:

    $ create-job first

List all jobs:

    $ list-jobs

Run a job:

    $ run-job first

Delete a job:

    $ delete-job first

Run a job from crontab:

    $ crontab -e
    * * * * * $HOME/simple-build/bin/run-job first

## Anatomy of the job

Jobs are stored in `~/.jobs` and a job looks like this:

    $ tree ~/.jobs/test
    /home/u/.jobs/test
    ├── build
    ├── builds
    │   ├── 2020-10-15_18:46:20.tgz
    │   └── 2020-10-15_18:46:26.tgz
    ├── output.log
    └── workspace
        └── hello.php

    2 directories, 5 files

The `job` contains the job steps. The `workspace` contains the application source code.
The `builds` contains tarballs of the workspace. The `job.log` contains job output.
