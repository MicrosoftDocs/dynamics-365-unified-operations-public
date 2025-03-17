---
title: Get started with Tax Calculation
description: Learn how to set up Tax Calculation, including outlines on high-level design, prerequisites, and configuring the Tax Calculation feature.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 02/09/2024
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Application user
ms.search.region: Global
ms.search.validFrom: 2021-04-01
ms.search.form: TaxIntegrationTaxServiceParameters
ms.dyn365.ops.version: 10.0.18
---


# Get started with Tax Calculation

[!include [banner](../../includes/banner.md)]

This article provides information about how to get started with Tax Calculation. The sections in this article guide you through the high-level design and configuration steps in Dynamics 365 Finance and Dynamics 365 Supply Chain Management. 

## High-level design

### <a name="runtime"></a> Runtime design

The following illustration shows the high-level runtime design of Tax Calculation.

1. A transaction, such as a sales order or purchase order, is created in Finance.
2. Finance automatically uses the default values of the sales tax group and the item sales tax group.
3. When the **Sales tax** button is selected on the transaction, the tax calculation is triggered. Finance then sends the transaction information to Tax Calculation.
4. Tax Calculation matches the transaction information with predefined rules in the tax feature to find a more accurate sales tax group and item sales tax group simultaneously.

    - If the transaction information can be matched with the **Tax Group Applicability** matrix, it overrides the sales tax group value with the matched tax group value in the applicability rule. Otherwise, it continues to use the sales tax group value from the transaction information.
    - If the transaction information can be matched with the **Item Tax Group Applicability** matrix, it overrides the item sales tax group value with the matched item tax group value in the applicability rule. Otherwise, it continues to use the item sales tax group value from the transaction information.

5. Tax Calculation determines the final tax codes by using the intersection of the sales tax group and the item sales tax group.
6. Tax Calculation calculates tax, based on the final tax codes that it determined.
7. Tax Calculation returns the tax calculation result. The **Sales tax** page shows the tax calculation result.

![Tax Calculation runtime design.](../media/tax-calculation-runtime-logic.png)

### High-level configuration

The following steps provide a high-level overview of the configuration process for Tax Calculation.

1. In the **Globalization Studio** workspace, click the **Tax calculation** tile, and create the **Tax Calculation** feature. 
2. Set up the **Tax Calculation** feature:

    1. Select the tax configuration version.
    2. Create tax codes.
    3. Create a tax group.
    4. Create an item tax group.
    5. Optional: Create tax group applicability if you want to override the default sales tax group that is entered from customer or vendor master data.
    6. Optional: Create item group applicability if you want to override the default item sales tax group that is entered from the item master data.

3. Complete the **Tax Calculation** feature.
4. In the **Tax calculation parameters**, select the **Tax Calculation** feature.

After you complete these steps, the following setups are automatically synced from the Tax feature setup to Finance:

- Sales tax codes
- Sales tax groups
- Item sales tax groups

The remaining sections in this article provide more detailed configuration steps.

## Configure the Tax Calculation feature

The steps in this section aren't related to a specific legal entity. You must complete this procedure only one time. You can complete it in any legal entity in [Globalization Studio workspace in Finance](./workspace/gsw-features.md) (if you're using version 10.0.39 or later).

1. Import the correct [tax configuration version](global-tax-calcuation-service-overview.md#versions), based on your Finance version. Follow the steps in [Import Electronic reporting (ER) configurations from Dataverse](./workspace/gsw-import-er-config-dataverse.md).
2. Open the **Globalization Studio** workspace, select the **Tax Calculation** tile. On the **Tax calculation features** page, select the **Add** button, and select one of the following feature types:

    - **New feature** – Create a feature setup that has blank content.
    - **Based on existing feature** – Create a feature from an existing feature, and copy the content from the existing feature setup.

    > [!NOTE]
    > You can import a demo feature for the **DEMF** demo legal entity. For more information, see [Import feature demo data](tax-calculation-import-export-feature.md).

4. Enter a name and description for the feature, and then select **Create feature**.

    After the feature is created, a draft version of it is automatically created. You can select **Get this version** to rebase the draft version on any completed version.

5. Select the draft version of the feature, and then select **Edit**. The **Tax Calculation setup** page is filled in.
6. Select **Configuration version**. You should see the configuration version that you imported.

    Microsoft provides a default tax configuration for tax calculation. This configuration covers most of the requirements for tax calculation behaviors. It will be updated based on market feedback. If you must extend the configuration to meet specific requirements, see [How to build extension in tax service](tax-service-add-data-fields-tax-integration-by-extension.md) for information about how to generate and select your own tax configuration.

7. After you select **Configuration version**, several additional tabs appear. Follow the order that is shown here to complete the mandatory tab setup.

    **Mandatory setup**

    - **Tax codes** – Maintain master data for tax codes. All tax codes that are created on this tab are automatically synchronized to Finance when you enable the current version.
    - **Tax group** – Define the tax group master data and the tax codes under the group.
    - **Item tax group** – Define the item tax group master data and the tax codes under the group.

    **Optional setup**

    - **Tax group applicability** – Define a matrix that determines the tax group. If no applicability rules in this matrix match the taxable document from Dynamics 365, Tax Calculation uses the default value on the taxable document line.
    - **Item tax group applicability** – Define a matrix that determines the item tax group. If no applicability rules in this matrix match the taxable document from Dynamics 365, Tax Calculation uses the default value on the taxable document line.
    - **Customer tax registration number applicability** – If you have multiple tax registration numbers for one customer, Tax Calculation can automatically determine the correct tax registration number. In the matrix on this tab, define the rules that should be used to make the determination. Otherwise, Finance and Supply Chain Management will continue to use the default tax registration number on taxable documents for sales transactions.
    - **Vendor tax registration number applicability** – If you have multiple tax registration numbers for one vendor, Tax Calculation can automatically determine the correct tax registration number. In the matrix on this tab, define the rules that should be used to make the determination. Otherwise, Finance and Supply Chain Management will continue to use the default tax registration number on taxable documents for purchase transactions.
    - **List code applicability** – Automatically determine the value of the **List code** field through more flexible and configurable rules. In the matrix on this tab, define the rules that should be used to make the determination. Otherwise, Finance and Supply Chain Management will continue to use the default code on taxable documents.

8. On the **Tax codes** tab, select **Add**, and enter the tax code and a description.
9. Select **Calculation origin**. The calculation origin defines how the tax base amount and the tax amount are calculated. The following values are available:

    - By net amount
    - By gross amount
    - By quantity
    - By margin
    - Tax on tax

10. Select **Save**. More fields become available, based on the **Calculation origin** that you selected.
11. Use the following options to identify the nature of the tax code:

    - Is exempt
    - Is use tax
    - Is reverse charge
    - Exclude from base amount calculation

    For a use tax scenario, set up a single tax code that has a positive tax rate, and mark it as **Is use tax**.

    For a reverse charge scenario, set up two tax codes, one of which has a positive tax rate, and the other of which has a negative tax rate but the same rate value. Mark the negative tax code as **Is reverse charge**. For more information about the reverse charge solution in Finance, see [Reverse charge mechanism for VAT/GST scheme](emea-reverse-charge.md).

    For some tax types that should be excluded from the calculation of the tax base amount for price-inclusive transactions (for example, custom duty in some countries or regions), select the **Exclude from Base Amount Calculation** checkbox. For more information about this parameter, see [Calculating tax on top of price when Prices include taxes is enabled](global-exclude-from-tax-base-amount-calculation.md).

    Maintain tax rates and the tax amount limits for this tax code.

12. Repeat steps 8 through 11 to add all other tax codes that are required.
13. On the **Tax group** tab, select the **Tax group** column, add it to the matrix as the input condition, and then add lines to maintain the tax group master data.

    Here is an example.

    | Tax group    | Tax codes           |
    | ------------ | ------------------- |
    | DEU_Dom | DEU_VAT19; DEU_VAT7 |
    | DEU_EU       | DEU_Exempt          |
    | BEL_Dom | BEL_VAT21; BEL_VAT6 |
    | BEL_EU       | BEL_Exempt          |

14. On the **Item tax group** tab, select **Item tax group** column, add it to the matrix as the input condition, and then add lines to maintain the item tax group master data.

    Here is an example.

    | Item tax group | Tax codes                                    |
    | -------------- | -------------------------------------------- |
    | Full           | DEU_VAT19; BEL_VAT21; DEU_Exempt; BEL_Exempt |
    | Reduced        | DEU_VAT7; BEL_VAT6; DEU_Exempt; BEL_Exempt   |

15. On the **Tax group applicability** tab, select the columns that are required to determine the correct tax group, and then select **Add**. Enter or select values for each column. The **Tax group** field will be the output of this matrix. If this tab isn't configured, the sales tax group on the transaction line will be used.

    Here is an example.

    | Business process | Ship from | Ship to | Tax group    |
    | ---------------- | --------- | ------- | ------------ |
    | Sales            | DEU       | DEU     | DEU_Dom |
    | Sales            | DEU       | FRA     | DEU_EU       |
    | Sales            | BEL       | BEL     | BEL_Dom |
    | Sales            | BEL       | FRA     | BEL_EU       |
    
    > [!NOTE]
    > If the default sales tax group on your taxable document lines is correct, leave this matrix blank. For more information, see the [Runtime design](#runtime) section in this article.

16. On the **Item tax group applicability** tab, select the columns that are required to determine the correct tax code, and then select **Add**. Enter or select values for each column. The **Item tax group** field will be the output of this matrix. If this tab isn't configured, the item sales tax group on the transaction line will be used.

    Here is an example.

    | Item code | Item tax group |
    | --------- | -------------- |
    | D0001     | Full           |
    | D0003     | Reduced        |

    > [!NOTE]
    > If the default item sales tax group on your taxable document lines is correct, leave this matrix blank. For more information, see the [Runtime design](#runtime) section in this article.

    For more information about how tax codes are determined in Tax Calculation, see [Sales tax group and item sales tax group determination logic](global-sales-tax-group-determination.md).

17. Set up the applicability of customer tax registration numbers, vendor tax registration numbers, and list codes, based on the business needs.
18. Select **Save**, and then close the page.
19. Select **Change status** \> **Complete**. After the status is changed to **Complete**, the version can no longer be edited. This version of the tax feature setup will be visible to each legal entity on **Tax calculation parameters** page.

## Set up Tax Calculation in Globalizaton studio Workspace

After you complete the setup in the [Configure the Tax Calculation feature](#configure-the-tax-calculation-feature) section, follow these steps to enable Tax Calculation uilize the settings provided by the Tax Calcualtion feature.

The setup in this section is done by legal entity. You must configure it for each legal entity that you want to enable Tax Calculation for in Finance.

1. In Finance, go to **Tax** \> **Setup** \> **Tax configuration** \> **Tax calculation parameters**.
2. On the **General** tab, set the following fields:

    - **Enable advanced tax calculation** – Select this checkbox to enable Tax Calculation for the legal entity. If it isn't enabled for the current legal entity, the legal entity will continue to use the existing tax engine to determine and calculate tax.
    - **Feature name** – Select a completed tax feature setup and version for the legal entity. For more information about how to set up and complete a published tax feature, see the previous section of this article.
    - **Business Process** – Select the business processes to enable.

3. Using the **Sales tax rounding rule** group of fields, define the expected rounding rule for the legal entity. For more information about the rounding logic, see [Tax calculation rounding rules](https://go.microsoft.com/fwlink/?linkid=2166988).
4. On the **Error handling** tab, define the expected error handling method for the legal entity. Three options are available:

    - No
    - Warning
    - Error

    You can set up an error handling method for each result code in the **Details** section.

5. On the **Multiple VAT registration** tab, you can turn on VAT declaration, EU Sales List, and Intrastat separately to work under a multiple VAT registrations scenario. For more information about tax reporting for multiple VAT registrations, see [Reporting for multiple VAT registrations](emea-reporting-for-multiple-vat-registrations.md).
6. Save the setup, and repeat the previous steps for each additional legal entity. When a new version of Tax Calculation feature is completed, and you want it to be applied, set the **Feature name** field on the **General** tab of the **Tax calculation parameters** page (see step 2).
