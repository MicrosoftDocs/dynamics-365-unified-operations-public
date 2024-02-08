---
title: Using application context with Copilot
description: This article provides guidance on how to use application context with Copilot.
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

# Using application context with Copilot

[!include [banner](../includes/banner.md)]

Copilot in finance and operations apps lets you create contextual AI experiences embedded in the flow of the business process of the application. It's important that the Copilot sidecar chat understands the context in which the user is working.

## Default contextual variables
Some variables are available by default as base components of the Copilot in the finance and operation chatbot. The global variables are set automatically for the user's Copilot session, making the values available when creating and extending plugins in Copilot Studio.

### Navigation context
The navigation context provides the list of the finance and operations navigation menu items available to the user in the user's current client session. The available menu items are dependent on the user's permissions. The record set is limited to the first 500 records.

**Variable name**: Global.PA_Copilot_ServerForm_NavigationContext<br>
**Type**: Table

**Properties**

| Name | Type | Description| 
| --- | --- | --- |
| DisplayName | String | The display name of the application menu item. |
| MenuItem | String | The name of the application menu item. This property can be used for actions like navigation in the application. |

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
The page context is the page open for the user in the current session.

**Variable name**: Global.PA_Copilot_ServerForm_PageContext<br>
**Type**: Record

**Properties**

| Name | Type | Description| 
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
This provides contextual information about the user.

**Variable name**: Global.PA_Copilot_ServerForm_UserContext<br>
**Type**: Record

**Properties**

| Name | Type | Description| 
| --- | --- | --- |
| dataAreaId | String | The legal entity the user is currently signed into.  |
| userLanguageId | String | The language code selected for the user in [User options](../get-started/personalize-user-experience.md#system-wide-options-for-the-current-user).  |

**Sample payload**
```json
{
  "dataAreaId": "USMF",
  "userLanguageId": "en-us"
}
```
