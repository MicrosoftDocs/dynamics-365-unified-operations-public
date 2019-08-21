---
# required metadata

title: Delete personal information
description: This topic discusses the references available to handle a data subject request per General Data Protection Regulation (GDPR) standards for Dynamics 365 e-Commerce.
author: brshoo
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

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

# Delete personal information

This topic discusses the references available to handle a data subject rights request per General Data Protection Regulation (GDPR) standards for Dynamics 365 Commerce. To best understand this topic, please review the [Dynamics 365 for Finance and Operations GDPR Guide](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide). 

## Overview

Users of Dynamics 365 Commerce own and control the data that power a published e-Commerce website. Dynamics 365 Commerce is built to act as a data processor for all out-of-the-box default e-Commerce features. This enables the site data controller to process GDPR requests when submitted. The following guidelines cover handling GDPR data subject rights (DSR) requests in Dynamics 365 Commerce (where customizations have not been made).

## Respond to your customer DSR requests

By default, Dynamics 365 Commerce functionality uses internal data inventory and tagging for all telemetry and system data to classify customer data in accordance with GDPR. This allows the data controller to use the Dynamics 365 for Finance and Operations [Person Report](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide#the-person-search-report) to respond to user DSR requests when received.

[!Important] Review the considerations noted throughout the [GDPR Guide](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide). Additional actions may be needed if customizations have been made to the e-Commerce instance, the retail server instance, or to any operating practices that may upload content or data into Dynamics 365 Commerce.

## Respond to your employee DSR requests

In addition to the Dynamics 365 for Finance and Operations [Person Report](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide#the-person-search-report) functionality, Dynamics 365 Commerce also stores personal information in the form of the history logs for authoring actions. These actions include Checkout or Check In, Publish, Save, or similar actions. The user's alias will be shown for each history action item logged.  

In Dynamics 365 Commerce, when a content item is selected (page, template, video, etc.), users can select the Show History icon in the actions menu above the item.

#### Pull records for a DSR request

To pull a list or remove all of the references to the DSR user's username in Dynamics 365 Commerce history logs, do the following. 

1. Go to the Main Menu and select **GDPR**. 
1. Enter the username to be searched.
1. If removing references to the username, enter the replacement string to be used to anonymize the username.
1. Select the **Run Tool** action

A list of all found instances can be saved once the operation is completed.

