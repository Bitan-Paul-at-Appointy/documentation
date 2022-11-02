---
id: index
title: tctl v1.16 command reference
sidebar_label: index
description: How to use Temporal's tctl v1.16 developer tool
toc_max_heading_level: 4
---

<!-- THIS FILE IS GENERATED. DO NOT EDIT THIS FILE DIRECTLY -->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

:::note

This documentation reflects tctl version 1.17

:::

The Temporal CLI (tctl) is a command-line tool that you can use to interact with a Temporal Cluster.
It can perform <a class="tdlp" href="/namespaces#">Namespace<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><div class="tdlpc"><p class="tdlppt">What is a Namespace?</p><p class="tdlppd">A Namespace is a unit of isolation within the Temporal Platform</p><p class="tdlplm"><a href="/namespaces#">Learn more</a></p></div></a> operations (such as register, update, and describe) and <a class="tdlp" href="/workflows#">Workflow<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><div class="tdlpc"><p class="tdlppt">What is a Workflow?</p><p class="tdlppd">In day-to-day conversations, the term "Workflow" frequently denotes either a Workflow Type, a Workflow Definition, or a Workflow Execution.</p><p class="tdlplm"><a href="/workflows#">Learn more</a></p></div></a> operations (such as start
Workflow, show Workflow History, and Signal Workflow).

- <a class="tdlp" href="#install">How to install tctl<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><div class="tdlpc"><p class="tdlppt">How to install tctl</p><p class="tdlppd">You can install tctl in four ways, described in this topic.</p><p class="tdlplm"><a href="#install">Learn more</a></p></div></a>
- <a class="tdlp" href="#environment-variables">Environment variables for tctl<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><div class="tdlpc"><p class="tdlppt">Environment variables for tctl</p><p class="tdlppd">What are the environment variables for tctl?</p><p class="tdlplm"><a href="#environment-variables">Learn more</a></p></div></a>

## tctl commands

- [tctl activity](/tctl-v1/activity/)
- [tctl admin](/tctl-v1/admin/)
- [tctl batch](/tctl-v1/batch/)
- [tctl cluster](/tctl-v1/cluster/)
- [tctl dataconverter](/tctl-v1/dataconverter/)
- [tctl namespace](/tctl-v1/namespace/)
- [tctl taskqueue](/tctl-v1/taskqueue/)
- [tctl workflow](/tctl-v1/workflow/)

## Install

> The Temporal tctl documentation covers version 1.16 of the Temporal CLI.

You can install [tctl](/tctl-v1) in the following ways.

- Install locally by using [Homebrew](https://brew.sh/): `brew install tctl`
- Run locally together with Temporal Server in [docker-compose](https://github.com/temporalio/docker-compose): `docker exec temporal-admin-tools tctl YOUR COMMANDS HERE`
  - To invoke [tctl](/tctl-v1) as though it is installed locally (such as `tctl namespace describe`), set an alias: `alias tctl="docker exec temporal-admin-tools tctl"`
- Run the [temporal-admin-tools](https://hub.docker.com/r/temporalio/admin-tools) Docker image:
  - On Linux: `docker run --rm -it --entrypoint tctl --network host --env TEMPORAL_CLI_ADDRESS=localhost:7233 temporalio/admin-tools:1.14.0`
  - On macOS or Windows: `docker run --rm -it --entrypoint tctl --env TEMPORAL_CLI_ADDRESS=host.docker.internal:7233 temporalio/admin-tools:1.14.0`
  - If your Temporal Server is running on a remote host, change the value of `TEMPORAL_CLI_ADDRESS`.
  - To simplify command lines, create a `tctl` alias.
- Build it locally:
  1. Clone the [Temporal Server repo](https://github.com/temporalio/temporal).
  1. Run `make tctl`.
  1. Copy the `tctl` executable to any directory that appears in the `PATH` environment variable; for example, `/usr/bin/`.
- Install the latest version of the tctl in your `GOPATH`: `go install github.com/temporalio/tctl/cmd/tctl@latest`

**Note:** To use [tctl](/tctl-v1), you must have a Temporal Server running.

To see help for [tctl](/tctl-v1) commands, enter the following commands.

| Command             | Description                                                              |
| ------------------- | ------------------------------------------------------------------------ |
| `tctl -h`           | Display help for top-level commands and global options                   |
| `tctl namespace -h` | Display help for <a class="tdlp" href="/namespaces#">Namespace<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><div class="tdlpc"><p class="tdlppt">What is a Namespace?</p><p class="tdlppd">A Namespace is a unit of isolation within the Temporal Platform</p><p class="tdlplm"><a href="/namespaces#">Learn more</a></p></div></a> operations   |
| `tctl workflow -h`  | Display help for <a class="tdlp" href="/workflows#">Workflow<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><div class="tdlpc"><p class="tdlppt">What is a Workflow?</p><p class="tdlppd">In day-to-day conversations, the term "Workflow" frequently denotes either a Workflow Type, a Workflow Definition, or a Workflow Execution.</p><p class="tdlplm"><a href="/workflows#">Learn more</a></p></div></a> operations     |
| `tctl taskqueue -h` | Display help for <a class="tdlp" href="/tasks#task-queue">Task Queue<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><div class="tdlpc"><p class="tdlppt">What is a Task Queue?</p><p class="tdlppd">A Task Queue is a first-in, first-out queue that a Worker Process polls for Tasks.</p><p class="tdlplm"><a href="/tasks#task-queue">Learn more</a></p></div></a> operations |

## Global modifiers

You can supply the values for many of these modifiers by setting <a class="tdlp" href="#environment-variables">environment variables<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><div class="tdlpc"><p class="tdlppt">Environment variables for tctl</p><p class="tdlppd">What are the environment variables for tctl?</p><p class="tdlplm"><a href="#environment-variables">Learn more</a></p></div></a> instead of including the modifiers in a tctl command.

### --address

Specify a host and port for the Frontend Service.
The default is `127.0.0.1:7233`.

Alias: `--ad`

### --auto_confirm

Automatically confirm all prompts.

### --context_timeout

Specify a timeout for the context of an RPC call in seconds.
The default value is 5.

Alias: `--ct`

### --data_converter_plugin

Specify the name of the executable for a headers provider plugin.

Alias: `--dcp`

### --headers_provider_plugin

Specify the name of the executable for a custom Data Converter plugin.

Alias: `--hpp`

### --help

Display help for tctl in the CLI.

Alias: `-h`

### --namespace

Specify a Namespace.
By using this modifier, you don't need to specify a `--namespace` modifier for a sub-command.
The default Namespace is `default`.

Alias: `--ns`

### --tls_ca_path

Specify the path to a server Certificate Authority (CA) certificate file.

### --tls_cert_path

Specify the path to a public X.509 certificate file for mutual TLS authentication.
If you use this modifier, you must also use the `--tls_key_path` modifier.

### --tls_disable_host_verification

Disable verification of the server certificate (and thus host verification).

### --tls_key_path

Specify the path to a private key file for mutual TLS authentication.
If you use this modifier, you must also use the `--tls_cert_path` modifier.

### --tls_server_name

Specify an override for the name of the target server that is used for TLS host verification.
The name must be one of the DNS names listed in the server TLS certificate.
Specifying this modifier also enables host verification.

### --version

Display the version of tctl in the CLI.

Alias: `-v`

### --codec_endpoint

The URL and port number for a Codec Server.

## Environment variables

Setting environment variables for repeated parameters can shorten tctl commands.

### TEMPORAL_CLI_ADDRESS

Specify a host and port for the Frontend Service.
The default is `127.0.0.1:7233`.

### TEMPORAL_CLI_AUTHORIZATION_TOKEN

Specify a token to be used by the HTTP Basic Authorization plugin.

<!-- TODO: Add link to "Securing tctl" page or its equivalent when it exists. -->

### TEMPORAL_CLI_NAMESPACE

Specify a Namespace.
By setting this variable, you don't need to specify a `--namespace` modifier in a tctl command.
The default Namespace is `default`.

### TEMPORAL_CLI_PLUGIN_DATA_CONVERTER

Specify the name of the executable for a custom Data Converter plugin.

### TEMPORAL_CLI_PLUGIN_HEADERS_PROVIDER

Specify the name of the executable for a headers provider plugin.

### TEMPORAL_CLI_TLS_CA

Specify the path to a server Certificate Authority (CA) certificate file.

### TEMPORAL_CLI_TLS_CERT

Specify the path to a public X.509 certificate file for mutual TLS authentication.

### TEMPORAL_CLI_TLS_DISABLE_HOST_VERIFICATION

Set to disable verification of the server certificate (and thus host verification).

### TEMPORAL_CLI_TLS_KEY

Specify the path to a private key file for mutual TLS authentication.
If you set this variable, you must also set the `TEMPORAL_CLI_TLS_CERT` variable.

### TEMPORAL_CLI_TLS_SERVER_NAME

Specify an override for the name of the target server that is used for TLS host verification.
The name must be one of the DNS names listed in the server TLS certificate.
Setting this variable also enables host verification.

### TEMPORAL_CONTEXT_TIMEOUT

Specify a timeout for the context of an RPC call in seconds.
The default value is 5.
