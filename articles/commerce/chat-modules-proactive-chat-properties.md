---
# required metadata

title: Commerce chat module proactive chat parameters 
description: This article describes the proactive chat parameters used with Commerce chat modules in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 10/12/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-07-20
---

# Commerce chat module proactive chat parameters

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes the proactive chat parameters used with the Commerce Chat with Omnichannel for Customer Service and Commerce Chat with Power Virtual Agents chat modules in Microsoft Dynamics 365 Commerce.

## Proactive chat properties

The proactive chat properties are located in the properties pane of the Commerce Chat with Omnichannel for Customer Service and Commerce Chat with Power Virtual Agents modules in Commerce site builder.

> [!NOTE] 
> All of the proactive chat properties listed below are empty by default. It is recommended that you learn more about these properties and set them only as needed, which will help reduce any erroneous proactive chats from being triggered.

### Proactive Chat

| Friendly name | Description | Default value |
| ------------- |--------------|--------------|
|  Enabled| Engage customers proactively based on different triggers. |Disabled |
|Chat greeting  |  Greeting message for when a proactive chat has been triggered.| Empty|

### Wait Time (Proactive Chat)

| Friendly name | Description |
| ------------- |--------------|
|  Wait time (sec)|  Time (in seconds) spent on  site apage before a proactive chat is triggered.| 
|  Chat greeting | Greeting message for when a proactive chat has been triggered.  | 

### Number of Page Visits (Proactive Chat)

| Friendly name | Description |
| ------------- |--------------|
|Number of page visits  |  Number of page visits before a proactive chat is triggered. Site users must first accept the prompt on the cookie consent banner.| 
|Chat greeting  | Greeting message for when a proactive chat has been triggered. | 

### Specific Page(s) (Proactive Chat)

| Friendly name | Description |
| ------------- |--------------|
| Page(s) |  List of pages that will trigger a proactive chat when visited.| 
|Chat greeting  |Greeting message for when a proactive chat has been triggered.  | 

### From Specific Page(s) (Proactive Chat)

| Friendly name | Description |
| ------------- |--------------|
|  Page(s)| List of pages that will trigger a proactive chat when users navigates away from them. | 
|Chat greeting  | Greeting message for when a proactive chat has been triggered. | 

### Specific Country/Region (Proactive Chat)

| Friendly name | Description |
| ------------- |--------------|
| Country code | User visiting from specified countries or regions will trigger a proactive chat. Country/region code should be 2-characters and uppercase (for example, US). | 
|  Chat greeting| Greeting message for when a proactive chat has been triggered. | 

### Date Range (Proactive Chat)

| Friendly name | Description |
| ------------- |--------------|
| Start Date (dd/mm/yyyy) |  On or after this date, a proactive chat will be triggered.| 
| End Date (dd/mm/yyyy) | On or before this date, a proactive chat will be triggered. | 
| Chat greeting | Greeting message for when a proactive chat has been triggered. | 

### Total Amount in Cart (Proactive Chat)

| Friendly name | Description |
| ------------- |--------------|
|  Minimum| The minimum monetary amount (inclusive) in the shopping cart that is required to trigger a proactive chat when users visit the cart page. | 
|  Maximum|The maximum monetary amount (inclusive) in the shopping cart that is required to trigger a proactive chat when users visit the cart page.  | 
|Chat greeting  | Greeting message for when proactive chat has been triggered. | 
 
### Total Number of Items in Cart (Proactive Chat)

| Friendly name | Description |
| ------------- |--------------|
|Minimum  | The minimum number of items (inclusive) in the shopping cart required to trigger a proactive chat when users visit the cart page. | 
|Maximum  | The maximum number of items (inclusive) in the shopping cart required to trigger a proactive chat when users visit the cart page. | 
 |Chat greeting  | Greeting message for when a proactive chat has been triggered. | 

### Specific Product(s) in Cart (Proactive Chat)

| Friendly name | Description |
| ------------- |--------------|
| Product(s) ID/SKU | List of product IDs/SKU numbers that will trigger a proactive chat when users visit the cart page. | 
| Chat greeting | Greeting message for when a proactive chat has been triggered. | 

