---
# required metadata

title: Vendor invoice dates
description: This topic describes the dates that appear on vendor invoices. It also explains how to set up the system so that it automatically adjusts the posting date.
author: sunfzam
ms.date: 2/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2021-08-30
ms.dyn365.ops.version: 10.0.23

---

# Vendor invoice dates

[!include [banner](../includes/banner.md)]

This topic describes the dates that appear on vendor invoices. It also explains how to set up the system so that it automatically adjusts the posting date.

On the **Pending vendor invoice detailed** page, the invoice header shows four dates: the invoice received date, the invoice date, the posting date, and the due date. When a vendor invoice is created, the following dates are entered by default:

- **Invoice received date** – This field is set to the current system date.
- **Posting date** – This field is set to the current system date. 
- **Due date** – The date in this field is calculated based on the posting date and payment terms.
- **Invoice date** – By default, this field is blank. However, you can enter a value as you require. In that case, the date in the **Due date** field is recalculated based on the invoice date and the payment terms.

Sometimes, a vendor invoice might be in a pending state for a long time after the period close. When it's ready for posting, the old posting date of the past posting period is still used. However, that period has now been closed. Therefore, an Accounts payable (AP) clerk must manually change all the posting dates to the new posting period for all pending invoices that were previously created.

The feature that is described in this topic lets you set up the system so that it automatically adjusts the posting date according to business requirements.

## Parameter for automatically adjusting the vendor invoice posting date

Follow these steps to enable the system to automatically adjust the posting date for vendor invoices.

1.	Go to **Account payable \> Setup \> Account payable parameters**.
2.	On the **Ledger and sales tax** tab, in the **Adjust posting date automatically** field, select one of the following values:

    - **No change** – The system doesn't automatically change the posting date during posting. This value is selected by default.
    - **Always change posting date to system date** – The system automatically changes the posting date to the system date during posting.
    - **Change posting date to system date when posting date period is closed or on hold** – The system changes the posting date to the system date during posting, but only if the corresponding period of the posting date has a status of **Closed** or **On hold**.
    - **Change posting date to first day of new period when posting date period is closed or on hold** – The system changes the posting date to the first day of the new open period, but only if the corresponding period of the posting date has a status of **Closed** or **On hold**.

> [!NOTE]
> If the new posting date that was automatically adjusted is in a new fiscal year, the posting date of the invoice will not be updated. The user will receive an error "The fiscal year has changed. Please check and reenter the posting date." The invoice posting date must be updated to the new fiscal year date in order to post.

## Impact of posting date changes

When the posting date on a pending vendor invoice is changed, the change has the following effects:

- **Due date**

    - If the **Invoice date** field is blank, the due date is recalculated based on the new posting date and payment terms.
    - If the **Invoice date** field was previously set, the posting date change doesn't affect the due date.

- **Cash discount date**

    - If the **Invoice date** field is blank, the new posting date is used to calculate the cash discount.
    - If the **Invoice date** field was previously set, the cash discount isn't changed.

- **Exchange rate** – The exchange rate date is determined by the setting of the **Update vendor accounting using the invoice date** option on the **Invoice** tab of the **Accounts payable parameters** page (**Account payable \> Setup \> Account payable parameters**).

    - If this option is set to **Yes**, the invoice date is used, and the posting date change doesn't affect the exchange rate.
    - If this option is set to **No**, the posting date is used to calculate the exchange rate. When the posting date is updated, accounting and reporting amounts are recalculated. Therefore, matching validation must be done again.

## Validation

Two other fields on the **Invoice** tab of the **Accounts payable parameters** page (**Account payable \> Setup \> Account payable parameters**) affect invoice processing:

- If the **Check the invoice number used** field is set to **Reject duplicates within fiscal year**, the system uses the posting date to check for duplicate invoices during invoice posting.
- If the **Require document date on vendor invoice** field is set to **Error option**, the **Invoice date on pending invoice header** field is required. If the invoice date is later than the posting date, the system shows an error message.
