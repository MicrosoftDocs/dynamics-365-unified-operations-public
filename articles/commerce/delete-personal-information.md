---
# required metadata

title: Delete personal information
description: This topic discusses the guidelines that are available to handle data subject requests per General Data Protection Regulation (GDPR) standards in Microsoft Dynamics 365 e-Commerce.
author: v-chgri
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Delete personal information

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic discusses the guidelines that are available to handle data subject rights (DSR) requests per General Data Protection Regulation (GDPR) standards in Microsoft Dynamics 365 e-Commerce. To better understand this topic, see the [General Data Protection Regulation overview](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide) topic for Dynamics 365 for Finance and Operations.

## Overview

Users of Dynamics 365 Commerce own and control the data that powers a published e-Commerce website. Dynamics 365 Commerce is built to act as a data processor for all default, out-of-box e-Commerce features. Therefore, the site data controller can process any GDPR DSR requests that are submitted. The following guidelines cover the handling of GDPR DSR requests in Dynamics 365 Commerce. These guidelines apply only in cases where customizations haven't been made.

> [!IMPORTANT]
> Review the considerations that are noted throughout [General Data Protection Regulation overview](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide). Additional actions might be required if customizations have been made to the e-Commerce instance, the Retail Server instance, or any operating practices that can upload content or data into Dynamics 365 Commerce.

## Respond to customer DSR requests

By default, Dynamics 365 Commerce functionality uses internal data inventory and tagging for all telemetry and system data, to classify customer data in accordance with GDPR. Therefore, the data controller can use the Finance and Operations [Person search report](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide#the-person-search-report) to respond to DSR requests that are received from customers.

## Respond to employee DSR requests

In addition to using the functionality of the Finance and Operations [Person search report](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide#the-person-search-report), Dynamics 365 Commerce stores personal information in the form of the history logs for authoring actions. These actions include Checkout and Check In, Publish, and Save. For each action item that is logged in history, the user's alias is shown.

In Dynamics 365 Commerce, when a content item (for example, a page, template, or video) is selected, users can select the **Show History** button in the menu above the item.

### Pull records for a DSR request

To pull a list of all references to the DSR user's user name in Dynamics 365 Commerce history logs, or to remove all references to the user name, follow these steps.

1. Go to **GDPR**, and enter the user name to search for.
1. If you're removing references to the user name, enter the replacement string that should be used to anonymize the user name.
1. Select **Run Tool**.

After the operation is completed, you can save the list of all references that were found.
