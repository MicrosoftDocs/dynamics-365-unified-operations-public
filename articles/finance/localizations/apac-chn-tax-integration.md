---
# required metadata

title: Configure tax integration for China
description: This topic describes the process for configuring tax integration for China.
author: ShylaThompson
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustParameters, VATInvoiceDescTable_CN, TaxProfileTable_CN
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 265264
ms.assetid: e5dbbbe1-935f-4fb4-a014-447916051628
ms.search.region: China (PRC)
# ms.search.industry: 
ms.author: leguo
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Configure tax integration for China

[!include [banner](../includes/banner.md)]

This topic describes the process for configuring tax integration for China.

## Prerequisites for Dynamics 365 Finance version 10.0 and later

To enable the system to generate this code as output in the exported file, you must complete the following tasks in the order in which they are listed.

| Prerequisite | Description | More information |
|------------|-------------|------------------------|
| Set up a hierarchy for product classification. | You must set up a category hierarchy for the classification of goods and services, and you must relate product items (goods or services) with category nodes. By using this functionality, you can set up any hierarchy that is required in a company. | [Create a hierarchy of product classification](../../supply-chain/pim/tasks/create-hierarchy-product-classification.md) |
| Assign the new hierarchy to a tax integration profile. | Go to **Accounts receivable &gt; Tax integration &gt; Tax integration profiles**, and then, in the **Commodity code hierarchy** field, select the new category. | |
| Select a commodity code for invoice lines. | For invoice lines that aren't related to product items (such as free text invoice lines and project invoice lines), or invoice lines that are created based on hour, expense, and fee journals, you can set up a default commodity code on the **Tax integration profiles** page. | |
| Identify the model mapping to use for import files. | Go to **Accounts receivable &gt; Periodic tasks &gt; VAT invoice integration**, and then select **Import**. Select the model mapping for the import file from one of the providers (Aisino or BaiWang), depending on which provider's software the company integrates exported invoices with. This selection should be made only one time. (The system saves the selected value.)<ul><li>To import a text file (\<file name\>\_invoicing result.TXT), set the **Import BaiWang TXT file** option to **Yes**. Then, in the **Model mapping** field, select **BaiWang – txt file mapping**.</li><li>To import a text file from Aisino or an XML file from BaiWang (exported files from BaiWang software), set the **Import BaiWang txt file** option to **No**. Then, in the **Model mapping** field, select **Aisino or BaiWang – xml file mapping**.</li></ul> | |
| Import configurations from Microsoft Dynamics Lifecycle Services (LCS). | For integration with Aisino software, you must import the following configurations from LCS:<ul><li>GoldenTax model</li><li>GST Export model mapping (CN)</li><li>GTS Export format (Aisino) (CN)</li><li>GTS Import model mapping (CN)</li><li>GTS Import format (Aisino) (CN)</li></ul>For integration with BaiWang software, you must import the following configurations from LCS:<ul><li>GoldenTax model</li><li>GST Export model mapping (CN)</li><li>GTS Import model mapping (CN)</li><li>GTS Export format (BaiWang) (CN)</li><li>GTS Import format (BaiWang)-txt) (CN)</li><li>GTS Import format (BaiWang-xml) (CN)</li></ul> | [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md) |

> [!NOTE]
> You can import a text file that is received as a response after import to BaiWang software. Alternatively, you can import XML files that are exported from BaiWang software.

## Configure tax integration for China

Before you can configure tax integration, you must turn it on. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**, and then, on the **Ledger and sales tax** tab, on the **General** FastTab, set the **Integration with tax system** option to **Yes**.

To configure tax integration for China, follow these steps.

1. On the **VAT invoice description** page, create a new value-added tax (VAT) invoice description. For example, you might have to set the following values:

    - **VAT invoice description ID:** InvoiceDescID01
    - **Description:** 设备
    - **Unit:** Box

2. On the **Tax integration profiles** page, create a new tax integration profile. You can set up tax integration profiles that are used when invoices are imported or exported. In the tax integration profile, you can specify the following information:

    - Sales tax code
    - Maximum invoice amount
    - Default description and unit for the golden tax invoice

    You can also specify whether non-deductible VAT invoices should be included.

The following illustration shows the tax integration process.

[![Tax integration process.](./media/ic666469.gif)](./media/ic666469.gif)

## Additional resources

- [Import the Chinese Golden Tax data entity](apac-chn-import-golden-tax-data-entity.md) (Not applicable for Microsoft Dynamics 365 for Finance and Operations version 10.0 \[April 2019\] and later)
- [Chinese tax integration modification for VAT customer invoices FAQ](apac-chn-tax-integration-vat-customer-invoices.md)
- [Set up basic tax integration profile for China](./tasks/set-up-basic-tax-integration-profile-china.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]