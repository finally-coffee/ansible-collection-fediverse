# `finallycoffee.fediverse.sharkey` ansible role

## Configuration

## Behind a proxy

The ansible role itself will respect system proxies (in the env var `HTTP_PROXY`/`https_proxy`).

To use this role with a registry like Artifactory or Nexus3,
set `sharkey_repo_server` to your registry server with full
protocol, hostname, port. For example `sharkey_repo_server: "https://my.orgs.registry.local:8443/sharkey-internet-proxy/"`
