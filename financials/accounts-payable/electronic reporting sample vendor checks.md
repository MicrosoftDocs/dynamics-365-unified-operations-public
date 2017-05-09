---
# required metadata

title: Electronic reporting sample vendor checks
description: This article provides general information using the electronic reporting sample check formats.
author: twheeloc
manager: AnnBe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc 
# ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: twheeloc
ms.dyn365.intro: 2017/06/01
ms.dyn365.version:

---

[!include[banner](../includes/banner.md)]

# Electronic reporting sample check formats

Electronic reporting can be used to format vendor checks. There are many bank specific or check provider specific check formats available in the market. Sample check formats have been included in the Electronic reporting tool repository.

## What check formats are currently supported?

You should always go to the Shared asset library on Microsoft Dynamics Lifecycle services (LCS) and view the most up-to-date list of available files that have an asset type of GER configuration. The next section, “What do I have to set up?”, provides a link to the topic that explains how to create an LCS repository to review available configurations and import selected configurations.

Dynamics 365 for Operations includes a sample format where the check is on top, followed by two remittance sections and a sample format where the check is in the middle, in between two remittance sections. These sample formats correspond to Deluxe business checks formats.

## What do I have to set up?

 - Before you can print checks using electronic reporting, at least one active check configuration must be imported into your ER configurations. For instructions, see [Download Electronic reporting configurations from Lifecycle Services](/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).
 - When you configure Cash and Bank management checks for the bank account, select the Generic electronic Export format check box, and select the appropriate check format as an export format configuration.
 - You must also specify the number of slip lines that will print on your remittance. Be sure to include the header rows when you calculate this number.
 - When you generate payments for the configured bank account in the payment journal, the checks will be printed using the specified format.
