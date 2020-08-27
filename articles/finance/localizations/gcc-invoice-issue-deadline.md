---
# required metadata

title: Invoice issue deadline (GCC)
description: This topic provides information about how to calculate the due dates for issuing customer invoices in Gulf Cooperation Council (GCC) countries.
author: v-oloski
manager: Annbe
ms.date: 08/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: GCC
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2020-07-03
ms.dyn365.ops.version: 10.0.13

---

# Invoice issue deadline (GCC)

[!include [banner](../includes/banner.md)]

<table>
<tbody>
<tr>
<td><strong>Country/region</strong></td>
<td>Gulf Cooperation Council (GCC) countries include Bahrain, Kuwait, Oman, Qatar, Saudi Arabia, and United Arab Emirates.</td>
</tr>
<tr>
<td><strong>Feature title</strong></td>
<td>Invoice issue deadline</td>
</tr>
<tr>
<td><strong>Feature reference</strong></td>
<td>GCC-00001</td>
</tr>
<tr>
<td><strong>Blueprint classification</strong></td>
<td>INVOICING: Invoice processing</td>
</tr>
<tr>
<td><strong>Configurable</strong></td>
<td>No</td>
</tr>
<tr>
<td><strong>Internal reference</strong></td>
<td><a href="https://vstsmbs.visualstudio.com/web/wi.aspx?pcguid=bf66efc0-4097-46c2-80a1-746442695fc7&id=3982487">Compliance 3982487</a></td>
</tr>
<tr>
<td><strong>First available</strong></td>
<td>2020 Release Wave 2 (Monthly update 10.0.13)</td>
</tr>
<tr>
<td><strong>Feature update history</strong></td>
<td></td>
</tr>
<tr>
<td><strong>Feature management</strong></td>
<td>Yes. See the <a href="#turn-on-the-feature">Turn on the feature</a> section.</td>
</tr>
<tr>
<td><strong>Business need</strong></td>
<td>The tax invoice issue date must comply with the GCC legal requirements and should be no later than the data that is set in the legislation.</td>
</tr>
<tr>
<td><strong>Feature description</strong></td>
<td>This topic explains how to configure Microsoft Dynamics 365 Finance so that it complies with GCC legal requirements for the tax invoice issue deadline.</td>
</tr>
</tbody>
</table>

## Prerequisites

The primary address of the legal entity must be in a GCC country. GCC countries include Bahrain, Kuwait, Oman, Qatar, Saudi Arabia, and United Arab Emirates.

## Turn on the feature

In the **Feature management** workspace, turn on the **Invoice issue deadline availability for additional countries** feature.

For more information about how to turn on features, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

> [!NOTE]
> This feature is the same as the feature for European Union (EU) countries. For more information, see [Invoice issue deadline](emea-invoice-issue-deadline.md).

## Setup

Follow these steps to set up the invoice issue deadline functionality.

1. Go to **General ledger** \> **Ledger setup** \> **Date intervals**.
2. On the **Date intervals** page, create a date interval.
3. On the **General** FastTab, in the **Interval start** and **Interval end** sections, set the fields to appropriate values.

    ![Date intervals page](media/gcc-invoice-issue-deadline-date-interval.jpg)

    > [!NOTE]
    > The preceding illustration shows an interval of 15 days. If the date interval is set up in this way, the deadline for issuing the invoice will be the fifteenth day of the month after the month when the packing slip is issued. If you leave the **To date period type** and **To date Start/End** fields in the **Interval end** section blank, the deadline for issuing the invoice will be the fifteenth day after the packing slip is issued.

4. Go **Tax** \> **Setup** \> **Foreign trade**.
5. On the **Foreign trade parameters** page, on the **Country/region properties** tab, select **New**.
6. On the line for the new record, in the **Party country/region** field, select a country or region, and then, in the **Country/region type** field, select **Domestic**.

    ![Foreign trade parameters page](media/gcc-invoice-issue-deadline-Foreign-trade-parameters.jpg)

7. Go to (Need navigation path to the page - the previous navigation is incorrect).
8. On the **Set up calculation for invoice issue due date** page, create a record.

    ![Set up calculation for invoice issue due date page](media/gcc-invoice-issue-deadline-calculation-for-invoice-issue-deadline.jpg)

9. Go to **Accounts receivable** \> **Setup** \> **Parameters**.
10. On the **Accounts receivable parameters** page, on the **Updates** tab, on the **Invoice date control** FastTab, in the **Invoice date control** field, select one of the following values:

    - **None** – Date control isn't run.
    - **Warning** – The invoice is posted, but a warning message appears afterward.
    - **Error** – The invoice isn't posted, and an error message appears.

    ![Accounts receivable parameters page](media/gcc-invoice-issue-deadline-ar-parameters.jpg)

Based on the settings, the system enters a value in the **Invoice issue due date** field in the packing slip journal. You can view all the packing slips that aren't yet invoiced by going to **Sales and marketing** \> **Sales orders** \> **Order shipping** \> **Packing slip not invoiced**. To review packing slips from a sales order, go to **Sales and marketing** \> **Sales orders** \> **Order shipping** \> **Packing slip**. 

> [!NOTE] 
> If you set the **Invoice date control** field on the **Accounts receivable parameters** page to **None**, the **Invoice issue due date** field in the packing slip journal is left blank.
