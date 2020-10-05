---
# required metadata

title: Invoice issue deadline (GBL)
description: This topic provides information about how to calculate the due dates for issuing customer invoices .
author: v-oloski
manager: Annbe
ms.date: 10/06/2020
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
ms.search.region: GBL
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2020-07-03
ms.dyn365.ops.version: 10.0.13

---

# Invoice issue deadline

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic explains how to configure Dynamics 365 Finance so that it complies with legal requirements for the invoice issue deadline. For example, legislation can require that an invoice be issued no later than the fifteenth day of the month following the sale. 


## Prerequisites

In the **Feature management** workspace, turn on the **Invoice issue deadline availability** feature. This feature is available for all countries from 10.0.15 version or later.

For more information about how to turn on features, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

> [!NOTE]
> This feature is the same as the feature for European Union (EU) countries which is delivered out-of-the-box. For more information, see [Invoice issue deadline](emea-invoice-issue-deadline.md).

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
6. On the line for the new record, in the **Party country/region** field, select a country or region, and then, in the **Country/region type** field, select the value. For example, **Domestic**.

    ![Foreign trade parameters page](media/gcc-invoice-issue-deadline-Foreign-trade-parameters.jpg)

7. Go to **Accounts receivable** > **Setup** > **Set up calculation for invoice issue date** or **Accounts payable** > **Setup** > **Set up calculation for invoice issue date**.
8. On the **Set up calculation for invoice issue due date** page, create a record.
9. In the **Country/region type** field, select a value, and in the **Date interval code** field, enter a value. The invoice issue deadline validation is applicable to the packing slips/product receipts which were posted with the domestic address.  

    ![Set up calculation for invoice issue due date page](media/gcc-invoice-issue-deadline-calculation-for-invoice-issue-deadline.jpg)

10. Go to **Accounts receivable** \> **Setup** \> **Parameters**.
11. On the **Accounts receivable parameters** page, on the **Updates** tab, on the **Invoice date control** FastTab, in the **Invoice date control** field, select one of the following values:

    - **None** – Date control isn't run.
    - **Warning** – The invoice is posted, but a warning message appears afterward.
    - **Error** – The invoice isn't posted, and an error message appears.

    > [!NOTE] 
    > This validation (**Warning** and **Error**) is applicabe to sales invoices which posted on the base of packing slip. 

 ![Accounts receiveble parameters](media/gcc-invoice-issue-deadline-ar-parameters.jpg)

Based on the settings, the system enters a value in the **Invoice issue due date** field in the packing slip journal and product receipt journal. 
You can view all the packing slips that aren't yet invoiced by going to **Sales and marketing** \> **Sales orders** \> **Order shipping** \> **Packing slip not invoiced**. 

You can view all the product receipts that aren't yet invoiced by going to **Procurement and sourcing** \> **Purchase orders** \> **Receiving products** \> **Product receipt not invoiced**

> [!NOTE] 
> If you set the **Invoice date control** field on the **Accounts receivable parameters** page to **None**, the **Invoice issue due date** field in the packing slip journal is left blank.
