---
# required metadata

title: Vendor invoice dates
description: This article describes the dates that appear on vendor invoices. It also explains how to automatically adjust the posting date.
author: sunfzam
ms.date: 3/14/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2021-08-30
ms.dyn365.ops.version: 10.0.23

---

# Vendor invoice dates

[!include [banner](../includes/banner.md)]

This article describes the dates that appear on vendor invoices. 

On the **Pending vendor invoice detailed** page, the invoice header shows four dates: **Invoice received date**, **Invoice date**, **Posting date**, and **Due date**. When a vendor invoice is created, the following dates are entered by default:

- **Invoice received date** – This field is set to the current system date.
- **Posting date** – This field is set to the current system date. 
- **Due date** – The date in this field is calculated based on the posting date and payment terms.
- **Invoice date** – By default, this field is blank. However, you can enter a value as you require. In that case, the date in the **Due date** field is recalculated based on the invoice date and the payment terms.

Sometimes, a vendor invoice might be in a pending state for a long time after the period close. When it's ready for posting, the old posting date of the past posting period is still used. However, that period has now been closed. Therefore, an Accounts payable (AP) clerk must manually change all the posting dates to the new posting period for all pending invoices that were previously created.

The feature that is described in this article lets you automatically adjust the posting date according to business requirements.

## Parameter for automatically adjusting the vendor invoice posting date

Follow these steps to automatically adjust the posting date for vendor invoices.

1.	Go to **Account payable \> Setup \> Account payable parameters**.
2.	On the **Ledger and sales tax** tab, in the **Adjust posting date automatically** field, select one of the following values:

    - **No change** – The system doesn't automatically change the posting date during posting. This value is selected by default.
    - **Always change posting date to system date** – The posting date is automatically changed to the system date during posting.
    - **Change posting date to system date when posting date period is closed or on hold** – The posting date is  automatically changed to the system date during posting, but only if the corresponding period of the posting date has a status of **Closed** or **On hold**.
    - **Change posting date to first day of new period when posting date period is closed or on hold** – The posting date is changed to the first day of the new open period, but only if the corresponding period of the posting date has a status of **Closed** or **On hold**.
3.  The **Adjust invoice posting date to next year’s open period** is only enabled when  **Adjust posting date automatically** is **NOT** set **No change**. This controls whether it allows the invoice posting when the posting date is automatically adjusted in a new fiscal year. The following values are avaiable for selection:
    - Block with error, if you want to stop invoice posting with an error that the posting date can’t be updated.This value is selected by default.
    - Allowed with warning, if you want to allow invoice posting with a warning and the posting date of the invoice updated to the next period’s open period.
  
> [!NOTE]
> The **Adjust the posting date automatically** only covers the Vendor invoice, Invoice register journal, Invoice journal. 
 
## Impact of posting date changes

When the posting date on a pending vendor invoice is changed, the change has the following effects:

- **Due date**

    - If the **Invoice date** field is blank, the due date is recalculated based on the new posting date and payment terms.
    - If the **Invoice date** field was previously set, the posting date change doesn't affect the due date.

- **Cash discount date**

    - If the **Invoice date** field is blank, the new posting date is used to calculate the cash discount.
    - If the **Invoice date** field was previously set, the cash discount isn't changed.
      
> [!NOTE]
> For the invoice register or invoice journals, the due date and cash discount date isn't recalculated based on the new posting date and payment terms.
      
## Exchange rate date

The exchange rate date is determined by the **Default exchange rate date** option on the **General** tab of the **Accounts payable parameters** page (**Account payable \> Setup \> Account payable parameters**).

- The **Posting date** is the default value for the **Default exchange rate date**. When the **Posting date** changes, this affects the exchange rate, and accounting and reporting amounts are recalculated. Matching validation must be done again.
- If the **Default exchange rate date** is set to **Document date**, the **Invoice date** is used, and the change doesn't affect the exchange rate. 

> [!NOTE]
> This parameter is only enabled when the **Update vendor accounting using the invoice date** parameter is disabled. If this parameter is enabled, it will use the **Invoice date** as **Accounting date** to post the invoice and it determines the exchange rate.
> There is no fixed exchange rate setting in the **Invoice register** and **Invoice journal line** level. The fixed exchange rate is set on the **Invoice register** or **Invoice journal header** > **Setup**.

## Validation

Two other fields on the **Invoice** tab of the **Accounts payable parameters** page (**Account payable \> Setup \> Account payable parameters**) affect invoice processing:

- If the **Check the invoice number used** field is set to **Reject duplicates within fiscal year**, the posting date will be used to check for duplicate invoices during invoice posting.
- If the **Require document date on vendor invoice** field is set to **Error option**, the **Invoice date on pending invoice header** field is required. If the invoice date is later than the posting date, an error message will be displayed.
