---
id: what-is-a-signal
title: What is a Signal?
description: A Signal is a write-only asynchronous message sent to a running Workflow Execution.
tags:
  - explanation
---

import CenteredImage from '../components/CenteredImage.js'
import {RelatedReadContainer, RelatedReadItem} from '../components/RelatedReadList.js'

<!-- prettier-ignore -->
import * as HowToSignalsInGo from '../go/signals.md'
import * as HowToSignalsInJava from '../java/signals.md'
import * as HowToSignalsInPHP from '../php/signals.md'

A Signal is a write-only asynchronous message sent into a running Workflow Execution and provides data to it.

<CenteredImage
imagePath="/diagrams/signal.svg"
imageSize="75"
title="Signal"
/>

- A Signal is meant to deliver notifications and/or updates to a running Workflow Execution that can change variable values and the state of Workflow Execution.
- Signals can receive data, but cannot return it.
- When a Signal is received by the Temporal Cluster, the Cluster persists the Signal (which includes it payload) as an Event in the Workflow Execution's Event History.
  The Workflow can then handle the Signal at any time afterwards without the risk of losing the information.

<RelatedReadContainer>
  <RelatedReadItem page={HowToSignalsInGo} />
  <RelatedReadItem page={HowToSignalsInJava} />
  <RelatedReadItem page={HowToSignalsInPHP} />
</RelatedReadContainer>
