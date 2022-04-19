---
# required metadata

title: Import the Chinese Golden Tax files
description: This topic explains how to import the Chinese Golden Tax files into Microsoft Dynamics 365 Finance.
author: ilkond
ms.date: 12/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DataManagementWorkspace, DMFQuickImportExportRnr
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 261394
ms.search.region: China (PRC)
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Import the Chinese Golden Tax files

[!include [banner](../includes/banner.md)]
  
This topic explains how to import files with external invoice numbers from providers (Aisino or BaiWang) into Dynamics 365 Finance. You can import txt and xml files from the BaiWang provider, and txt and txt files from the Aisino provider.

To import the files from a provider with external invoice numbers, complete the following steps.

1. Go to **Accounts receivable** > **Periodic tasks** > **VAT invoice integration**.
2. On the Action Pane, select **Import**. 
3. Select the model mapping for the import file from one of the providers, either Aisino or BaiWang, depending on which provider's software the company integrates exported invoices with. 
   - To import a text file (\<file name\>_invoicing result.TXT) from the BaiWang provider, set the **Import BaiWang TXT file** option to **Yes**. Then, in the **Model mapping** field, select **BaiWang – txt file**.
   - To import a text file from Aisino or an XML file from BaiWang, set the **Import BaiWang txt file** option to **No**. Then, in the **Model mapping** field, select **Asimo - txt** or **BaiWang-xml file**.
6. Select a file for upload and then select **Upload**.
7. Select **OK**.
  
 > [!NOTE] 
 > To import files, upload the import formats. For more information, see [Import configurations](apac-chn-tax-integration.md).



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
