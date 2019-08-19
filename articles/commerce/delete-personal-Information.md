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

# Delete personal information

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic discusses the references available to handle a data subject rights request per General Data Protection Regulation (GDPR) standards for Dynamics 365 e-Commerce. To best understand the information below, please review the [Dynamics 365 for Finance and Operations GDPR Guide](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide). 



## Overview

Users of Dynamics 365 e-Commerce own and control the data that makes up and operates a site as published. The e-Commerce system is built to act as a Data processor for all out of the box default e-Commerce features. This enables you, the e-Commerce user as Data controller, to process GDPR requests when encountered. The following guidelines can be referenced for handling GDPR Data Subject requests in e-Commerce (where e-Commerce customizations have not been made).



## Responding to your customer data subject rights (DSR) requests

By default, e-Commerce functionality utilizes an internal data inventory and tagging for all telemetry and system data to classify the data in accordance with GDPR. This allows the data controller to use the Dynamics 365 for Finance and Operations [Person Report](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide#the-person-search-report) to respond when a user DSR request is received.

[!Important] Review the considerations noted throughout the [GDPR Guide](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide). Additional actions may be needed dependent upon any customizations made to the e-Commerce instance, Retail Server Instance, or any operating practices enabled that may upload content or data into e-Commerce.



## Responding to your employee DSR requests

In addition to the [Person Report](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide#the-person-search-report) functionality, e-Commerce Tooling also stores personal information in the form of the History Logs for authoring actions in e-Commerce Tooling.  This applies to actions such as page Checkout or Check In, Publish, Save, or similar actions. The user's alias will be shown per row for each history action item logged.  

In e-Commerce, when a Content Item is selected (Page, Template, Video, etc.), users can select the Show History icon in the actions menu above the item.

#### To pull records from e-Commerce tooling for a DSR request

Go to the Main Menu and select GDPR. Follow the steps to pull a list or remove all of the references of the DSR user's Username in e-Commerce history logs:

- Enter the Username to be searched
- If Removing, enter the Replacement String to be used to anonymize the Username
- Select the Run Tool action

A list of all found instances can be saved from the e-Commerce Tooling instance once the run is complete.

