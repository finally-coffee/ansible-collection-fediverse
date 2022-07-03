# `finallycoffee.fediverse.gotosocial` ansible role


## Configuration

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
