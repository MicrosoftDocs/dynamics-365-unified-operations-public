---
# required metadata

title: Create a Payment Invoice
description: This topic lists the steps for creating monthly lease invoices, which can be created for individual leases or for multiple leases using a batch process.  
author: moaamer
manager: Ann Beebe
ms.date: 07/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-07-28
ms.dyn365.ops.version: 10.0.14

---
# Create a Payment Invoice

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

You can create monthly lease invoices individually, or for multiple leases using a batch process. The following procedure lists the steps to create an individual lease payment entry when the **Pay to Vendor** parameter on the lease book is enabled.

1. Select a lease in the main lease summary list and click (**Books > Payment schedule**).

2. Select payment to be made and click on Create journal. The user will receive an infolog showing a journal was created against the selected payment.

3. Click **Invoice journals** and select the invoice to be paid. Open the **Lines** tab to review the journal entry before posting to the general ledger.

 > [!Note]
 > The vendor posting profile from **Accounts payable parameters** will default to vendor invoice lines created.

4. Click the correct journal and select the invoice to be paid. For this example, the **Pay to Vendor** parameter is turned on, so the invoice will be in the invoice journal. A summary of the journal entry is seen in the Overview section, while details on the actual journal lines can be seen in the Lines section below.

 > [!Note]
 > If the **Pay to Vendor** parameter is disabled on the **Lease book setup** page, payment journal entries will be listed on the **Asset leasing** page for the lease book and the system will create a asset leasing entry instead of an invoice. The lease payment entry will post to the journal name that's listed in the **Monthly lease journal** field.

5. When the transaction is posted, you can view the transaction information, and the carrying value of the lease liability, by clicking **Liability transactions** on the lease book.

6. On the payment schedule, the **Journal posted** field will be checked and the invoice journal number will populate on this line. After a payment journal is created against a month, an entry cannot be recreated unless it's reversed first.
