---
# required metadata

title: Get started with Tax Calculation
description: This topic explains how to set up Tax Calculation.
author: wangchen
ms.date: 04/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18

---


# Get started with the Tax Calculation (Preview)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic provides information about how to get started with Tax Calculation. It first guides you through the configuration steps in Microsoft Dynamics Lifecycle Services (LCS), Regulatory Configuration Service (RCS), and Dynamics 365 Finance and Dynamics 365 Supply Chain Management. It then reviews the common process for using Tax Calculation capabilities in Finance and Supply Chain Management transactions.

The setup consists of four main steps:

1. In LCS, install Tax Calculation.
2. In RCS, set up the Tax Calculation feature. This setup isn't specific to a legal entity. It can be shared across legal entities in Finance and Supply Chain Management.
3. In Finance and Supply Chain Management, set up the Tax Calculation parameters by legal entity.
4. In Finance and Supply Chain Management, create transactions such as sales orders, and use Tax Calculation to determine and calculate taxes.

## Prerequisites

Before you can complete the procedures in this topic, the following prerequisites must be in place:

- You have access to your LCS account, and you've deployed an LCS project with a Tier 2 (or above) environment that runs Dynamics 365 version 10.0.18 with KB4616360 or later.
- You have access to your RCS account.
- You've contacted Microsoft to enable the flighting in your deployed Finance or Supply Chain Management environment.

## Set up Tax Calculation in LCS

1. Sign in to [LCS](https://lcs.dynamics.com)
2. Complete the setup for Microsoft Power Platform integration. For more information, see [Add-ins overview](../../fin-ops-core/dev-itpro/power-platform/add-ins-overview.md).
3. Select one of your deployed non-production environments, and then select **Install a new add-in**.
4. Select **Tax Calculation (preview)**.
5. Read and agree to the terms and conditions, and then select **Install**.

## Set up Tax Calculation in RCS

The steps in this section aren't related to a specific legal entity. You must complete this procedure only one time, and you can complete it in any legal entity in RCS.

1. Sign in to [RCS](https://marketing.configure.global.dynamics.com/).
2. In Finance, in the **Electronic reporting** workspace, add a new configuration provider. Use your company name as the name of the provider. For more information, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).
3. Select the configuration provider that you just created, and then select **Set active**.
4. Select the **Microsoft** configuration provider, and then select **Repositories**.
5. In the **Type** field, select **Global**.
6. Select **Open**.
7. Go to **Tax Data Model**, expand the file tree, and then select **Tax Configuration**.
8. Select the latest version, and then select **Import**.
9. Return to the **Globalization features (Preview)** workspace, select **Features**, select the **Tax Calculation** tile, and then select **Add**.
10. Select one of the following feature types:

    - **New feature** – Create a feature setup that has blank content.
    - **Based on existing feature** – Create a feature from an existing feature, and copy the content from the existing feature setup.

11. Enter a name and description for the feature, and then select **Create feature**.

    After the feature is created, a draft version of it is automatically created.

12. Select the draft version of the feature, and then select **Edit**. The **Tax Calculation setup** page is filled in.
13. Select **Configuration version**. You should see the configuration version that you imported in step 8.

    Microsoft provides a default tax configuration for the tax calculation add-in. This configuration covers most of the requirements for tax calculation behaviors. It will be updated based on market feedbacks. If you must extend the configuration to meet specific requirements, see [How to build extension in tax service](./tax-service-add-data-fields-tax-integration-by-extension.md) for information about how to generate and select your own tax configuration.

    After you select **Configuration version**, several additional tabs appear:

    - **Tax codes** – This tab is mandatory. It's used to maintain master data for tax codes. All tax codes that are created on this tab are automatically synced to Finance when you enable the current version of the tax feature setup in the legal entity.
    - **Tax codes applicability** – This tab is mandatory. It's used to define a matrix that determines the tax code, tax group, and item tax group. The tax code that is determined is used to calculate the tax amount. The values of the **Tax code**, **Tax group**, and **Item tax group** fields are returned to Finance.
    - **Customer tax registration number applicability** – This tab is optional. If you have multiple tax registration numbers for one customer, Tax Calculation can automatically determine the correct tax registration number. In the matrix on this tab, you define the rules that the uses to make the determination. Otherwise, Finance and Supply Chain Management will continue to use the default tax registration number on taxable documents for sales transactions.
    - **Vendor tax registration number applicability** – This tab is optional. If you have multiple tax registration numbers for one vendor, Tax Calculation can automatically determine the correct tax registration number. In the matrix on this tab, you define the rules that the uses to make the determination. Otherwise, Finance and Supply Chain Management will continue to use the default tax registration number on taxable documents for purchase transactions.
    - **List code applicability** – This tab is optional. It can help automatically determine the value of the **List code** field through more flexible and configurable rules. In the matrix on this tab, you can define the rules that the uses to make the determination. Otherwise, Finance and Supply Chain Management will continue to use the default code on taxable documents.

14. On the **Tax codes** tab, select **Add**, and enter the tax code and a description.
15. Select **Tax component**. The tax component is a group of methods that were defined in the previous version of the selected tax configuration. The following tax components are available:

    - By net amount
    - By gross amount
    - By quantity
    - By margin
    - Tax on tax

16. Select **Save**. More fields become available, based on the tax component that you selected.
17. Use the following options to identify the nature of the tax code:

    - Is Exempt
    - Is Use tax
    - Is Reverse Charge
    - Exclude from Base Amount Calculation

    For a use tax scenario, set up a single tax code that has a positive tax rate, and mark it as **Is Use tax**.

    For a reverse charge scenario, set up two tax codes, one of which has a positive tax rate, and the other of which has a negative tax rate but the same rate value. Mark the negative tax code as **Is reverse charge**. For more information about the reverse charge solution in Finance, see [Reverse charge mechanism for VAT/GST scheme](emea-reverse-charge.md).
    
    For some tax types which should be excluded in the tax base amount calculation for price inclusive transactions, like custom duty in some countries, select the **Exclude from Base Amount Calculation** check box.

    Maintain tax rates and the tax amount limits for this tax code.

18. Repeat steps 14 through 17 to add all other tax codes that are required.
19. On the **Tax codes applicability** tab, select the columns that are required to determine the correct tax code, and then select **Add**.
20. Enter or select values for each column. The **Tax code**, **Tax group**, and **Item tax group** fields will be the output of this matrix.
21. Repeat steps 19 through 20 to set up the applicability of customer tax registration numbers, vendor tax registration numbers, and list codes.
22. Select **Save**, and then close the page.
23. Select **Change status** \> **Complete**. After the status is changed to **Complete**, the version can no longer be edited.
24. Select **Change status** \> **Publish**. This version of the tax feature setup will be pushed to the global repository and will be visible to each legal entity in Finance.

## Dynamics 365 setup

After you complete the setup in RCS, as described in the previous section, you will have a published version of the tax feature. Follow these steps to set up Tax Calculation in Finance.

The setup in this section is done by legal entity. You must configure it for each legal entity that you want to enable Tax Calculation for in Finance.

1. In Finance, go to **Tax** \> **Setup** \> **Tax configuration** \> **Tax calcluation setup (Preview)**.
2. On the **General** tab, set the following fields:

    - **Enable Tax Calculation** – Select this check box to enable Tax Calculation add-in for the legal entity. If it isn't enabled for the current legal entity, the legal entity will continue to use the existing tax engine to determine and calculate tax.
    - **Feature setup** – Select a published tax feature setup and version for the legal entity. For more information about how to set up and complete a published tax feature, see the previous section of this topic.
    - **Business Process** – Select the business processes to enable.
    - **Enable tax code adjustment** – Set this option to **Yes** to enable tax code adjustments on the sales tax page.

3. On the **Calculation** tab, define the expected rounding rule for the legal entity.
4. On the **Error handling** tab, define the expected error handling method for the legal entity. Three options are available for each result code:

    - No
    - Warning
    - Error

5. Save the setup.
6. Repeat steps 1 through 5 for each additional legal entity.

## Transaction processing

After you've completed all the setup procedures, you can use Tax Calcuation to determine and calculate tax in Finance. The steps to process transactions remain the same. The following transactions are supported in Finance version 10.0.18:

- Sales process

    - Sales quotation
    - Sales order
    - Confirmation
    - Picking list
    - Packing slip
    - Sales invoice
    - Credit note
    - Return order
    - Header charge
    - Line charge

- Purchase process

    - Purchase order
    - Confirmation
    - Receipts list
    - Product receipt
    - Purchase invoice
    - Header charge
    - Line charge
    - Credit note
    - Return order
    - Purchase requisition
    - Purchase requisition line charge
    - Request for quotation
    - Request for quotation header charge
    - Request for quotation line charge

- Inventory process

    - Transfer order – ship
    - Transfer order - receive
