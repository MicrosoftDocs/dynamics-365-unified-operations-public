---
# required metadata

title: Apply prepayments to vendor invoices overview
description: This topic describes the capability for applying prepayments to vendor invoices automatically. 
author: sunfzam
ms.date: 08/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2021-08-30
ms.dyn365.ops.version: 10.0.23

---

# Apply prepayments to vendor invoices overview

[!include [banner](../includes/banner.md)]

This topic describes the capability for applying prepayments to vendor invoices automatically.

On the **Pending vendor invoice detailed** page, the invoice header displays four dates: the invoice received date, invoice date, posting date and due date. When a vendor invoice is created, the following dates are entered by default.

- **Invoice received date**: current system date.
- **Posting date**: current system date. 
- **Due date**: determined from posting date and payment term.

The invoice date is always initial, and you can change this date manually. If you do change this date, the date on **Due date** field will be recalculated based on the invoice date and the payment term.
Sometimes, vendor invoice could be in pending status for long time after the period close. When it’s ready for posting, the old posting date of past posting period is still used, which will not be possible since the period has been closed. As a result, AP clerk must manually change all the posting dates to the new posting period for all pending invoices created previously.
This feature provides capability to let system automatically adjust the posting date according to business needs. 

## Parameter for automatically adjusting vendor invoice posting date

You can let the system adjust the posting date automatically for vendor invoices. 

1.	Go to **Account payable > Setup > Account payable parameters**.
2.	Open the **Ledger and sales tax** tab.
3.	On the **Adjust posting date automatically** field, select one of the following options:

  - **No change**
    This is the default selction. When it is selected, the system won't change the posting date automatically during posting.
  - **Always change posting date to system date**
     This selection always automatically changes the posting date to the system date during posting.
  - **Change posting date to system date when posting date period is closed or on hold**
     This selection changes the posting date to new system date during posting only if the corresponding period of posting date is **Closed** or **On hold**.
  - **Change posting date to first day of new period when posting date period is closed or on hold**
     This selection changes the posting date to the first day of new open period only if the corresponding period is **Closed** or **On hold**.

## Impact of posting date change

When the posting date on a pending vendor invoice is changed, the results of that change are as follows:

- **Due date**
  If the **Invoice date** field is blank, the due date will be recalculated according to new posting date and payment terms. 
  If the **Invoice date** field was entered earlier, the posting date change won't affect the due date. 
  
- **Cash discount date** 
  If **Invoice date** is blank, then the new posting date is used to calculate the cash discount. 
  If **Invoice date** is previously entered, the cash discount won't be changed.
  
- **Exchange rate** 
   The exchange rate date is determined by the setting on the **Update vendor accounting using the invoice date** parameter on the **Accounts payable parameters** page (**Account payable > Setup > Account payable parameters > Invoice** tab).

   If this parameter is set to **Yes**, Invoice date is used nd the posting date change won't influence the exchange rate.

   If this parameter is set to **No**, the posting date is used to calculate the exchange rate. When the posting date is updated, accounting and reporting amounts are recalculated. As a result, matching validation needs to be performed again.

## Validation

Two other parameters on the **Invoice** tab (**Account payable > Setup > Account payable parameters > Invoice** tab) affect invoice processing.

   If the **Check the invoice number used** parameter is set to **Reject duplicates within fiscal year**, the system uses the posting date to check for duplicate invoices during invoice posting.

   If the **Require document date on vendor invoice** parameter is on, the **Invoice date on pending invoice header** field will be required. And if the Invoice date is later than the posting date, the system will display an error message.
