---
# required metadata

title: Get started with tax calculation service
description: This topic explains the detail setups in tax calculation service.
author: wangchen
manager: beya
ms.date: 01/28/2021
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

 

This topic provides information about how to get started using tax calculation service. First, the topic will walk you through the configuration steps in Microsoft Dynamics Lifecycle Services (also known as LCS), Microsoft Dynamics 365 Regulatory Service (also known as RCS), and Microsoft Dynamics 365 Finance and Supply Chain Management. Next, you will review the common process for using the tax calculation service in Dynamics 365 Finance and Supply Chain Management transactions.

There are four main steps to complete in this topic: 

·     LCS setup: Install tax calculation service add-in. 
·     RCS setup: Set up tax feature, the setup here is legal entity irrelevant and can be shared across legal entities in Microsoft Dynamics 365 Finance and Supply Chain Management.
·     Finance setup: Set up tax service parameter, the setup here is by legal entity.
·     Transaction processing: Create transaction (for example. sales order) in Microsoft Dynamics 365 Finance and Supply Chain Management, determine, and calculate tax through tax calculation service.

Note that all the setups in this document are under the scope of tax service public preview, content is subjected to change after general availability.



## Pre-requisites

To complete these steps, you must first complete the following steps: 

·    Access to your LCS account and deploy a LCS project with Microsoft Dynamics 365 version 10.0.18 or higher
·    Access to your RCS account
·    Contact Microsoft team to enable the flighting in your deployed  Microsoft Dynamics 365 environment

## Microsoft Dynamics Lifecycle Services setup

1.    Sign into [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com)
2.    Complete the Power Platform Integration setup. For more information, please refer to [Add-ins overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/add-ins-overview).
3.    Select one of you deployed non-production environment, and click **Install a new add-in**.
4.    Select **Tax calculation service (preview)**.
5.    Read and agree all the terms and conditions, and then click **Install**.

## Microsoft Dynamics Regulatory Service setup

 Setup in this section is irrelevant to legal entity. You only need to configure it once under any legal entity in Microsoft Dynamics 365 Regulatory Service.

1.    Sign into [Microsoft Dynamics 365 Regulatory Service](https://marketing.configure.global.dynamics.com/) 

2.    Go to **Electronic reporting** workspace and add a new configuration provider. For more information, please refer to [Create configuration providers and mark them as active](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11) 

3.    Click on **Configuration providers.**

4.    Add a new configuration provider, you can use your company name as the provider name

5.    Go back to **Electronic reporting** workspace.

6.    Select the configuration provider you created in step 4 and click “**Set active**”

7.    Select configuration provider **Microsoft** (not the above provider you created), click **Repositories**

8.    Select Type “**Global**” and click **Open**

9.    Navigate to **Tax Data Model**, expand the file tree, and select **Tax Configuration - Europe**

10.  Select the **latest version** and click **Import**

11.  Go back to **Globalization features（Preview）** workspace and click on **Features > Tax calculation service** tile. 

12.  Click **Add**

13.  Select **feature type**, enter **feature name,** **feature description,** and then click **Create feature**. There are two types of feature:

·     **New feature**: this option will create a new feature setup with blank content.

·     **Based on existing feature**: this option will derive from an existing feature setup and copy all the existing contents.

After the feature is created, a draft version of this feature will be created automatically.

14.  Select the draft feature version, click **Edit**, tax feature setup form will be populated.

15.  Select **Configuration version**, you can see the configuration version you imported in step 10. Microsoft will provide default tax configuration for tax calculation service; it covers the majority requirements of tax calculation behaviors and Microsoft will update it based on the feedback from markets. If you need to extend it to meet some specific requirements, you could refer to [**How to build extension in tax service**](https://go.microsoft.com/fwlink/?linkid=2138483) to generate your own tax configuration and select it here.

16. After you select configuration version, several extra tabs will be shown:

·     Tax codes

·     Tax codes applicability

·     Customer tax registration number applicability

·     Vendor tax registration number applicability

·     List code applicability

Here is the explanation of each tab.

·     Tax codes: This tab is mandatory for tax calculation service. It will be used to maintain tax code master data in tax service. All the tax codes created here will be automatically synchronized to Dynamics 365 Finance when you enable the current tax feature setup version in the legal entity. A synchronization feature will be provided later to initialize tax code/sales tax group/item sales tax group from Dynamics 365 to tax calculation service when you enable tax calculation service for the first time.

·     Tax codes applicability: This tab is mandatory for tax calculation service. It will be used to define a matrix to determine tax code, tax group, and item tax group. Determined tax code will be used to calculate tax amount and all the three fields will be returned to Dynamics 365 Finance. 

·     Customer tax registration number applicability: This tab is optional for tax calculation service. If you have multiple tax registration numbers under one single customer and want to apply tax calculation service to automatically determine the correct one, you could define the rules in this matrix to determine it. Otherwise, Dynamics 365 Finance and Supply Chain Management will continue to use the default one on the taxable documents for sales transactions.

·     Vendor tax registration number applicability: This tab is optional for tax calculation service. If you have multiple tax registration numbers under one single vendor and want to apply tax calculation service to automatically determine the correct one, you could define the rules in this matrix to determine it. Otherwise, Dynamics 365 Finance and Supply Chain Management will continue to use the default one on the taxable documents for purchase transactions.

·     List code applicability: This tab is optional for tax calculation service. It can help you automatically determine List code field with the more flexible and configurable rules. You could define the rules in this matrix to determine it. Otherwise, Dynamics 365 Finance and Supply Chain Management will continue to use the default one on the taxable documents.

17.  Go to **Tax codes** tab.

18.  Click **Add** to add tax code.

19. Enter **Tax code**, **Description**, and select **Tax component.** Tax component is a group of tax calculation methods defined in previous selected tax configuration version. Following tax components will be available in public preview:

·     By net amount
·     By gross amount
·     By quantity
·     By Margin
·     Tax on tax

20.  Click **Save**, then more fields will be shown based on the tax component you have selected.

21. Use the **toggle** under **General** table to identify the nature of this tax code.

·     Is Exempt
·     Is Use tax
·     Is Reverse Charge

For use tax scenario, we expect you to set up single tax code with positive tax rate and mark it as use tax.

For reverse charge scenario, we expect you to set up two tax codes, one with positive tax rate, the other with negative tax rate but same rate value and mark the negative tax code as reverse charge. Refer to this document for more detail reverse charge solution in Dynamics 365 Finance: https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-reverse-charge

22.  Maintain **tax rates** for this tax code.
23.  Maintain **tax amount limits** for this tax code.
24.  Add other required tax codes by repeating from step 14 to step 19.
25.  Go to **Tax codes applicability** tab.
26.  **Manage column** form will be populated for the first time, you could select the columns, which are required to determine correct tax code and add these columns to the right side
27.  Click **Add** to add applicability rule to determine tax code.
28.  Enter or select values for each column, **Tax code**, **Tax group**, **Item tax group** will be the output of this matrix and return to transaction after determination in tax service
29.  Repeat from step 26 to step 28 if you need to set up customer tax registration number applicability,  vendor tax registration number applicability, and list code applicability.
30.  Click **Save** after all above setups are completed and **Close** the form.
31.  Click **Change status** and select **Complete**, after the status is changed to **Complete**, this version cannot be edited anymore.
32.  Click **Change status** and select **Publish**, then this tax feature setup version will be pushed to global repository and visible by each legal entity in Dynamics 365 Finance.



## Microsoft Dynamics 365 setup

After you complete the setups in section “Microsoft Dynamics Regulatory Configuration Service setup”, you will have a published version of tax feature, then you can continue the setups in this section in Dynamics 365 Finance.

Setup in this section is by legal entity. configure it for each legal entity which you want to enable tax service in Dynamics 365 Finance.

1.    Go to module **Tax.**

2.    Go to path **Setup** – **Tax configuration** – **Tax service setup (Preview).**

3.    Under **General** tab, configure the parameters. Here is the explanation of each parameter:

·     **Enable tax service**: You can enable tax service by legal entity. If tax service is not enabled for current legal entity, it will continue to use existing tax engine to determine and calculate tax.

·     **Feature setup**: Select a published tax feature setup and version here for each legal entity. Please refer to section “Microsoft Dynamics Regulatory Configuration Service setup” about how to complete a published tax feature setup version.

·     **Business Process**: You can enable which business process will be enabled for tax service. 

·     **Enable tax code adjustment**: You can turn on this parameter if you allow the end use to adjust calculated tax directly on the sales tax form on taxable documents.

4.    Under **Calculation** tab, you can define the expected rounding rule by each legal entity. 

5.    Under **Error handling** tab, you can define the expected error handling method by each legal entity. There are three options available for each result code from tax service:

·     No

·     Warning

·     Error

6.    **Save** the tax service parameter setup and repeat step 1 to 5 for each legal entity.

 

## Transaction Processing

 

After you complete all the above setups, you can now use tax service to determine and calculate tax in Dynamics 365 Finance. The steps to process transactions in Dynamics 365 keep same as now. Here are supported transactions in 10.0.18:

Sales process

·     Sales quotation

·     Sales order 

·     Confirmation 

·     Picking list 

·     Packing slip 

·     Sales invoice 

·     Credit note 

·     Return order 

·     Header charge 

·     Line charge 



Purchase process

·     Purchase order 

·     Confirmation 

·     Receipts list 

·     Product receipt 

·     Purchase invoice 

·     Header charge 

·     Line charge 

·     Credit note 

·     Return order 

·     Purchase requisition 

·     Purchase requisition line charge 

·     Request for quotation 

·     Request for quotation header charge 

·     Request for quotation line charge 

 

Inventory process

·     Transfer order – ship

·     Transfer order - receive

 
