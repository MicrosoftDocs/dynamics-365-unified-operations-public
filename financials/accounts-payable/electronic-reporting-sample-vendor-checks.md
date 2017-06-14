---
# required metadata

title: Electronic reporting sample vendor checks
description: This topic provides general information about how to use the Electronic reporting sample check formats.
author: twheeloc
manager: AnnBe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
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

You can use Electronic reporting to format vendor checks. Many bank-specific and check provider–specific check formats are available in the market. Sample check formats have been included in the Electronic reporting tool repository in the Payment check model. The sample checks contained in the model are labeled Check in the middle (US) and Check on top stub below (US). 

## What check formats are currently supported?

You should always go to the Shared asset library on Microsoft Dynamics Lifecycle Services (LCS) and view the most up-to-date list of available files that have an asset type of **GER configuration**. The next section, “What do I have to set up?,” includes a link to a topic that explains how to create an LCS repository so that you can review available configurations and import selected configurations.

Microsoft Dynamics 365 for Finance and Operations, Enterprise edition includes a sample format where the check is on top, followed by two remittance sections. It also includes a sample format where the check is in the middle, between two remittance sections. These sample formats correspond to Deluxe business checks formats.

## What do I have to set up?

- Before you can print checks by using Electronic reporting, at least one active check configuration must be imported into your Electronic reporting configurations. For instructions, see [Download Electronic reporting configurations from Lifecycle Services](/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).
- When you configure Cash and bank management checks for the bank account, select the **Generic electronic Export format** check box, and select the appropriate check format as an export format configuration.
- You must also specify the number of slip lines that will be printed on the remittance. Be sure to include the header rows when you calculate this number. The recommended setting for the number of slip lines for the two sample check formats is 17. This will vary based on your check stock and your printer drivers.
- It is recommended that you print a test check to validate the check layout by selecting the Print test option. The sample check formats work best when the advanced printer properties for Microsoft Excel are set up with Margins = None. Once the test check has been generated, enable editing of the Microsoft Excel output to configure the page layout to have all margins set to zero. Compare the test copy of the checks to your check stock and adjust until you are satisfied with the position alignment.
- When you generate payments for the configured bank account in the payment journal, the checks will be printed by using the specified format.

For more information, see [Modify an Electronic reporting format](dev-itpro/analytics/modify-electronic-reporting-format-reapply-excel-template.md)
