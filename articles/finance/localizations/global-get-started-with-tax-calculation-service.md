---
# required metadata

title: Get started with tax calculation service
description: This topic explains how to set up the tax calculation service.
author: wangchen
manager: tfehr
ms.date: 03/01/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
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


# Get started with tax calculation service (Preview)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]
 

This topic provides information about how to get started with the tax calculation service. First, the topic will walk you through the configuration steps in Microsoft Dynamics Lifecycle Services (LCS), Microsoft Dynamics 365 Regulatory Service (RCS), and Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management. Next, you will review the common process for using the tax calculation service in Finance and Supply Chain Management transactions.

There are four main steps to complete this setup: 

1. Install the tax calculation service add-in in LCS.
2. Set up the tax feature in RCS. This set up is not specific to a legal entity and can be shared across legal entities in Finance and Supply Chain Management.
3. Set up the tax service parameters by legal entity in Finance and Supply Chain Management.
4. Create transactions, such as sales orders, in Finance and Supply Chain Management, and use the tax calculation service to determine and calculate taxes.

## Prerequisites

To complete these procedures in this topic, you must first complete the following: 

·    Have access to your LCS account and deploy a LCS project with Microsoft Dynamics 365 version 10.0.18 or higher.
·    Have access to your RCS account.
·    Contact Microsoft to enable the flighting in your deployed Finance or Supply Chain Management environment.

## Set up the tax calculation service in Lifecycle Services

1. Sign into [Lifecycle Services](https://lcs.dynamics.com)
2. Complete the Power Platform Integration setup. For more information, see [Add-ins overview](../../dev-itpro/power-platform/add-ins-overview.md).
3. Select one of you deployed non-production environments, and then select **Install a new add-in**.
4. Select **Tax calculation service (preview)**.
5. Read and agree the terms and conditions, and then select **Install**.

## Set up the tax calculation service in RCS 

The steps in this section aren't related to a specific legal entity. You only need to complete this procedure one time using any legal entity in RCS. Before you begin this procedure, sign in to the [Microsoft Dynamics 365 Regulatory Service](https://marketing.configure.global.dynamics.com/).

1. In Finance, in the **Electronic reporting** workspace, add a new configuration provider. Use your company name as the provider name. For more information, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md). 
2. Select the configuration provider you just created and then select **Set active**.
3. Select configuration provider, **Microsoft** and then select **Repositories**
4. In the **Type** field, select **Global**, and then select **Open**.
5. Go to **Tax Data Model**, expand the file tree, and then select **Tax Configuration - Europe**
6. Select the **latest version** and click **Import**
7. Return to the **Globalization features（Preview）** workspace, select **Features > Tax calculation service** tile, and then select **Add**. 
8. Select the feature type, and enter the feature name and feature description, and then select **Create feature**. There are two types of features you can created:

  - **New feature**: Create a new feature setup with blank content.
  - **Based on existing feature**: Create a new feature from an existing feature and copy the existing contents.

 After the feature is created, a draft version of the feature is automatically created.

9. Select the draft feature version and select **Edit**. The **tax feature setup** page will be populated.
10. Select **Configuration version**. You can see the configuration version you imported in step 6. Microsoft provides a default tax configuration for the tax calculation service. The configuration covers the majority requirements of tax calculation behaviors and will be updated based on market feedback. If you need to extend the configuration to meet specific requirements, see [**How to build extension in tax service**](https://go.microsoft.com/fwlink/?linkid=2138483) to generate and select your own tax configuration.
11. After you select configuration version, several extra tabs will be shown:

   - **Tax codes**: This tab is mandatory for the tax calculation service and is used to maintain tax code master data. All of the tax codes created here are automatically synchronized to Finance when you enable the current tax feature setup version in the legal entity.
   - **Tax codes applicability**: This tab is mandatory for the tax calculation service and is used to define a matrix to determine the tax code, tax group, and item tax group. The determined tax code is used to calculate the tax amount. The three fields, **Tax code**, **Tax group**, and **Item tax group** are returned to Finance. 
   - **Customer tax registration number applicability**: This tab is optional for the tax calculation service. If you have multiple tax registration numbers for one customer, and you want to apply the tax calculation service to automatically determine the correct tax registration number, define the rules in this matrix to make the determination. Otherwise, Finance and Supply Chain Management will continue to use the default number on taxable documents for sales transactions.
   - **Vendor tax registration number applicability**: This tab is optional for the tax calculation service. If you have multiple tax registration numbers for one vendor and you want to apply the tax calculation service to automatically determine the correct tax registration number, define the rules in this matrix to make the determination. Otherwise, Finance and Supply Chain Management will continue to use the default number on taxable documents for purchase transactions.
   - **List code applicability**: This tab is optional for the tax calculation service and can help you automatically determine the value of the **List code** field with more flexible and configurable rules. You can define the rules in this matrix to determine the list code. Otherwise, Finance and Supply Chain Management will continue to use the default code on taxable documents.

12.  On the **Tax codes** tab, select **Add** and enter the tax code and a description. Next, select **Tax component**. The tax component is a group of tax calculation methods defined in previous selected tax configuration version. The following tax components are available:

  - By net amount
  - By gross amount
  - By quantity
  - By Margin
  - Tax on tax

13. Select **Save**. More fields will become available based on the tax component you select.
14. Use the toggle on the **General** table to identify the nature of this tax code.

   - Is Exempt
   - Is Use tax
   - Is Reverse Charge

  For a use tax scenario, set up a single tax code with a positive tax rate and mark it as **Is use tax**.

  For a reverse charge scenario, set up two tax codes, one with positive tax rate, and one with a negative tax rate but same rate value. Mark the negative tax code as **Is reverse charge**. For more information about the reverse charge solution in Finance, see [Reverse charge mechanism for VAT/GST scheme](emea-reverse-charge.md).

  Maintain tax rates and the tax amount limits for this tax code.

15. Add other required tax codes by repeating steps 12-14.
16. On to **Tax codes applicability** tab, select the columns required to determine the correct tax code and then select **Add**.
17. Enter or select values for each column. The **Tax code**, **Tax group**, and **Item tax group** fields will be the output of this matrix. 
18. Repeat steps 16 and 17 to set up customer tax registration number applicability, vendor tax registration number applicability, and list code applicability.
19. Select **Save** and then close the page.
20. Select **Change status** > **Complete**. After the status is changed to **Complete**, this version can't be edited anymore.
21. Select **Change status** > **Publish**. This tax feature setup version will be pushed to the global repository and visible to each legal entity in Finance.

## Microsoft Dynamics 365 setup

After you complete the steps in the previous section, **Set up the tax calculation service in RCS**, you will have a published version of tax feature. Complete the following steps to complete the tax calculation service setup in Finance. Setup in this section is done by legal entity. Configure the tax calculation service for each legal entity that you want to enable tax service for in Finance.

1. In Finance, go to **Tax** > **Setup** > **Tax configuration** > **Tax service setup (Preview)**.
2. On the **General** tab, enter the following field information:

     - **Enable tax service**: Select this check box to enable the tax service by legal entity. If the tax service isn't enabled for the current legal entity, it will continue to use the existing tax engine to determine and calculate tax.
     - **Feature setup**: Select a published tax feature setup and version for each legal entity. For more information about how to setup and complete a published tax feature, see the section, **Set up the tax calculation service in RCS**.
     - **Business Process**: Select the business processes to enable for the tax service. 
     - **Enable tax code adjustment**: Enable this parameter to allow adjustments to calculated tax directly on the sales tax form on taxable documents.

4. On the **Calculation** tab, define the expected rounding rule for each legal entity. 
5. On the **Error handling** tab, define the expected error handling method for each legal entity. There are three options available for each result code from the tax service:

      - No
      - Warning
      - Error

6. Save the tax service parameter setup and repeat steps 1 - 5 for each legal entity.

 
## Transaction processing

After the setup procedures are complete, you can use the tax service to determine and calculate tax in Finance. The steps to process transactions remain the same. The following transactions are supported transactions in Finance version 10.0.18:

Sales process

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

Purchase process

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

Inventory process

 - Transfer order – ship
 - Transfer order - receive

 
