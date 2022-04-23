# `finallycoffee.fediverse` ansible collection

## Overview

Ansible collection containing roles and playbooks for automating fediverse
software like Pixelfed, Mastodon, Funkwhale etc. The aim of this repository
is to cover a common szenario with a dockerized setup and a database already
available.

## Roles

- [`mastodon`](roles/mastodon/README.md): deployment using a container based
  setup, able to use webfinger delegation.

## License

[CNPLv7+](LICENSE.md): Cooperative Nonviolent Public License
