---
# required metadata

title: Display non-prorated header level charges in e-commerce channels
description: This topic describes a fix for possible issues related to charges flows in Microsoft Dynamics 365 Commerce e-commerce channels.
author: gvrmohanreddy
ms.date: 02/16/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-02-10
---

# Display non-prorated header level charges in e-commerce channels 

[!include [banner](includes/banner.md)]

This topic describes a fix for possible issues related to charges flows in Microsoft Dynamics 365 Commerce e-commerce channels.

In Dynamics 365 Commerce, by default non-prorated header level charges are not applied in e-commerce channel. This may cause one of the following issues in e-commerce channels: 

- Non-prorated header level charges do not appear.
- Charges for delivery modes are notconsistent between the mode of delivery selection and the checkout order summary. 

To see header level non-prorated charges in an e-commerce channel, you must enable the **Enable consistent delivery mode handling in channel** feature.

## Enable the Enable consistent delivery mode handling in channel feature

To enable the **Enable consistent delivery mode handling in channel** feature in Commerce headquarters, follow these steps.

1. Go to the the **Feature management** workspace at **System adminstration \> Workspaces \> Feature management. 
1. in the list of available features, search for and select **Enable consistent delivery mode handling in channel**.
1. In the right pane, select **Enable now**.

> [!NOTE]
> The **Enable consistent delivery mode handling in channel** feature also ensures that sales order delivery information is consistently handled by the same request workflow. 
