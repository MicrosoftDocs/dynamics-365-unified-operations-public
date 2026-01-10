---
title: Agent Feed developer documentation (preview)
description: This article describes how to use Agent Feed in Dynamics 365 Finance and Operations (FnO) to create, update, read, and customize feed items surfaced in Immersive Home.
author: cabeln
ms.author: cabeln
ms.topic: how-to
ms.date: 01/09/2026
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Agent Feed developer documentation

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The guidance applies to FnO version 10.0.47, available in public preview by January 26, 2026. 

This article describes how to use Agent Feed in Dynamics 365 Finance and Operations (FnO) to create, update, read, and customize feed items surfaced in Immersive Home.
Agent Feed enables ERP agents to post actionable feed items through Dataverse Custom APIs, store them natively in FnO, and render them as cards that respect security, ranking, and personalization.

## Overview

Agent Feed provides a platform capability that allows agents and applications to surface contextual work items to users in Immersive Home. Feed items are created by agents, ranked using AI-assisted logic, secured using FnO menu items, and rendered through configurable card providers.

## How to use Agent Feed

### Enable FnO features

In Finance and Operations Feature management, enable the following:

- Immersive Home
- (Preview) Agent Feed for Immersive Home
- (Preview) Custom API Generation

These features are required for both feed rendering and agent‑driven integration.

### Use Custom APIs to create and update feed items

Feed items are created and maintained via Dataverse Custom APIs, delivered as part of the Copilot for finance and operations solution (version 1.0.03291.1 or later).

Supported APIs:

- msdyn_AgentFeedCreateFeedItemCustomApi
- msdyn_AgentFeedUpdateFeedItemCustomApi

These APIs write and update feed data into FnO tables through an orchestrated X++ implementation that maintains transactional integrity across related Agent Feed tables.

## Custom API documentation

### Create feed item

#### Endpoint

POST {organizationUrl}/api/data/v9.2/msdyn_CreateAgentFeedItemCustomApi

Parameters in the namespace **msdyn_AgentFeedCreateFeedItemCustomApi_...** (see below)

#### Required parameters

| Parameter        | Type     | Description                                              | Example                  |
| ---------------- | -------- | -------------------------------------------------------- | -------------------------|
| **title**        | String   | Primary card title shown to users. It should be short, human-readable headline displayed as the primary card title.| “Supplier Invoice Overdue” |
| **subtitle**     | String   | Secondary contextual line, providing immediate context to the title (phase, action, or focus)	| “Invoice PD 1042 is past due by 5 days.” |
| **correlationid**| String   | GUID for idempotency and tracing across systems          |“7c2a4f64 8d3b 4b8d 9c11 1af33bb234d7”|
| **summary**      | String   | Summary is a concise description of the business situation or task the agent will assist with. Plain text; aim for one or two sentences.|                               |
| **status**       | String   | Status is the current lifecycle state of the feed item.  |Allowed values: not started, in progress, completed, canceled|
| **permissionscheck**| String   | a comma-separated list of MenuItems used to drive security checks for the feed item and determine if action controls are rendered.|“PURCHTABLE,VENDTABLE,IMMERSIVEHOME”|
| **cardprovider** | Text     | Card Provider is the identifier of the UI/component provider that renders the interactive card. Must match a registered provider name.|“DefaultAgentFeedCardProvider”|
| **aicontext**    | JSON     | JSON string with required keys TaskType, AgentSchema, RecordType, Priority, Category. Optional: BusinessImpact, SourceApp, WorkspaceLink. Must be valid JSON and provide user/app context.|{"TaskType":"Approval","AgentSchema":"msdyn_expenseagent","RecordType":"VendInvoice","Priority":"High","Category":"Procurement","BusinessImpact":"Avoid late fees","SourceApp":"FinanceAndOperations","WorkspaceLink":"https://contoso.com/workspace/123"}|

#### Optional parameters

| Parameter        | Type     | Description                                              | Example                  |
| ---------------- | -------- | -------------------------------------------------------- | ------------------------ |
| **duedate**      | DateTime | Target completion date/time for the task. ISO 8601 format: YYYY-MM-DD or YYYY-MM-DDThh:mm:ssZ. Leave blank if not time-bound. | “2026-01-12” |
| **fnorecord**    | String   | The FNO Record Reference is a JSON array string linking this feed item to Finance and Operations entities. Each object: {"RefRecId":<long>,"RefTableId":"<table>"}. Improves contextual navigation. | [{"RefRecId":5637144576,"RefTableId":"VendInvoiceTable"},{"RefRecId":5637144588,"RefTableId":"PurchTable"}] |

#### Example parameter payload

```json
{
  "msdyn_AgentFeedCreateFeedItemCustomApi_title": "Quarterly Budget Review",
  "msdyn_AgentFeedCreateFeedItemCustomApi_subtitle": "Review and finalize budget allocations",
  "msdyn_AgentFeedCreateFeedItemCustomApi_correlationid": "42d72a99-9786-4c28-8ab5-66a1451d27a5",
  "msdyn_AgentFeedCreateFeedItemCustomApi_summary": "Submitted expense reports require auditing for accuracy and compliance with company policy.",
  "msdyn_AgentFeedCreateFeedItemCustomApi_status": "Active",
  "msdyn_AgentFeedCreateFeedItemCustomApi_permissionscheck": "VENDTABLE, PURCHTABLE",
  "msdyn_AgentFeedCreateFeedItemCustomApi_cardprovider": "DefaultAgentFeedCardProvider",
  "msdyn_AgentFeedCreateFeedItemCustomApi_duedate": "2025-12-31",
  "msdyn_AgentFeedCreateFeedItemCustomApi_aicontext": "{\"TaskType\": \"Expense Validation\", \"AgentSchema\": \"msdyn_expenseagent\", \"RecordType\": \"Purchase Order\", \"Priority\": \"High\", \"Category\": \"Procurement\", \"BusinessImpact\": \"Payment Blocked\", \"User\": \"jane.smith@microsoft.com\", \"LastViewed\": \"2025-09-17T20:57:52Z\", \"SourceApp\": \"Excel\", \"WorkspaceLink\": \"aka.ms/workspace1\"}",
  "msdyn_AgentFeedCreateFeedItemCustomApi_fnorecord": "[{\"RefRecId\":5637150639,\"RefTableId\":\"CustInvoiceJour\"},{\"RefRecId\":5637150642,\"RefTableId\":\"CustInvoiceJour\"}]"
}
```

#### Output

| Parameter        | Type     | Description                                              | Example                  |
| ---------------- | -------- | -------------------------------------------------------- | ------------------------ |
| **feeditemrecid**| RecId / Decimal | Identifier for feed item                          | 1342198406               |
| **correlationid**| String   | GUID for idempotency and tracing across systems          |"42d72a99-9786-4c28-8ab5-66a1451d27a5"|

#### Example Output Payload

```json
{
"msdyn_AgentFeedCreateFeedItemCustomApi_feeditemrecid": 1342198406,
"msdyn_AgentFeedCreateFeedItemCustomApi_correlationid": "42d72a99-9786-4c28-8ab5-66a1451d27a5"
}
```
