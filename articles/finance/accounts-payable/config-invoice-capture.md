---
# required metadata

title: Configure the Invoice capture solution
description: This article explains how to configure the Invoice capture solution.
author: sunfzam
ms.date: 04/04/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Configure the Invoice capture solution

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

After the Invoice capture solution is installed, default configurations are provided to use Invoice capture. The default settings might not fully meet the customer's requirements. In Invoice capture, configurations can be found in the **System preference**. 

## System preference 
1. **AI Builder model** - The default model is set as the **Invoice processing model**. To update the default model, select one from the drop-down list. 
2. **Channel for file upload** -  A default channel is provided for directly uploading the invoice files.  
3. **File filter** - Select the file filter to apply additional filtering to incoming files at application level.  
4. **Configuration group** - The configuration group that will be used when a configuration group is not set at the legal entity or vendor level during invoice processing. 
5. **Use continuous learning** - Select this option to have the continuous learning feature **On**.

### Definition of master data  

Invoice capture supports two data types for vendor invoice processing: legal entities and vendors. 

**Legal entities** are organizations registered with legal authorities and are defined in Dynamics 365 Finance. Business activities are performed and recorded separately for each legal entity. In Power Platform, business units, security roles, and users are linked to conform to the role-based security model. This controls data access through business units and security roles, allowing AP clerks to view only the invoices assigned to their users. 

**Vendors** are supplier organizations or sole proprietors who supply goods or services to a business, as defined in Dynamics 365 Finance. The vendor master data is used to automatically derive the vendor account, increasing the touchless rate in invoice processing. 

The Invoice capture solution provides a configuration space where you can load basic information from existing legal entities and vendors in Finance. When a supplier invoice arrives, the legal entity and vendor account must be correctly determined before transferring the invoice to the target system. The use of master data for the derivation of legal entities and vendor accounts can reduce maintenance work on mapping rules. 


### Sync master data
The **Manage legal entities** and **Manage vendors** processes work the same. In **Manage legal entities**, users can't create legal entities manually. Instead, the legal entities are synchronized from Dynamics 365 Finance, following these steps: 
1. Go to **Setup > System setup > Manage legal entities**.
2. Select **Sync**. 
3. Select **OK** in the confirmation dialog box. 

After synchronization is completed, a message will show the number of new legal entities. The list view will refresh automatically to show the new legal entities.  

>[!Note]
>An Accounts payable administrator will manually trigger the sync. 



