---
title: Vendor invoice dates
description: Learn about the dates that appear on vendor invoices. It also explains how to automatically adjust the posting date.
author: sunfzam
ms.author: shpandey
ms.topic: article
ms.date: 3/14/2024
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-08-30
ms.search.form: VendParameters
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

The feature that is described in this article automatically adjusts the posting date according to business requirements.

## Parameter for automatically adjusting the vendor invoice posting date

Follow these steps to automatically adjust the posting date for vendor invoices.

1.	Go to **Account payable \> Setup \> Account payable parameters**.
2.	On the **Ledger and sales tax** tab, in the **Adjust invoice posting date automatically** field, select one of the following values:

    - **No change** – The posting date isn't automatically changed during posting. This value is selected by default.
    - **Always change posting date to system date** – The posting date is automatically changed to the system date during posting.
    - **Change posting date to system date when posting date period is closed or on hold** – The posting date is automatically changed to the system date during posting, but only if the corresponding period of the posting date has a **Closed** or **On hold** status.
    - **Change posting date to first day of new period when posting date period is closed or on hold** – The posting date is changed to the first day of the new open period, but only if the corresponding period of the posting date has a **Closed** or **On hold** status.
3.  The **Adjust invoice posting date to next year’s open period** is only enabled when **Adjust invoice posting date automatically** option is **NOT** set **No change**. This controls if invoice posting automatically adjusts the posting date in a new fiscal year. The following values are available for selection:
    - **Block with error** - if you want to stop invoice posting with an error that the posting date can’t be updated. This value is selected by default.
    - **Allowed with warning** - if you want to allow invoice posting with a warning and update the posting date of the invoice to the next period’s open period.
  
> [!NOTE]
> The **Adjust the invoice posting date automatically** will only affect the posting date adjustments in Vendor invoice, Invoice register journal, Invoice journal. 
 
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

The exchange rate date is determined by the **Default exchange rate date** field on the **General** tab of the **Accounts payable parameters** page (**Account payable \> Setup \> Account payable parameters**).

- The **Posting date** is the default value for the **Default exchange rate date** field. When the **Posting date** changes, this affects the exchange rate, and accounting and reporting amounts are recalculated. Matching validation must be done again.
- If the **Default exchange rate date** is set to **Document date**, the **Invoice date** is used, and the change doesn't affect the exchange rate. 

> [!NOTE]
> This parameter is only enabled when the **Update vendor accounting using the invoice date** parameter is disabled. If this parameter is enabled, the **Invoice date** is used as the **Accounting date** to post the invoice and it determines the exchange rate.
> There is no fixed exchange rate setting in the **Invoice register** and **Invoice journal line** level. The fixed exchange rate is set on the **Invoice register** or **Invoice journal header** > **Setup**.

## Validation

Two other fields on the **Invoice** tab of the **Accounts payable parameters** page affect invoice processing:

- If the **Check the invoice number used** field is set to **Reject duplicates within fiscal year**, the posting date is used to check for duplicate invoices during invoice posting.
- If the **Require document date on vendor invoice** field is set to **Error option**, the **Invoice date on pending invoice header** field is required. If the invoice date is later than the posting date, an error message is displayed.
