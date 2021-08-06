---
# required metadata

title: Generate VAT declaration in paper format (VAT 100)
description: This topic explains how to generate VAT declaration in paper format (VAT 100) for the United Kingdom (UK)
author: liza-golub
ms.date: 08/06/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: United Kingdom
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 08/06/2021

---

# Generate VAT declaration in paper format (VAT 100)

[!include [banner](../includes/banner.md)]

This topic explains how to generate VAT declaration in paper format (VAT 100) for the United Kingdom (UK).

You can generate VAT declaration in paper format (VAT 100) for the United Kingdom (UK) in Dynamics 365 Finance independently from Electronic Messaging (EM) functionality.

## Prerequisits

Before you start generating VAT 100 report, make sure that the following settings are provided in your system.

1. Import the following ER configurations:

| Number | ER configuration name                       | Type                                 | Description |
|--------|---------------------------------------------|--------------------------------------|-------------|
| **1**  | **Tax declaration model**                   | **Model**                            | **A generic model for different tax declarations.** |
| 2      | Tax declaration model mapping               | Model mapping                        | A generic model mapping for VAT declarations. |
| 3      | VAT Declaration Excel (UK)                  | Format (exporting)                   | The **VAT 100** report (a declaration in Microsoft Excel format). |

Import the latest versions of these configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article 
that explains the changes that were introduced in the configuration version. Configuration version may contain references to the objects that are not available in your Finance version, 
in this case importing process of such version of configuration will be locked. Import the latest version of the configuration that is available for your Finance version.

> [!NOTE]
> After all the ER configurations from the preceding table are imported, set the **Default for model mapping** option to **Yes** for **Tax declaration model mapping**.
>
> ![Default for model mapping option.](media/emea-gbr-default-for-model-mapping-parameter.png)

For more information about how to download ER configurations from the Microsoft global repository, see [Download ER configurations from the Global repository](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo).

2. Setup of application-specific parameter of **VAT Declaration Excel (UK)** format is done and completed in Electronic reporting. Find more details in [Set up application-specific parameters for VAT Declaration format](emea-gbr-mtd-vat-integration-setup.md#declaration) section of this topic.
3. **VAT Declaration Excel (UK)** format is defined in **VAT statement format mapping** field of **Tax options** section on the **Sales tax** tab of the **Tax** > **Setup** > **General ledger parameters** page.

## Generating VAT 100 report

You can generate a paper format of the **VAT 100** report by using the **Report sales tax for settlement period** dialog box.

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period**. 
2. Specify 

Alternatively, you can generate the statement for a selected sales tax payment transaction from the **Sales tax payments** page (**Tax** \> **Inquiries and reports** \> **Sales tax inquiries** \> **Sales tax payments**). 
 
