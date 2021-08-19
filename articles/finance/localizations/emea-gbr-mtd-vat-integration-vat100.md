---
# required metadata

title: Generate VAT declaration in paper format (VAT 100)
description: This topic explains how to generate VAT declaration in paper format (VAT 100) for the United Kingdom (UK).
author: liza-golub
ms.date: 08/19/2021
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

You can generate VAT declaration in paper format (VAT 100) for the United Kingdom (UK) in Dynamics 365 Finance independently from the Electronic Messaging (EM) functionality.

## Prerequisits

Before you start generating the VAT 100 report, make sure that the following settings are provided in your system.

1. Import the following ER configurations:

    | Number | ER configuration name                       | Type                                 | Description |
    |--------|---------------------------------------------|--------------------------------------|-------------|
    | 1      | Tax declaration model                       | Model                                | A generic model for different tax declarations. |
    | 2      | Tax declaration model mapping               | Model mapping                        | A generic model mapping for VAT declarations. |
    | 3      | VAT Declaration Excel (UK)                  | Format (exporting)                   | The **VAT 100** report (a declaration in Microsoft Excel format). |

   Import the latest versions of these configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. The configuration version may contain references to the objects that aren't available in your Finance version. In this case, the importing process of a version of configuration is locked. Import the latest version of the configuration that's available for your Finance version.

    > [!NOTE]
    > After all the ER configurations from the preceding table are imported, set the **Default for model mapping** option to **Yes** for **Tax declaration model mapping**.
    >
    > ![Default for model mapping option.](media/emea-gbr-default-for-model-mapping-parameter.png)

   For more information about how to download ER configurations from the Microsoft global repository, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

2. The setup of the application-specific parameter, **VAT Declaration Excel (UK)** format is completed in Electronic reporting. For more information, see [Set up application-specific parameters for VAT Declaration format](emea-gbr-mtd-vat-integration-setup.md#declaration).
3. To define the **VAT Declaration Excel (UK)** format, go to **Tax** > **Setup** > **General ledger parameters**.
4. On the **Sales tax** tab, in the **Tax options** section, enter the format information in the **VAT statement format mapping** field.

## Generating VAT 100 report

You can generate a paper format of the **VAT 100** report by using the **Report sales tax for settlement period** dialog box.

1. Go to **Tax** > **Declarations** > **Sales tax** > **Report sales tax for settlement period**. 
2. Select the settlement period and in the **From date** field, enter the start date of the reporting period.
4. In the **Sales tax payment version** field, select a version of the VAT statment: 

    - **Original**: Include data of the first sales tax payment record in the period.
    - **Corrections**: Include data of the additional sales tax payment records in the period for corrections.
    - **Latest corrections**: Include data of the corrections that aren't settled in the reporting period.
    - **Total list**: Include data of the first sales tax payment record and additional sales tax payment records for corrections in the reporting period.

5. Select **OK** to start the VAT 100 report generation.
6. Alternatively, you can generate the VAT statement for specific sales tax payment record by going to **Tax** > **Inquiries and reports** > **Sales tax inquiries** > **Sales tax payments**, and on the Action Pane, select **Print report**.
