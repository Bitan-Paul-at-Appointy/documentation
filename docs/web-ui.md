---
id: web-ui
title: Temporal Web UI
sidebar_label: Web UI
sidebar_position: 9
description: This guide is an overview of the Temporal Web UI.
toc_max_heading_level: 4
tags:
- term
- web-ui
---

<!-- THIS FILE IS GENERATED. DO NOT EDIT THIS FILE DIRECTLY -->

The Temporal Web UI provides users with Workflow Execution state and metadata for debugging purposes.
It ships with every <a class="tdlp" href="/cli/index#">Temporal CLI<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is the Temporal CLI?</span><br /><br /><span class="tdlppd">The Temporal CLI is the most recent version of Temporal's command-line tool.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/cli/index#">Learn more</a></span></span></a> release and [Docker Compose](/kb/all-the-ways-to-run-a-cluster#docker--docker-compose) update and is available with [Temporal Cloud](/cloud).

You can configure the Temporal Web UI to work in your own environment.
See the <a class="tdlp" href="/references/web-ui-configuration#">UI configuration reference<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">Temporal Web UI configuration reference</span><br /><br /><span class="tdlppd">The Temporal Web UI Server uses a configuration file for many of the UI's settings.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/references/web-ui-configuration#">Learn more</a></span></span></a>.

Web UI open source repos:

- [temporalio/ui](https://github.com/temporalio/ui)
- [temporalio/ui-server](https://github.com/temporalio/ui-server)

The Web UI is packed with several features.

### Namespaces

All Namespaces in your self-hosted Cluster or Temporal Cloud account are listed under **Namespaces** in the left section of the window.
You can also switch Namespaces from the Workflows view by selecting from the Namespace switcher at the top right corner of the window.
After you select a Namespace, the Web UI shows the Recent Workflows page for that Namespace.
In Temporal Cloud, users can access only the Namespaces that they have been granted access to.
For details, see [Namespace-level permissions](/cloud/#namespace-level-permissions).

### Recent Workflows

Recent Workflows lists all Workflow Executions run in the past 24 hours.
The default number shown is 1,000 Workflow Executions.

Users can list Workflow Executions by any of the following:

- Status
- <a class="tdlp" href="/workflows#workflow-id">Workflow ID<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Workflow Id?</span><br /><br /><span class="tdlppd">A Workflow Id is a customizable, application-level identifier for a Workflow Execution that is unique to an Open Workflow Execution within a Namespace.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#workflow-id">Learn more</a></span></span></a>
- <a class="tdlp" href="/workflows#workflow-type">Workflow Type<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Workflow Type?</span><br /><br /><span class="tdlppd">A Workflow Type is a name that maps to a Workflow Definition.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#workflow-type">Learn more</a></span></span></a>
- Start time
- End time
- A <a class="tdlp" href="/visibility#list-filter">List Filter<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a List Filter?</span><br /><br /><span class="tdlppd">A List Filter is the SQL-like string that is provided as the parameter to an Advanced Visibility List API.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/visibility#list-filter">Learn more</a></span></span></a>

For start time and end time, users can set their preferred date and time format as one of the following:

- UTC
- Local
- Relative

Select a Workflow Execution to view the Workflow Execution's History, Workers, and pending Activities.

#### History

This is a view of the <a class="tdlp" href="/workflows#event">Events<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is an Event?</span><br /><br /><span class="tdlppd">Events are created by the Temporal Cluster in response to external occurrences and Commands generated by a Workflow Execution.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#event">Learn more</a></span></span></a> and Event fields within the Workflow Execution.
Approximately <a class="tdlp" href="/references/events#">40 different Events<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">Events reference</span><br /><br /><span class="tdlppd">Events are created by the Temporal Cluster in response to external occurrences and Commands generated by a Workflow Execution.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/references/events#">Learn more</a></span></span></a> can appear in a Workflow Execution's Event History.

The top of the page lists the following execution metadata:

- <a class="tdlp" href="/workflows#workflow-type">Workflow Type<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Workflow Type?</span><br /><br /><span class="tdlppd">A Workflow Type is a name that maps to a Workflow Definition.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#workflow-type">Learn more</a></span></span></a>
- <a class="tdlp" href="/workflows#run-id">Run ID<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Run Id?</span><br /><br /><span class="tdlppd">A Run Id is a globally unique, platform-level identifier for a Workflow Execution.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#run-id">Learn more</a></span></span></a>
- Start Time and Close Time
- <a class="tdlp" href="/workers#task-queue">Task Queue<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Task Queue?</span><br /><br /><span class="tdlppd">A Task Queue is a first-in, first-out queue that a Worker Process polls for Tasks.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workers#task-queue">Learn more</a></span></span></a>
- Parent and Parent ID
- <a class="tdlp" href="/workflows#state-transition">State Transitions<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a State Transition?</span><br /><br /><span class="tdlppd">A State Transition is a unit of progress by a Workflow Execution.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/workflows#state-transition">Learn more</a></span></span></a>

The Input and Results section displays the function arguments and return values for debugging purposes.
Results are not available until the Workflow finishes.

The Recent Events tab has the following views:

- Timeline: A chronological or reverse-chronological order of events with a summary.
  Clicking into an Event displays all details for that Event.
  Clicking “Expand all” displays all Event details.
  Similarly, clicking “Collapse all” collapses the table and displays only the summary.
- Compact: A logical grouping of Activities, Signals and Timers.
- JSON: The full JSON code for the workflow.

#### Download Event History

The entire Workflow Execution Event History, in JSON format, can be downloaded from this section.

#### Terminate Workflow

Workflow Executions can be Terminated directly from the UI.
A custom note can be logged from the UI when that happens.

#### Workers

Displays the Workers currently polling on the Workflow Task Queue with a count.
If no Workers are polling, an error displays.

#### Pending Activities

Displays a summary of recently active and/or pending Activity Executions.
Clicking a pending Activity directs the user to the Pending Activities tab to view details.

#### Stack Trace

The screen shows the captured result from the [\_\_stack_trace](/workflows#stack-trace-query) Query.
The Query is performed when the tab is selected.
It works only if a Worker is running and available to return the stack trace.

#### Queries

Lists all Queries sent to the Workflow Execution.

### Schedules

On Temporal Cloud and self-hosted Temporal Cluster Web UI, the Schedules page lists all the [Schedules](/workflows#schedule) created on the selected Namespace.

Click a Schedule to see details, such as configured frequency, start and end times, and recent and upcoming runs.

### Settings

On Temporal Cloud, **Settings** is visible only to [Global Admins](/cloud/#account-level-roles).

Click **Settings** to see and manage the list of users in your account and to set up integrations such as [Observability](/cloud/how-to-monitor-temporal-cloud-metrics#configure-a-metrics-endpoint-using-temporal-cloud-ui) and [Audit logging](/cloud/how-to-manage-audit-logging).

On self-hosted Temporal Clusters, manage your users, metrics, and logging in your <a class="tdlp" href="/references/configuration#">server configuration<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">Temporal Cluster configuration reference</span><br /><br /><span class="tdlppd">Much of the behavior of a Temporal Cluster is configured using the `development.yaml` file.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/references/configuration#">Learn more</a></span></span></a>.

<!--
AB: Commenting because this is redundant now? Also this needs to be updated for self-hosted clusters.
Displays the following information:

- Description of the Namespace.
- Owner: Namespace owner.
- Global?: Whether the Namespace is a Global Namespace
- Retention Period: Namespace Retention Period
- History Archival: Whether History Archival is enabled
- Visibility Archival: Whether Visibility Archival is enabled
- Failover Version: Namespace Failover Version
- Clusters: Cluster information -->

### Archive

On self-hosted Temporal Clusters, Archive shows <a class="tdlp" href="/clusters#archival">Archived<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is Archival?</span><br /><br /><span class="tdlppd">Archival is a feature that automatically backs up Event Histories from Temporal Cluster persistence to a custom blob store after the Closed Workflow Execution retention period is reached.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/clusters#archival">Learn more</a></span></span></a> data of your Workflow Executions on the Namespace.

To see data in your self-hosted Temporal Cluster, you must have [Archival set up and configured](/cluster-deployment-guide#archival).

For information and details on the Archive feature in Temporal Cloud, contact your Temporal representative.

### Codec Server

The Web UI can use a [Codec Server](/dataconversion#codec-server) with a custom Data Converter to decode inputs and return values.
For details, see [Securing your data](/production-readiness/develop#securing-your-data).
The UI supports both a [Codec Server endpoint](/production-readiness/develop#web-ui) and the `tctl` plugin port.

For details on setting the Codec Server endpoint, see [Codec Server setup](/production-readiness/develop#codec-server-setup).

