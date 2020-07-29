---
# required metadata

title: Create a Payment Invoice
description:  
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

Monthly lease invoices can either be created on an individual lease basis or through a batch process for multiple leases. The following steps detail how to create an individual lease payment entry when the Pay to Vendor parameter on the lease book is enabled.

1.	Select a lease in the main lease summary and click on Books > Payment schedule.

2.	Select payment to be made and click on Create invoice. The user will receive an infolog showing an invoice was created against the selected payment.

3.	Click on Invoice journals and select invoice to be paid. Select the Lines tab to review journal entry before posting to the general ledger.

Note: The vendor posting profile from Accounts payable parameters will default to vendor invoice lines created.

4.	Click on the correct journal and select the invoice to be paid. For this example, the Pay to Vendor parameter is turned on, so the invoice will be in the Invoice journal. A summary of the journal entry is seen in the Overview section, while details on the actual journal lines can be seen in the Lines section below.
Note: If the Pay to Vendor parameter is disabled in the lease book setup, payment journal entries will exist in the General journals form on the lease book and will create a general journal entry instead of an invoice. The lease payment entry will post to the journal name indicated in the Monthly lease journal field.

5.	Once posted, to view the transaction and the carrying value of the lease liability, click the Liability Transactions on the lease book.

6.	On the payment schedule, the Journal posted field will be checked and the invoice journal number will populate on this line. Once a payment journal is created against a month, an entry cannot be recreated unless first reversed.
