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

* git-pull Fetch source code from git repository
* fs-fetch Fetch source code from file system
* composer-install Install composer dependencies
* php-lint Lint php source code
* tarball-create Create a tarball
* deploy-fs Extract a tarball into a local file system directory

Your custom modules can be placed in the contrib folder.

## Getting started

Clone this repository:

```bash
git clone https://github.com/dvikan/simple-build ~/
```

Modify PATH: `PATH="$HOME/simple-build/:$PATH"`

Create job:

```bash
sb create first
```

List all jobs:

```bash
sb list
```

Run job:

```bash
sb run first
```

Remove job:

```bash
sb remove first
```

Run job each 5 minutes via cron:

```bash
crontab -e
*/5 * * * * $HOME/simple-build/sb run first
```

## Anatomy of the job

Jobs are stored in `~/.jobs` and a job looks like this:

```bash
tree ~/.jobs/test
/home/u/.jobs/test
├── build
├── builds
│   ├── 2020-10-15_18:46:20.tgz
│   └── 2020-10-15_18:46:26.tgz
├── output.log
└── workspace
    └── hello.php

2 directories, 5 files
```

The `job` contains the job steps. The `workspace` contains the application source code.
The `builds` contains tarballs of the workspace. The `job.log` contains job output.
