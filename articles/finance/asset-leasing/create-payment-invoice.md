---
title: Create payment invoices
description: Learn about how to create monthly lease invoices. You can create invoices for individual leases, or you can use a batch process to create them for multiple leases.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/12/2021
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeasePaymentSchedule
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Create payment invoices

[!include [banner](../includes/banner.md)]


You can create monthly invoices for individual leases, or you can use a batch process to create them for multiple leases. The following procedure shows how to create an individual lease payment entry when the **Pay to Vendor** parameter on the **Lease book setup** page is turned on.

1. On the **Lease summary** page, select a lease, and then select **Books \> Payment schedule**.
2. Select the payment that must be made, and then select **Create journal**. You receive a message that states that a journal was created against the selected payment.
3. Select **Invoice journals**, and then select the invoice that must be paid.
4. On the **Lines** tab, review the journal entry before you post it to the general ledger.

    > [!NOTE]
    > By default, the vendor invoice lines that are created use the vendor posting profile from the **Accounts payable parameters** page.

5. Select the correct journal, and then select the invoice that must be paid.

    For this example, the **Pay to Vendor** parameter on the lease book is turned on. Therefore, the invoice will be in the invoice journal. The **Overview** section shows a summary of the journal entry, and the **Lines** section shows details of the actual journal lines.
    
   The system locks certain financial fields from being edited to prevent any variances between the transactions and the schedules. Some fields that are locked include: **Account**, **Amounts**, **Financial dimensions**, **Currency**, and **Transaction type**. Additionally, you won't be able to add or delete journal entry lines in any Asset leasing journal entries, as this might cause variances between the schedules and the transactions.

    > [!NOTE]
    > If the **Pay to Vendor** parameter is turned off, payment journal entries will be listed on the **Asset leasing** page for the lease book, and the system will create an asset leasing entry instead of an invoice. The lease payment entry will be posted to the journal name that is specified in the **Monthly lease journal** field.

6. After the transaction is posted, you can view the transaction information and the carrying value of the lease liability by selecting **Liability transactions** in the lease book.

    In the payment schedule, the **Journal posted** check box will be selected, and the line will show the invoice journal number. After a payment journal and an entry for that journal have been created, you must reverse the entry before it can be re-created.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
