---
title: Use application context with Copilot
description: This article provides guidance about how to use application context with Copilot.
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.search.form:
ms.topic: how-to
ms.date: 02/08/2024
audience: Developer
ms.search.region: Global
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
---

# Use application context with Copilot

[!include [banner](../includes/banner.md)]

Copilot in finance and operations apps lets you create contextual AI experiences that are embedded in the flow of the business process of an application. It's important that the Copilot sidecar chat understands the context that the user is working in.

## Default contextual variables

Some variables are available by default as base components of the **Copilot in Finance and Operation** chatbot. The global variables are automatically set for the user's Copilot session. Therefore, the values are available when plugins are created and extended in Microsoft Copilot Studio.

### Navigation context

The navigation context provides the list of finance and operations navigation menu items that are available to the user in their current client session. The available menu items depend on the user's permissions. The record set is limited to the first 500 records.

**Variable name:** Global.PA\_Copilot\_ServerForm\_NavigationContext<br>
**Type:** Table

**Properties**

| Name | Type | Description |
| --- | --- | --- |
| DisplayName | String | The display name of the application menu item. |
| MenuItem | String | The name of the application menu item. This property can be used for actions such as navigation in the application. |

**Sample payload**

```json
[
  {
    "DisplayName": "All purchase orders",
    "MenuItem": "PurchTableListPage"
  },
  {
    "DisplayName": "All tax fiscal documents",
    "MenuItem": "TaxFiscalDocument_BR"
  },
  {
    "DisplayName": "All vendors",
    "MenuItem": "VendTableListPage"
  },
  {
    "DisplayName": "Allocation journals",
    "MenuItem": "LedgerJournalTable_Allocation"
  },
  {
    "DisplayName": "Approval journal history and matching details",
    "MenuItem": "PurchPostingHistoryInvoiceApproval"
  }
]
```

### Page context

The page context is the page that's open for the user in the current session.

**Variable name:** Global.PA\_Copilot\_ServerForm\_PageContext<br>
**Type:** Record

**Properties**

| Name | Type | Description |
| --- | --- | --- |
| caption | String | The page caption of the current page. |
| metadataName | String | The metadata name of the page. |

**Sample payload**

```json
{
  "caption": "Courses",
  "metadataName": "HRMCourseTable"
}
```

### User context

The user context provides contextual information about the user.

**Variable name:** Global.PA\_Copilot\_ServerForm\_UserContext<br>
**Type:** Record

**Properties**

| Name | Type | Description |
| --- | --- | --- |
| dataAreaId | String | The legal entity that the user is currently signed in to. |
| userLanguageId | String | The language code that's selected for the user in [User options](../get-started/personalize-user-experience.md#system-wide-options-for-the-current-user). |

**Sample payload**

```json
{
  "dataAreaId": "USMF",
  "userLanguageId": "en-us"
}
```
