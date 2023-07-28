# `finallycoffee.fediverse.gotosocial` ansible role

## Configuration

The server name can be set using `gotosocial_config_host`, with `gotosocial_config_account_domain` being available when webfinger delegation is used:

```yaml
gotosocial_config_host: gotosocial.example.org
gotosocial_config_account_domain: example.org
```

### Database

The database can be configured using the `gotosocial_config_db_[address|port|user|password|database]` variables. the `[...]_type` defaults to `postgres`.

### Built-in LetsEncrypt client

To use the built-in letsencrypt client, set `gotosocial_config_letsencrypt_enabled: true`.

You are required to fill in a valid administrative email address into
`gotosocial_config_letsencrypt_email_address`.

The port letsencrypt will listen on defaults to `80` and can be set using
`gotosocial_config_letsencrypt_port` (if f.ex. the container lacks the permission
to bind to ports < 1024). Note that when `gotosocial_config_letsencrypt_enabled` is
`true`, the `gotosocial_config_letsencrypt_port` will by default be mapped to
_host_ port 80 on all interfaces!

This is fine when this is the only ACME client and allows easily changing
`gotosocial_config_letsencrypt_port` without breaking any functionality,
but with multiple acme clients all performing HTTP-01 challenges, you need to manually
overwrite `gotosocial_container_ports` to fit your needs.

### Advanced configuration

#### OIDC

OIDC can be configured using `gotosocial_config_oidc_*` variables, disabled by default. A minimal configuration could look like this:

```yaml
gotosocial_config_oidc_enabled: true
gotosocial_config_oidc_idp_name: "My fancy name for the configured IdP"
gotosocial_config_oidc_issuer: http://issuer/url
gotosocial_config_oidc_client_id: my_client_id
gotosocial_config_oidc_client_secret: my_client_secret
```
