---
title: Create report-as-finished journal lines from a proposal (preview)
description: Learn how to automatically create report-as-finished journal lines for a production order by using a proposal.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: ProdJournalTransProd, ProdJournalTransProdCreateLines
ms.topic: how-to
ms.date: 10/15/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Create report-as-finished journal lines from a proposal (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The **Create lines** function helps you create lines in a report-as-finished journal without entering each line manually. Select a production order and a proposal, and the system creates a new journal with the lines that match the proposal. For example, you can create one line for each registered receipt or serialized finished product that's fully matched to its tracked components.

The function creates an unposted journal. Review the generated lines before you post the journal.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.50 or later.
- The feature named *(Preview) Create report as finished journal lines from a proposal* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- At least one production journal name with the *Report as finished* journal type must be set up. To review or create production journal names, go to **Production control** > **Setup** > **Production journal names**.

To use the *Fully matched serial numbers* proposal, the following additional requirements apply:

- The *Tracked components* feature must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- The **Enable tracked components** option must be set to *Yes* on the **Inventory and warehouse management parameters** page.
- The finished product must be serial-number controlled, and the applicable components must be configured for tracked components. For more information, see [Register and track batch/serial numbers for finished products and their components](tracked-components.md).

## Proposal options

The following table describes the available proposals.

| Proposal | Lines that are created |
|---|---|
| *Fully matched serial numbers* | One line for each finished-product serial number that you didn't report as finished and that fully matches all required tracked components. This option is available only when tracked components are enabled. |
| *Registered* | One line for each inventory dimension that has a registered receipt quantity for the production order. The line includes the registered quantity and inventory dimensions. |
| *Quantity* | One line for the quantity that you enter. The quantity must be greater than zero and can't exceed the remaining quantity on the production order. |
| *Remaining quantity* | One line for the full quantity that remains to be reported as finished. No line is created if no quantity remains. |
| *Full reversal* | Negative lines that reverse the quantities you already reported as finished. The system creates a line for each set of inventory dimensions used for the reported quantities. |

## Create journal lines

Follow these steps to create report-as-finished journal lines from a proposal:

1. Go to **Production control** > **Adjustments** > **Report as finished**.
1. On the Action Pane, select **Create lines**.
1. In the **Create lines** dialog, set the following fields:

    - **Production** – Select the production order to create lines for. You can select an order that has a status of *Released*, *Started*, or *Reported as finished*. If you open the dialog from a journal or line that has a production order, the order is selected by default.
    - **Report as finished journal** – Select a journal name that has the *Report as finished* journal type. The standard report-as-finished journal name for the selected production order is selected by default.
    - **Include co/by products** – Select this option to also create lines for co-products and by-products. This option is available only if the selected production order has co-products or by-products, and it's selected by default.
    - **Proposal** – Select the proposal to use. For information about each value, see the [Proposal options](#proposal-options) section.
    - **Good quantity** – If you selected the *Quantity* proposal, enter the quantity to report. The field initially shows the remaining quantity for the production order.
    - **Catch weight good quantity** – If the finished product is a catch-weight item and you selected the *Quantity* proposal, enter the catch-weight quantity. When you change this value, the system calculates the corresponding **Good quantity**.

1. Select **OK**.

The system creates a new report-as-finished journal and shows a message that identifies the journal number and the number of lines created. If no lines match the selected proposal, the system doesn't create a journal and shows a warning.

> [!NOTE]
> The function creates a new journal. It doesn't add lines to a report-as-finished journal that's currently open.

## Review and post the journal

Before you post the generated journal, open it and verify the following information:

- The production order, item, quantity, and inventory dimensions on each line.
- The serial numbers and tracked-component matches for lines created by using the *Fully matched serial numbers* proposal.
- The negative quantities and inventory dimensions on reversal lines.
- The co-product and by-product lines, if you selected **Include co/by products**.

When the lines are correct, select **Post** on the Action Pane. The standard validations and posting rules for report-as-finished journals apply.

## Related information

- [Report production orders as finished](report-production-orders-as-finished.md)
- [Production feedback](production-feedback.md)
- [Register and track batch/serial numbers for finished products and their components](tracked-components.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
