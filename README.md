# `finallycoffee.fediverse` ansible collection

## Overview

Ansible collection containing roles and playbooks for automating fediverse
software like Pixelfed, Mastodon, Funkwhale etc. The aim of this repository
is to cover a common szenario with a dockerized setup and a database already
available.

## Roles

- [`fediwall`](roles/fediwall/README.md): deployment of [Fediwall](https://fediwall.social),
  a media wall for mastodon inspired by mastowall.

- [`gotosocial`](roles/gotosocial/README.md): deployment of [GoToSocial.org](https://gotosocial.org/),
  an ActivityPub social network server, in a docker container.

- [`mastodon`](roles/mastodon/README.md): deployment using a container based
  setup, able to use webfinger delegation.

## License

[CNPLv7+](LICENSE.md): Cooperative Nonviolent Public License
