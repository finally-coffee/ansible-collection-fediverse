# `finallycoffee.fediverse.mastodon` ansible role

## Overview

This role aims to automate as much as possible with running a docker container
based mastodon setup. It provides you with the streaming container, sidekiq and
web (api) as well an nginx routing the application traffic.

You need to provide a postgresql database, the redis server, optionally an
elasticsearch instance and the mail server. Roles providing components are linked,
if applicable.

### Usage

The minimum configuration could be as follows:

```yaml
mastodon_domain: finally.coffee
# Optional, if you want to host your frontend + api somewhere else
mastodon_web_domain: frontend.some.website

# you need to provide and manage the following secrets
mastodon_secret_key: very_long_secret
mastodon_otp_secret: also_very_long_secret
mastodon_vapid_public_key: check_mastodon_docs_for_this
mastodon_vapid_private_key: see_above
```

#### Database

The database configuration is as follows:

```yaml
mastodon_database_host: postgres.local
mastodon_database_port: 5432 #optional, defaults to this
mastodon_database_user: mastodont
mastodon_database_pass: hopefully_secure
mastodon_database_name: mastodon
```

For seeding the database during initial deployment, you need to set
`mastodon_seed_database: true` exactly once (when it succeeds).

### Redis

As of writing this, it seems that atleast one component of mastodon can't
deal with a password for redis, leading to the need to run redis without
authentification for all components:

```yaml
mastodon_redis_url: unix:///var/run/redis/mastodon.sock
```

#### Mail

The mail server for verifications and notifications can be configured as followed:

```yaml
mastodon_mail_server: mail.example.org
mastodon_mail_user: mailuser@mydomain.org
mastodon_mail_password: very_secure_password_for_mailing_account
```

For further Configuration, see [`defaults/main.yml`](defaults/main.yml) to
override further keys for configuration
