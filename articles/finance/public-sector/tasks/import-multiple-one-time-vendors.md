--- 
# required metadata 
 
title: Import and create multiple one-time vendors and invoices in the public sector
description: This article provides information about how to simultaneously create an invoice and record for a new vendor when no purchase order is required.
author: twheeloc
ms.date: 02/14/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendImportOneTimeVendFileUpload_PSN   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Import and create multiple one-time vendors and invoices in the public sector

[!include [banner](../../includes/banner.md)]

When approval or a contract in the form of a purchase order is not required, you can create an invoice for a new vendor with whom you have no regular relationship, at the same time as creating a record for the vendor. This procedure was created using the PSUS demo company data in the public sector partition.

1. Go to **Accounts payable > Periodic tasks > Import one-time vendors and invoices**.
2. Browse for and select the CSV file that contains vendor information.
3. In the **Account structure** field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. Click **OK**.
    * The vendor and invoice information is imported. If there are errors, a report will be printed, and you should correct any listed entries in the import file and then reimport the file.  
6. Go to **Accounts payable > Periodic tasks > Process one-time vendors and invoices**.
    * Duplicate vendor names or Federal tax IDs will be looked for.  Important: If you choose not to process duplicate vendors, the related invoices won't be processed either. You can manually create an invoice by using the information in the CSV file.    
7. Click **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
