---
# required metadata

title: Commerce chat module proactive chat parameters
description: This article describes the proactive chat parameters of Commerce chat modules in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 07/26/2024
ms.topic: how-to
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2022-07-20
ms.custom: 
  - bap-template
---

# Commerce chat module proactive chat parameters

[!include [banner](../includes/banner.md)]

This article describes the proactive chat parameters of the Commerce Chat with Omnichannel for Customer Service and Commerce Chat with Power Virtual Agents chat modules in Microsoft Dynamics 365 Commerce.

## Proactive chat properties

The proactive chat properties are located in the properties pane of the Commerce Chat with Omnichannel for Customer Service and Commerce Chat with Power Virtual Agents modules in Commerce site builder.

> [!NOTE]
> By default, all the proactive chat properties that are listed here are blank. We recommend that you learn more about these properties and set them only as they are required. This approach will help reduce erroneous proactive chats from being triggered.

### Proactive Chat

| Friendly name | Description | Default value |
|---------------|-------------|---------------|
| Enabled | Proactively engage customers, based on different triggers. | Disabled |
| Chat greeting | The greeting message that is used when a proactive chat has been triggered. | Blank |

### Wait Time (Proactive Chat)

| Friendly name | Description |
|---------------|-------------|
| Wait time (sec) | The time (in seconds) that site users spend on a site page before a proactive chat is triggered. |
| Chat greeting | The greeting message that is used when a proactive chat has been triggered. |

### Number of Page Visits (Proactive Chat)

| Friendly name | Description |
|---------------|-------------|
| Number of page visits | The number of page visits before a proactive chat is triggered. Site users must first accept the prompt in the cookie consent banner. |
| Chat greeting | The greeting message that is used when a proactive chat has been triggered. |

### Specific Page(s) (Proactive Chat)

| Friendly name | Description |
|---------------|-------------|
| Page(s) | A list of the pages that will trigger a proactive chat when they are visited. |
| Chat greeting | The greeting message that is used when a proactive chat has been triggered. |

### From Specific Page(s) (Proactive Chat)

| Friendly name | Description |
|---------------|-------------|
| Page(s) | A list of the pages that will trigger a proactive chat when users navigate away from them. |
| Chat greeting | The greeting message that is used when a proactive chat has been triggered. |

### Specific Country/Region (Proactive Chat)

| Friendly name | Description |
|---------------|-------------|
| Country code | Users who visit from specified countries or regions will trigger a proactive chat. Country/region codes should be two uppercase letters (for example, **US**). |
| Chat greeting | The greeting message that is used when a proactive chat has been triggered. |

### Date Range (Proactive Chat)

| Friendly name | Description |
|---------------|-------------|
| Start Date (dd/mm/yyyy) | The date on or after which a proactive chat will be triggered. |
| End Date (dd/mm/yyyy) | The date on or before which a proactive chat will be triggered. |
| Chat greeting | The greeting message that is used when a proactive chat has been triggered. |

### Total Amount in Cart (Proactive Chat)

| Friendly name | Description |
|---------------|-------------|
| Minimum | The minimum monetary amount (inclusive) in the shopping cart that will trigger a proactive chat when users visit the cart page. |
| Maximum | The maximum monetary amount (inclusive) in the shopping cart that will trigger a proactive chat when users visit the cart page. |
|Chat greeting | The greeting message that is used when a proactive chat has been triggered. |

### Total Number of Items in Cart (Proactive Chat)

| Friendly name | Description |
|---------------|-------------|
| Minimum | The minimum number of items (inclusive) in the shopping cart that will trigger a proactive chat when users visit the cart page. |
| Maximum | The maximum number of items (inclusive) in the shopping cart that will trigger a proactive chat when users visit the cart page. |
| Chat greeting | The greeting message that is used when a proactive chat has been triggered. |

### Specific Product(s) in Cart (Proactive Chat)

| Friendly name | Description |
|---------------|-------------|
| Product(s) ID/SKU | A list of the product IDs/stock keeping unit (SKU) numbers that will trigger a proactive chat when users visit the cart page. |
| Chat greeting | The greeting message that is used when a proactive chat has been triggered. |

## Additional resources

[Commerce chat features overview](commerce-chat-overview.md)

[Commerce Chat with Omnichannel for Customer Service module](commerce-chat-module.md)

[Commerce Chat with Power Virtual Agents module](chat-module-pva.md)
