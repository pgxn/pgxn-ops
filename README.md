PGXN Ops
========

``` sh
./gho build manager
./gho deploy manager
./gho restart manager
```

This project contains [Ansible] playbooks for building deploying, and otherwise
managing the [PGXN][www] apps:

*   [PGXN Manager][]: [playbooks](manager)
*   [PGXN API][]: [playbooks](api)
*   [PGXN Site][www]: [playbooks](site)

Operations
----------

A simple script, [`gho`](./gho) provides shortcuts to manage each app.
Use it like so:

``` sh
./gho ACTION APP
```

Run `./gho --help` for the complete list of actions and apps.

The apps correspond to the playbooks directories for each app, `manager`, `api`,
and `site`. The actions are:

### `build`

Execute the `./$app/build.yml` playbook to download and build the app. This
action does not replace existing builds or affect the currently-running build.
If the current version is already built, this action will not rebuild it.

### `deploy`

Deploy the latest version of the app. This creates or replaces a symlink to
the version and then restarts (or starts) the app.

### `restart`

Restart an app.

Secrets
-------

One additional [`gho`](./gho) action, `./gho edit secrets`, edits the secrets
file. This file is protected by a password; contact @theory for details. The
contents of the file include database connection information and secrets
required for the [Mastodon account] to post releases.

  [Ansible]: https://www.ansible.com "Ansible is Simple IT Automation"
  [www]: https://pgxn.org "PGXN: PostgreSQL Extension Network"
  [PGXN Manager]: https://manager.pgxn.org
    "Distribute PostgreSQL Extensions on PGXN"
  [PGXN API]: https://api.pgxn.org/index.json
  [Mastodon account]: https://botsin.space/@pgxn "@pgxn@botsin.space"
