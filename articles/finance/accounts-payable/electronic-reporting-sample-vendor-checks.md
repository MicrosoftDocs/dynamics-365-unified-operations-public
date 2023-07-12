---
# required metadata

title: Electronic reporting sample vendor checks
description: This article provides general information about how to use the Electronic reporting sample check formats.
author: mrolecki
ms.date: 06/14/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update

---

# Electronic reporting sample vendor checks

[!include [banner](../includes/banner.md)]

You can use Electronic reporting (ER) to format vendor checks. Many bank-specific and check provider–specific check formats are available on the market. Sample check formats have been included in the Payment check model in the ER tool repository. These sample checks are labeled **Check in the middle (US)** and **Check on top stub below (US)**.

## What check formats are currently supported?

You should always go to the Shared asset library in Microsoft Dynamics Lifecycle Services (LCS) and view the current list of available files that have an asset type of **GER configuration**. The next section, “What do I have to set up?,” includes a link to a article that explains how to create an LCS repository so that you can review available configurations and import selected configurations.

Microsoft Dynamics 365 Finance includes a sample format where the check is on top, followed by two remittance sections. It also includes a sample format where the check is in the middle, between two remittance sections. These sample formats correspond to Deluxe business checks formats.

## What do I have to set up?

- Before you can print checks by using ER, at least one active check configuration must be imported into your ER configurations. For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).
- When you configure Cash and bank management checks for the bank account, select the **Generic electronic Export format** checkbox, and then select the appropriate check format as an export format configuration.
- You must also specify the number of slip lines that will be printed on the remittance. Be sure to include the header rows when you calculate this number. For the two sample check formats, the recommended number of slip lines is 17. However, this number will vary, depending on your check stock and your printer drivers.
- We recommend that you print a test check to validate the check layout. To print a test check, select the **Print test** option. The sample check formats work best when **Margins** is set to **None** in the advanced printer properties for Microsoft Excel. After the test check has been generated, enable editing of the Excel output, and configure the page layout so that all margins are set to **0** (zero). Compare the test copy of the checks to your check stock, and adjust the settings until you're satisfied with the alignment.
- When you generate payments for the configured bank account in the payment journal, the checks will be printed by using the specified format.

For more information, see [Modify an Electronic reporting format](../../fin-ops-core/dev-itpro/analytics/modify-electronic-reporting-format-reapply-excel-template.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
