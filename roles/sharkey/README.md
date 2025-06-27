# `finallycoffee.fediverse.sharkey` ansible role

## Configuration

Set the required `sharkey_config_url` variable to the domain you want sharkey to run on.

To extend/modify the sharkey configuration file (upstream: `default.yml`),
set your (structed) configuration in `sharkey_config` and it will be merged
over the upstream config file and the role built-in configuration.

### Docker compose

To extend/modify the compose project file (`compose.yml`), populate `sharkey_compose_file_overrides`.
Take care when overriding `sharkey_compose_file_role_overrides`, as this can
break the functionality of the ansible role.

## Behind a proxy

The ansible role itself will respect system proxies (in the env var `HTTP_PROXY`/`https_proxy`).

To use this role with a registry like Artifactory or Nexus3,
set `sharkey_repo_server` to your registry server with full
protocol, hostname, port. For example `sharkey_repo_server: "https://my.orgs.registry.local:8443/sharkey-internet-proxy/"`

## Stopping

### Docker compose

Set `sharkey_compose_state: "stopped"` to ensure all containers in the compose
project are stopped. This has the same effect as `docker compose stop`. Set
`sharkey_compose_state: "absent"` to not only stop all containers, but remove
them, the docker networks associated with the project etc. This is equivalent
to `docker compose down`.

> [!WARNING]
> Do not confuse `sharkey_compose_state` with `sharkey_state`!

## Deprovisioning

Set `sharkey_state: "absent"` to remove sharkey from the target, including
*all* application data, configuration files, container images.

> [!CAUTION]
> This removes all (user) data irrecoverably with no backup.
