---
title: Vendor invoice dates
description: Learn about the dates that appear on vendor invoices. It also explains how to automatically adjust the posting date.
author: sunfzam
ms.author: shpandey
ms.topic: article
ms.date: 7/28/2026
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

On the **Pending vendor invoice detailed** page, the invoice header shows four dates: **Invoice received date**, **Invoice date**, **Posting date**, and **Due date**. When you create a vendor invoice, the system enters the following dates by default:

- **Invoice received date** – The system sets this field to the current date.
- **Posting date** – The system sets this field to the current date.
- **Due date** – The system calculates this date based on the posting date and payment terms.
- **Invoice date** – This field is blank by default. However, you can enter a value as needed. When you enter a value, the system recalculates the **Due date** based on the invoice date and the payment terms.

Sometimes, a vendor invoice remains in a pending state for a long time after the period close. When it's ready for posting, the process uses the old posting date of the past posting period. However, that period is now closed. Therefore, an Accounts payable (AP) clerk must manually change all the posting dates to the new posting period for all pending invoices that were previously created.

The feature described in this article automatically adjusts the posting date according to business requirements.

## Parameter for automatically adjusting the vendor invoice posting date

Follow these steps to automatically adjust the posting date for vendor invoices.

1. Go to **Account payable \> Setup \> Account payable parameters**.
1. On the **Ledger and sales tax** tab, in the **Adjust invoice posting date automatically** field, select one of the following values:

    - **No change** – The posting date isn't automatically changed during posting. This value is selected by default.
    - **Always change posting date to system date** – The posting date is automatically changed to the system date during posting.
    - **Change posting date to system date when posting date period is closed or on hold** – The posting date is automatically changed to the system date during posting, but only if the corresponding period of the posting date has a **Closed** or **On hold** status.
    - **Change posting date to first day of new period when posting date period is closed or on hold** – The posting date is changed to the first day of the new open period, but only if the corresponding period of the posting date has a **Closed** or **On hold** status.
1. The **Adjust invoice posting date to next year’s open period** option is only enabled when you set **Adjust invoice posting date automatically** to a value other than **No change**. This option controls if invoice posting automatically adjusts the posting date in a new fiscal year. Select from the following values:
    - **Block with error** - if you want to stop invoice posting with an error that the posting date can’t be updated. This value is selected by default.
    - **Allowed with warning** - if you want to allow invoice posting with a warning and update the posting date of the invoice to the next period’s open period.
  
> [!NOTE]
> The **Adjust the invoice posting date automatically** setting only affects the posting date adjustments in Vendor invoice, Invoice register journal, and Invoice journal.

## Impact of posting date changes

When you change the posting date on a pending vendor invoice, the change affects the following fields:

- **Due date**

  - If the **Invoice date** field is blank, the system recalculates the due date based on the new posting date and payment terms.
  - If the **Invoice date** field is set, the posting date change doesn't affect the due date.

- **Cash discount date**

  - If the **Invoice date** field is blank, the system uses the new posting date to calculate the cash discount.
  - If the **Invoice date** field is set, the cash discount isn't changed.

> [!NOTE]
> For the invoice register or invoice journals, the system doesn't recalculate the due date and cash discount date based on the new posting date and payment terms.

## Exchange rate date

The **Default exchange rate date** field on the **General** tab of the **Accounts payable parameters** page (**Account payable > Setup > Account payable parameters**) determines the exchange rate date.

- The **Posting date** is the default value for the **Default exchange rate date** field. When the **Posting date** changes, it affects the exchange rate, and the system recalculates accounting and reporting amounts. You must complete matching validation again.
- If you set the **Default exchange rate date** to **Document date**, the system uses the **Invoice date**, and the change doesn't affect the exchange rate.

> [!NOTE]
> You can enable this parameter only when the **Update vendor accounting using the invoice date** parameter is disabled. If you enable this parameter, the system uses the **Invoice date** as the **Accounting date** to post the invoice and it determines the exchange rate.
> There's no fixed exchange rate setting at the **Invoice register** and **Invoice journal line** levels. Set the fixed exchange rate on the **Invoice register** or **Invoice journal header** > **Setup**.

## Validation

Two other fields on the **Invoice** tab of the **Accounts payable parameters** page affect invoice processing:

- If you set the **Check the invoice number used** field to **Reject duplicates within fiscal year**, the system uses the posting date to check for duplicate invoices during invoice posting.
- If you set the **Require document date on vendor invoice** field to **Error option**, the **Invoice date on pending invoice header** field is required. If the invoice date is later than the posting date, the system displays an error message.
