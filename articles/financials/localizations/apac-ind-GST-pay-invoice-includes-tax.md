---
# required metadata

title: Pay an invoice that includes tax
description:  
author: EricWang
manager: RichardLuan
ms.date: 06/03/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: EricWang
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Payment of an invoice that has tax

Complete the following steps to post an invoice thatincludes sales tax.

1. Click **Accounts receivable > Payments > Payment journal**.
2. Create a record, and in the **Name** field, select a value.
3. On the **Setup** tab, select the **Amounts include sales tax** check box.
4. Click Lines.
5. Create a customer advance payment journal.
6. Click **Functions > Settlement**.
7. In the **Invoice** field, select a value.
8. Close the form.
9. Save the record.
10. Click **Post > Post**.
11. Close the message.

### Validate financial entries

Validate the financial entries by clicking, **Inquiries > Voucher**.

The following table shows the tax entries that are generated when an invoice payment is made in various scenarios

| Transaction details | Example                                                      | Tax entries that are generated during settlement             |
| ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Invoice = Payment   | Invoice amount: 12,000.00<br/>Payment amount: 12,000.00      | No tax entries are generated.                                |
| Invoice < Payment   | Invoice amount: 6,000.00<br/>Payment amount: 12,000.00<br/> Note that if either an HSN code or an SAC is defined for the journal, tax is calculated and posted on the journal amount. | Tax is calculated and posted on the payment amount.<br/>Tax on the payment is reversed to the extent of the invoice amount in the related voucher.<br/>IGST interim payable account Dr. 2,000.00<br/>IGST payable account Cr. 2,000.00<br/>**Related voucher**<br/>IGST interim payable account Cr. 1,000.00<br/>IGST payable account Dr. 1,000.00 |
| Invoice > Payment   | Invoice amount: 24,000.00<br/>Payment amount: 12,000.00 without tax | No tax entries are generated.                                 |





