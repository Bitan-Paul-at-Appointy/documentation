---
id: index
title: Temporal Cloud documentation
sidebar_label: Temporal Cloud
sidebar_position: 3
description: Temporal Cloud documentation, including explanations and usage.
toc_max_heading_level: 4
tags:
- term
- explanation
---

<!-- THIS FILE IS GENERATED. DO NOT EDIT THIS FILE DIRECTLY -->

[Temporal Cloud](https://temporal.io/cloud) is a managed, hosted Temporal environment that provides a platform for [Temporal Applications](/temporal/#temporal-application)—an alternative to deploying and operating your own [Temporal Cluster](/clusters).

Temporal Cloud is offered in units of isolation known as [Namespaces](/namespaces). You can provision and use one or more Cloud Namespaces. A typical use case is to use separate Namespaces as development, testing, integration, staging, and production environments for an application.

:::note Sign up for Temporal Cloud

To request a Temporal Cloud account, complete the [request form](https://pages.temporal.io/cloud-request-access).

:::

- [Get started with Temporal Cloud](/cloud/how-to-get-started-with-temporal-cloud)
- [Manage certificates in Temporal Cloud](/cloud/how-to-manage-certificates-in-temporal-cloud)
- [Manage Namespaces in Temporal Cloud](/cloud/how-to-manage-namespaces-in-temporal-cloud)
- [tcld (Temporal Cloud command-line interface)](/cloud/tcld)
- [Temporal Cloud release notes](/cloud/release-notes)

## Action

An Action is the fundamental pricing unit in <a class="tdlp" href="#">Temporal Cloud<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is Temporal Cloud?</span><br /><br /><span class="tdlppd">Temporal Cloud is a managed, hosted Temporal environment that provides a platform for Temporal Applications.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="#">Learn more</a></span></span></a>.

The following operations result in Actions, which are billed monthly.

**Workflows**

- **Workflow started.**
  Occurs via client start, client Signal-With-Start, <a class="tdlp" href="/workflows#continue-as-new">Continue-As-New<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is Continue-As-New?</span><br /><br /><span class="tdlppd">Continue-As-New is the mechanism by which all relevant state is passed to a new Workflow Execution with a fresh Event History.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#continue-as-new">Learn more</a></span></span></a>, or <a class="tdlp" href="/workflows#child-workflow">Child Workflow<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Child Workflow Execution?</span><br /><br /><span class="tdlppd">A Child Workflow Execution is a Workflow Execution that is spawned from within another Workflow.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#child-workflow">Learn more</a></span></span></a> start.
  If a Workflow start fails, an Action is not recorded.
- **Workflow reset.**
  Occurs when a <a class="tdlp" href="/workflows#">Workflow<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Workflow?</span><br /><br /><span class="tdlppd">In day-to-day conversations, the term "Workflow" frequently denotes either a Workflow Type, a Workflow Definition, or a Workflow Execution.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#">Learn more</a></span></span></a> is reset.
  (Actions that occur before a <a class="tdlp" href="/workflows#reset">Reset<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Reset?</span><br /><br /><span class="tdlppd">A Reset terminates a Workflow Execution, removes the progress in the Event History up to the reset point, and then creates a new Workflow Execution with the same Workflow Type and Id to continue.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#reset">Learn more</a></span></span></a> are counted even if they are no longer visible in <a class="tdlp" href="/workflows#event-history">Event History<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is an Event History?</span><br /><br /><span class="tdlppd">An append-only log of Events that represents the full state a Workflow Execution.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#event-history">Learn more</a></span></span></a>.)
- **Timer started.**
  Includes implicit Timers that are started by a Temporal SDK when timeouts are set, such as `AwaitWithTimeout` in Go or `condition` in TypeScript.
- **Search Attribute upsert requested.**
  Occurs after a Workflow starts and invokes `UpsertSearchAttributes`.
- **Signal sent.**
  Includes sending a <a class="tdlp" href="/workflows#signal">Signal<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Signal?</span><br /><br /><span class="tdlppd">A Signal is an asynchronous request to a Workflow Execution.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#signal">Learn more</a></span></span></a> from a client or from within a Workflow to another Workflow.
- **Query received.** <a class="tdlp" href="/workflows#query">Queries<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Query?</span><br /><br /><span class="tdlppd">A Query is a synchronous operation that is used to report the state of a Workflow Execution.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#query">Learn more</a></span></span></a> aren't recorded in Event History.
  An operation such as viewing the stack trace in the Temporal Cloud UI results in a Query.
- **Version marker recorded.**
  Occurs when a Workflow calls `get-version` or `patch`.
- **Side Effect recorded.**
  For a mutable <a class="tdlp" href="/workflows#side-effect">Side Effect<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Side Effect?</span><br /><br /><span class="tdlppd">A Side Effect is a way to execute a short, non-deterministic code snippet, such as generating a UUID, that executes the provided function once and records its result into the Workflow Execution Event History.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#side-effect">Learn more</a></span></span></a>, an Action occurs only when the value changes.
  (Be aware that some SDKs don't support Side Effects.)

**Activities**

- **Activity started or retried.**
  Occurs each time an Activity is started or retried.
- **Local Activity started.**
  Occurs each time a <a class="tdlp" href="/activities#local-activity">Local Activity<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Local Activity?</span><br /><br /><span class="tdlppd">A Local Activity is an Activity Execution that executes in the same process as the Workflow Execution that spawns it.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/activities#local-activity">Learn more</a></span></span></a> is started.
- **Activity Heartbeat recorded.**
  A Heartbeat call from Activity code counts as an Action only if it reaches the <a class="tdlp" href="/clusters#temporal-server">Temporal Server<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is the Temporal Server?</span><br /><br /><span class="tdlppd">The Temporal Server is a grouping of four horizontally scalable services.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/clusters#temporal-server">Learn more</a></span></span></a>.
  Temporal SDKs throttle <a class="tdlp" href="/activities#activity-heartbeat">Activity Heartbeats<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is an Activity Heartbeat?</span><br /><br /><span class="tdlppd">An Activity Heartbeat is a ping from the Worker that is executing the Activity to the Temporal Cluster. Each ping informs the Temporal Cluster that the Activity Execution is making progress and the Worker has not crashed.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/activities#activity-heartbeat">Learn more</a></span></span></a>.
  The default throttle is 80% of the <a class="tdlp" href="/activities#heartbeat-timeout">Heartbeat Timeout<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Heartbeat Timeout?</span><br /><br /><span class="tdlppd">A Heartbeat Timeout is the maximum time between Activity Heartbeats.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/activities#heartbeat-timeout">Learn more</a></span></span></a>.
  Heartbeats don't apply to Local Activities.

## Temporal Cloud Account Id

A Temporal Cloud Account Id is a unique identifier for a customer for the entire time they use Temporal Cloud.
Temporal Technologies assigns each Account Id, which is an opaque code of five or six alphanumeric characters, such as `f45a2`.

## Account-level Roles

When a Global Admin invites a user to join an account, the Global Admin selects one of the following Roles for that user:

- **Global Admin**
  - Has full administrative permissions across the account, including users and usage
  - Has Namespace Admin [permissions](/cloud/#namespace-level-permissions) on all [Namespaces](/namespaces) in the account
- **Developer**
  - Can create and update Namespaces; has full control over [Workflows](/workflows)
  - Has Namespace Admin permissions for each Namespace created by that user
- **Read-Only:** Can only read information

## Temporal Cloud Namespace Name

A Cloud Namespace Name is a customer-supplied name for a [Namespace](/namespaces) in Temporal Cloud.
Each Namespace Name, such as `accounting-production`, is unique within the scope of a customer's account.
It cannot be changed after the Namespace is provisioned.

Each Namespace Name must conform to the following rules:

- A Namespace Name must contain at least 2 characters and no more than 34 characters.
- A Namespace Name must begin with a letter, end with a letter or number, and contain only letters, numbers, and the hyphen (-) character.
- Each hyphen (-) character must be immediately preceded _and_ followed by a letter or number; consecutive hyphens are not permitted.
- All letters in a Namespace Name must be lowercase.

## Temporal Cloud Namespace Id

A Cloud Namespace Id is a globally unique identifier for a [Namespace](/namespaces) in Temporal Cloud.
A Namespace Id is formed by concatenating the following:

1. A <a class="tdlp" href="#temporal-cloud-namespace-name">Namespace Name<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Cloud Namespace Name?</span><br /><br /><span class="tdlppd">A Cloud Namespace Name is a customer-supplied name for a Namespace in Temporal Cloud.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="#temporal-cloud-namespace-name">Learn more</a></span></span></a>
1. A period (.)
1. The <a class="tdlp" href="#temporal-cloud-account-id">Account Id<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Temporal Cloud Account Id?</span><br /><br /><span class="tdlppd">A Temporal Cloud Account Id is a unique identifier for a customer.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="#temporal-cloud-account-id">Learn more</a></span></span></a> to which the Namespace belongs

For example, for the Account Id `f45a2` and Namespace Name `accounting-production`, the Namespace Id is `accounting-production.f45a2`.

## Namespace-level permissions

A [Global Admin](/cloud/#account-level-roles) can assign permissions for any [Namespace](/namespaces) in an account.
A Developer can assign permissions for a Namespace they create.

For a Namespace, a user can have one of the following permissions:

- **Namespace Admin:** Can [create](/cloud/how-to-manage-namespaces-in-temporal-cloud#create-a-namespace) and [edit Namespaces](/cloud/how-to-manage-namespaces-in-temporal-cloud#manage-namespaces); can create, rename, update, and delete [Workflows](/workflows)
- **Write:** Can create, rename, update, and delete Workflows within the Namespace
- **Read-Only:** Can only read information from the Namespace
