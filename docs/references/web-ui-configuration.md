---
id: web-ui-configuration
title: Temporal Web UI configuration reference
sidebar_label: Web UI config
description: The Temporal Web UI Server uses a configuration file for many of the UI's settings.
toc_max_heading_level: 4
tags:
- reference
- web-ui
---

<!-- THIS FILE IS GENERATED. DO NOT EDIT THIS FILE DIRECTLY -->

The Temporal Web UI Server uses a configuration file for many of the UI's settings.

An example development.yaml file can be found in the [temporalio/ui-server repo](https://github.com/temporalio/ui-server/blob/main/config/development.yaml).

Multiple configuration files can be created for configuring specific areas of the UI, such as Auth or TLS.

## enableUi

Enables the browser UI.
This configuration can be set dynamically with the <a class="tdlp" href="/references/web-ui-environment-variables#temporaluienabled">TEMPORAL_UI_ENABLED<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">Temporal Web UI environmental variables</span><br /><br /><span class="tdlppd">How to set  environmental variables for Temporal Web UI.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/references/web-ui-environment-variables#temporaluienabled">Learn more</a></span></span></a> environment variable.
If disabled—that is, set to `false`—the UI server APIs remain available.

```yaml
enableUi: true
```

## enableOpenApi

Enables the UI Server's Open API reference documentation at `/openapi/`.
This configuration can be set dynamically with the <a class="tdlp" href="/references/web-ui-environment-variables#temporalopenapienabled">TEMPORAL_OPEN_API_ENABLED<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">Temporal Web UI environmental variables</span><br /><br /><span class="tdlppd">How to set  environmental variables for Temporal Web UI.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/references/web-ui-environment-variables#temporalopenapienabled">Learn more</a></span></span></a> environment variable.
For example, if you are currently viewing the Web UI at `http://localhost:8080`, the page is available at [localhost:8080/openapi/](http://localhost:8080/openapi/).

```yaml
enableOpenApi: true
```

## cors

The name of the `cors` field stands for Cross-Origin Resource Sharing.
Use this field to provide a list of domains that are authorized to access the UI Server APIs.

```yaml
cors:
  allowOrigins:
    - http://localhost:3000 # used at development by https://github.com/temporalio/ui
```

## refreshInterval

How often the configuration UI Server reads the configuration file for new values.
Currently, only [tls](#tls) configuration values are propagated during a refresh.

```yaml
refreshInterval: 1m
```

## temporalGrpcAddress

The frontend adddress for the Temporal Cluster.

The default address is localhost (127.0.0.1:7233).

```yaml
temporalGrpcAddress: default
```

## port

The port used by the Temporal Web UI Server and any APIs.

```yaml
port: 8080
```

## defaultNamespace

The default Namespace that the UI loads data for.
Defaults to `default`.

```yaml
defaultNamespace: default
```

## showTemporalSystemNamespace

When enabled—that is, when set to `true`—the Temporal System Namespace becomes visible in the UI.
The Temporal System Namespace lists Workflow Executions used by the Temporal Platform.

```yaml
showTemporalSystemNamespace: false
```

## feedbackUrl

The URL to direct users to when they click on the Feedback button in the UI.
If not specified, it defaults to the UI's GitHub Issue page.

```yaml
feedbackUrl: https://github.com/temporalio/ui/issues/new/choose
```

## notifyOnNewVersion

When enabled—that is, when set to `true`—a notification appears in the UI when a newer version of the [Temporal Server](/clusters#temporal-server) is available.

```yaml
notifyOnNewVersion: true
```

## auth

Auth configuration.

```yaml
auth:
  enabled: false
  providers:
    - label: Auth0 oidc # for internal use; in future may expose as button text
      type: oidc # for futureproofing; only oidc is supported today
      providerUrl: https://myorg.us.auth0.com/
      clientId: xxxxxxxxxxxxxxxxxxxx
      clientSecret: xxxxxxxxxxxxxxxxxxxx
      scopes:
        - openid
        - profile
        - email
      callbackUrl: http://localhost:8080/auth/sso/callback
      passIdToken: false
      options: # added as URL query params when redirecting to auth provider
        audience: myorg-dev
        organization: org_xxxxxxxxxxxx
        invitation:
```

## tls

Transport Layer Security (TLS) configuration.

```yaml
tls:
  caFile:
  certFile:
  keyFile:
  caData:
  certData:
  keyData:
  enableHostVerification: false
  serverName:
```

## codec

Codec Server configuration.

```yaml
codec:
  endpoint: http://your-codec-server-endpoint
  passAccessToken: false
```

## disableWriteActions

Prevents the user from executing Workflow Actions on the Web UI.

This option affects Bulk Actions for Recent Workflows as well as Workflow Actions on the Workflow Details page.

```yaml
disableWriteActions: false
```

:::note
`disableWriteActions` overrides the configuration values of each individual Workflow Action.
Setting this variable to `true` disables all Workflow Actions on the Web UI.
:::

## workflowTerminateDisabled

Prevents the user from terminating Workflow Executions from the Web UI.

```yaml
workflowTerminateDisabled: false
```

## workflowCancelDisabled

Prevents the user from canceling Workflow Executions from the Web UI.

```yaml
workflowCancelDisabled: false
```

## workflowSignalDisabled

Prevents the user from signaling Workflow Executions from the Web UI.

```yaml
workflowSignalDisabled: false
```

## workflowResetDisabled

Prevents the user from resetting Workflows from the Web UI.

```yaml
workflowResetDisabled: false
```

