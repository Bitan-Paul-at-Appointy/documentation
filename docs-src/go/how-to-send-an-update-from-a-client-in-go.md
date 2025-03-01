---
id: how-to-send-an-update-from-a-client-in-go
title: How to send an Update from a Temporal Client in Go
sidebar_label: Send Update from Client
description: Use the UpdateWorkflow method on an instance of the Go SDK Temporal Client to send an Update to a Workflow Execution.
---

Invoke the UpdateWorkflow() method on an instance of the [Go SDK Temporal Client](https://pkg.go.dev/go.temporal.io/sdk/client#Client) to dispatch an [Update](/concepts/what-is-an-update) to a Workflow Execution.

You must provide the Workflow Id, but specifying a Run Id is optional.
If you supply only the Workflow Id (and provide an empty string as the Run Id param), the currently running Workflow Execution receives the Update.

<a class="dacx-source-link" href="https://github.com/temporalio/documentation-samples-go/blob/main/yourupdate/update/main_dacx.go">View source code</a>

```go
func main() {
// ...
	// Set the Update argument values.
	updateArg := yourupdate.YourUpdateArg{
		Add: n,
	}
	// Call the UpdateWorkflow API.
	// A blank RunID means that the Update is routed to the most recent Workflow Run of the specified Workflow ID.
	updateHandle, err := temporalClient.UpdateWorkflow(context.Background(), yourupdate.YourUpdateWFID, "", yourupdate.YourUpdateName, updateArg)
	if err != nil {
		log.Fatalln("Error issuing Update request", err)
	}
	// Get the result of the Update.
	var updateResult yourupdate.YourUpdateResult
	err = updateHandle.Get(context.Background(), &updateResult)
	if err != nil {
		log.Fatalln("Update encountered an error", err)
	}
	log.Println("Update succeeded, new total: ", updateResult.Total)
}
```
