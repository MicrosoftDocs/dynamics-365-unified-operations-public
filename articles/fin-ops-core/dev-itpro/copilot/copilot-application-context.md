---
title: Use application context with Copilot
description: Learn about how to use application context with Copilot, including an outline of default contextual variables, navigation context, page context, and user context.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 04/29/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
audience: Developer
ms.search.region: Global
ms.search.form:
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

The page context is the page that's open for the user in the current session, including record information for the record that's currently shown on the page.

**Variable name:** Global.PA\_Copilot\_ServerForm\_PageContext<br>
**Type:** Record

> [!NOTE]
> The fields that provide the current record context are available only in version 10.0.40 and later. These fields include `rootTableName`, `rootTableRecId`, `titleField1Name`, `titleField1Value`, `titleField2Name`, and `titleField2Value`. 

**Properties**

| Name | Type | Description |
| --- | --- | --- |
| caption | String | The page caption of the current page. |
| metadataName | String | The metadata name of the page. |
| rootTableName | String | The name of the root table of the page. | 
| rootTableRecId | Integer | The table record ID of the root table for the record that's currently shown on the page. |
| titleField1Name | String | The name of the first title field at the top of the page. | 
| titleField1Value | String | The value of the first title field at the top of the page, populated with the value for the record that's currently shown on the page. |
| titleField2Name | String | The name of the second title field at the top of the page. |
| titleField2Value | String | The value of the second title field at the top of the page, populated with the value for the record that's currently shown on the page. |

**Sample payload**

```json
{
  "caption":"Vendors",
  "metadataName":"VendTable",
  "rootTableName":"DirPartyTable",
  "rootTableRecId":22565449580,
  "titleField1Name":"PartyNumber",
  "titleField1Value":"1001",
  "titleField2Name":"Name",
  "titleField2Value":"Acme Office Supplies"
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
| userLanguageId | String | The language code selected for the user in [User options](../get-started/personalize-user-experience.md#system-wide-options-for-the-current-user). |

**Sample payload**

```json
{
  "dataAreaId": "USMF",
  "userLanguageId": "en-us"
}
```
