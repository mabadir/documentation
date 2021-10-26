---
id: what-is-a-query
title: What is a Query?
description: A Query is a read-only synchronous request sent to a running Workflow Execution.
tags:
  - explanation
---

import CenteredImage from '../components/CenteredImage.js'
import {RelatedReadContainer, RelatedReadItem} from '../components/RelatedReadList.js'

<!-- prettier-ignore -->
import * as HowToQueryInGo from '../go/queries.md'
import * as HowToQueryInJava from '../java/queries.md'
import * as HowToQueryInPHP from '../php/queries.md'

A Query is a read-only synchronous message sent to a running Workflow Execution that requests data.

<CenteredImage
imagePath="/diagrams/query.svg"
imageSize="75"
title="Query"
/>

The state of a running Workflow Execution is constantly changing.
Queries are available to expose the internal Workflow Execution state to the external world.

- A Query is a synchronous call from a Temporal Client.
- A Query can carry arguments to specify which data it is requesting, as every Workflow can expose data to multiple types of Queries.
- A Query must never mutate the state of the Workflow Execution.
- If a Query is sent to a completed Workflow Execution, the final value is returned.
- Query handling logic is implemented as code within a [Workflow Definition](#what-is-a-workflow-definiton).
Query handling logic must be **read-only** and cannot change the Workflow Execution state in any way, or contain any blocking code.
This means that Query handling logic can not spawn Activity Executions.

In many SDKs the Temporal Client exposes a predefined `_stack_track_` Query that returns the stack trace of all the threads owned by that Workflow Execution.
This is a great way to troubleshoot a Workflow Execution in production.

<RelatedReadContainer>
  <RelatedReadItem page={HowToQueryInGo} />
  <RelatedReadItem page={HowToQueryInJava} />
  <RelatedReadItem page={HowToQueryInPHP} />
</RelatedReadContainer>
