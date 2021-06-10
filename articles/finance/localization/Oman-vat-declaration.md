---
# required metadata

title: VAT declaration for Oman
description: This topic explains how to configure and generate the VAT return form for Oman.
author: sndray
ms.date: 06/10/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:
# ms.tgt_pltfrm: 
# ms.custom: NotInTOC
ms.search.region: Global
# ms.search.industry:
ms.author: tfehr
ms.search.validFrom: 2017-06-20
ms.dyn365.ops.version: 10.0.21
---

#  VAT declaration for Egypt (OM-00003)

[!include[banner](../includes/banner.md)]

[!include[banner](../includes/banner.md)]

This topic explains how to set up and generate the VAT return form and sales and purchase books for legal entities in Oman.

The VAT return form for Oman is the standard document that summarizes the total output VAT tax amount due, the total input VAT tax amount recoverable, and the related VAT tax amount liability. The form is used for all types of taxpayers and should be completed manually through the tax authority portal. The VAT return form is commonly referred to as VAT return filing.

The VAT return form in Dynamics 365 Finance includes the following reports:

- VAT return form which provides a breakdown of amounts, adjustments, and VAT amount per line item in the VAT return form as described in the legislation.
- Sales transactions book
- Purchase transactions book

## Prerequisites
The primary address of the legal entity must be in Egypt.
In the **Feature management** workspace, enable the following feature:

   - Category hierarchy for Sales and purchase tax report.
   - VAT statement format reports.

For more information about how to enable features, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

In the **Electronic reporting** workspace, import the following Electronic reporting format from the repository:

- VAT declaration Excel (OM)

> [!NOTE]
> The format above is based on the **Tax declaration model** and uses the **Tax declaration model mapping**. Additional configurations will be automatically imported.

For more information about how to import Electronic reporting configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Download Electronic reporting configurations

The implementation of the VAT return form for Egypt is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

For production and user acceptance testing (UAT) environments, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

To generate the VAT return form and related reports in an Oman legal entity, upload the following configurations:

- Tax declaration model.version.95.xml.
- Tax declaration model mapping.version.95.159.xml
- VAT Declaration Excel (OM).version.95.8.xml.

After you download the ER configurations from Lifecycle Services (LCS) or the global repository, complete the following steps.

1. Go to the **Electronic reporting** workspace and select the **Reporting configurations** tile.
1. On the **Configurations** page, on the Action Pane, select **Exchange** > **Load from XML file**.
1. Upload the files in the order in which they are listed above. After all the configurations are uploaded, the configuration tree should be present in Finance.

## Set up application-specific parameters

The VAT declaration form includes a set of boxes (lines) which correspond to specific parts of the VAT Return process. Each box should include information about the base, adjustment and VAT amounts. In order to include the requirements established by the form, the user needs to configure each box with the proper information that is coming automatically from sales tax transactions generated from sales , purchase or other operations where VAT tax is posted through the sales tax code configuration.

#### Example

**Line/Box1 - Standard rated sales:**  Per legal definition, this box includes the total amount of standard rated goods and services (excluding collected VAT) sold during the current period in Oman.

In Finance, you can have a specific sales tax code implemented that represents and calculates the operations at a standard sales rate. In this example, it is necessary to configure **Box1** as follows.

The Application-specific parameters option let the users to establish the criteria of how the tax transactions will be collected and calculated in each box (line) of the declaration form when the report is generated depending on the configuration of sales tax code.

1. In the Electronic reporting workspace, select **Configurations** > **Setup** to set up the rules to identify the tax transaction into the related box of the VAT return form.
2. Select the current version. On the **Lookups** FastTab, select the lookup name **ReportFieldLookup**. This lookup identifies the list of boxes (lines) in the VAT form required by tax authority. 
3. On the **Conditions** FastTab, select **Add**, and in the new line in the **Lookup result** column, select the related line of VAT return form.
4. In the **Tax code (Code)** column, select the sales tax code that is used to calculate the related line of VAT return form.
5. In the **Name** column, select the tax transaction classification where the sales tax code is used.
6. Repeat steps 3-5 for all VAT return form boxes (lines) and the combination of sales tax code and tax transaction types configured in your legal entity.
7. Select **Add** again, and then follow these steps to include the final record line:
   a. In the **Lookup result** column, select **NA**.
   b. In the **Tax code (Code)** column, select **Not blank**.
   c. In the **Name column**, select **Not blank**.

By adding this last record (NA), you define the following rule: When the tax code and name that is passed as an argument doesn't satisfy any of the previous rules, the transactions will not be included in the VAT return form. Although this rule is not used when generating the report, the rule does help to avoid errors in report generation when there is a missing rule configuration. 
	
8. In the **State** field, select **Completed**, and then select **Save**. 
9. Close the **Application specific parameters** page.

The following table represent an example of how the user needs to configure these parameters to establish the configuration between the different boxes in the declaration form and sales tax code configuration implemented in Finance.






## Set up General ledger parameters

To generate the VAT return form report in Microsoft Excel format, define an ER format on the **General ledger parameters** page.

1. Go to **Tax** > **Setup** > **General ledger parameters**.
2. On the **Sales tax** tab, in the **Tax options** section, in the **VAT statement format mapping** field, select **VAT Declaration Excel (OM)**. If you leave the field blank, the standard sales tax report will be generated in SSRS format.
3. Select the **Category hierarchy**. This category enables the commodity code in Foreign trade tab transactions to allow users to select and classify goods and services. The description of this classification is detailed in sales and purchase transaction reports. This configuration is optional.



## Generate a VAT return report
The process to prepare and submit a VAT return report for a period is based on sales tax payment transactions that were posted during the Settle and post sales tax job. For more information about sales tax settlement and reporting, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md).

Complete the following steps to generate the tax declaration report.

Go to **Tax > Declarations** > **Sales tax** > **Report sales tax for settlement period** or **Settle and post sales tax**.
2. Select the **Settlement period**.
3. Select the from date.
4. Select the sales tax payment version.
5. Select **OK** to confirm the above steps. 
6. Enter the amount of credit from the previous period, if applicable, or leave the amount as zero.
7. In the **Generate details** field, select one of the following available options. The VAT return form is always generated in this process.
   - **All** - Generate sales and purchase tax transactions details reports.
   - **None** - Generate only the VAT declaration return form.
   - **Purchase transactions**
   - **Sales transactions**

8. Select **OK** to complete the process.


 
