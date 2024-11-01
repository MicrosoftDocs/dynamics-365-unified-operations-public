---
title: Calculate sales totals when prices include sales tax
description: Access example scenarios that show how sales totals are calculated when prices include and exclude sales tax, including prerequisites.
author: adpattanaik
ms.author: adpattanaik
ms.topic: how-to
ms.date: 12/11/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Calculate sales totals when prices include sales tax

[!include [banner](../includes/banner.md)]

This article provides example scenarios that show how sales totals and discounts are calculated when prices include and exclude sales tax.

## Prerequisites

### Enable sample data

To work through the example scenarios by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

### Adjust the tax rate

The example scenarios in this article assume the following setup in Microsoft Dynamics 365 Supply Chain Management:

- A sales tax code that's named *AV\_CAST* has a tax rate of 50 percent.
- A sales tax group that's named *CA* includes sales tax code *AV\_CAST*.
- An item sales tax group that's named *AU/VI* includes sales tax code *AV\_CAST*.

The USMF sample data includes these tax codes and groups, but it uses a different tax rate for the sales tax code. To adjust the tax rate to 50 percent, follow these steps.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. In the list pane, select sales tax code *AV\_CAST* to open it.
1. On the Action Pane, on the **Sales tax code** tab, select **Values**.
1. For the row where the **Sales tax code** field is set to *AV_CAST*, set the **Value** field to *50*.

## Example scenario 1: Sales total calculation when prices exclude sales tax

Follow these steps to see how sales totals are calculated when prices exclude sales tax.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Create a sales order for customer account *US-001*.
1. Add a sales order line, and set the following values for it:

    - **Item number:** *1000*
    - **Site:** *1*
    - **Warehouse:** *11*
    - **Quantity:** *1*
    - **Unit price:** *1000*

1. While the new sales order line is still selected, on the **Line details** FastTab, on the **Setup** tab, set the following values:

    - **Item sales tax group:** *AU/VI*
    - **Sales tax group:** *CA*

1. On the Action Pane, on the **Sales order** tab, select **Totals**.
1. In the **Totals** dialog box, notice that your tax settings produce the following values:

    - **Invoice amount:** *1500*
    - **Subtotal amount:** *1000*
    - **Sales tax:** *500* (= *Subtotal amount* &times; 50%)

1. Select **OK** to close the dialog box.
1. Edit the sales line so that the **Discount** field is set to *100*.
1. Open the **Totals** dialog box again, and notice the following new values:

    - **Invoice amount:** *1350* (= *Unit price* &minus; *Discount*)
    - **Subtotal amount:** *900* (= *Unit price* &minus; *Discount*)
    - **Sales tax:** *450* (= *Subtotal amount* &times; 50%)
    - **Line discount:** *100*

## Example scenario 2: Sales total calculation when prices include sales tax

Follow these steps to see how sales totals are calculated when prices include sales tax.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Create a sales order for customer account *US-001*.
1. On the **Header** tab of the new sales order, on the **Setup** FastTab, set the **Prices include sales tax** option to *Yes*.
1. On the **Lines** tab, add a sales order line, and set the following values for it:

    - **Item number:** *1000*
    - **Site:** *1*
    - **Warehouse:** *11*
    - **Quantity:** *1*
    - **Unit price:** *1000*

1. While the new sales order line is still selected, on the **Line details** FastTab, on the **Setup** tab, set the following values:

    - **Item sales tax group:** *AU/VI*
    - **Sales tax group:** *CA*

1. On the Action Pane, on the **Sales order** tab, select **Totals**.
1. In the **Totals** dialog box, notice that your tax settings produce the following values:

    - **Invoice amount:** *1000*
    - **Subtotal amount:** *666.67* (= *Invoice amount* &minus; *Sales tax*)
    - **Sales tax:** *333.33* (= *Subtotal amount* &times; 50%)

1. Select **OK** to close the dialog box.
1. Edit the sales line so that the **Discount** field is set to *100*.
1. Open the **Totals** dialog box again, and notice the following new values:

    - **Invoice amount:** *900* (= *Unit price* &minus; *Discount*)
    - **Subtotal amount:** *600* (= *Invoice amount* &minus; *Sales tax*)
    - **Sales tax:** *300* (= *Subtotal amount* &times; 50%)
    - **Line discount:** *66.67* (= *Original subtotal amount* \[666.67\] &minus; *New subtotal amount* \[600\])

    Because tax is included in the price, the line discount doesn't equal 100. Instead, it's calculated as the difference between the gross amount without tax (calculated without the discount) and the line amount without tax (calculated to include the discount).

1. Select **OK** to close the dialog box.

    The remaining steps in this example show how to apply a manual adjustment to the sales tax amount.

1. On the Action Pane, on the **Sell** tab, select **Sales tax**.
1. In the **Temporary sales tax transactions** dialog box, select the **Adjustment** tab to view the actual sales tax amount.
1. For the row where the **Sales tax code** field is set to *AV_CAST*, follow these steps:

    1. Set the **Actual sales tax amount** field to *400*.
    2. Make sure that the **Override calculated sales tax** checkbox is selected. (It should be automatically selected when you change the **Actual sales tax amount** value.)

1. Select **OK** to close the dialog box.
1. Open the **Totals** dialog box again, and notice the following new values:

    - **Invoice amount:** *900* (= *Unit price* &minus; *Discount*)
    - **Subtotal amount:** *500* (= *Invoice amount* &minus; *Sales tax*)
    - **Sales tax:** *400* (manually adjusted amount)
    - **Line discount:** *166.67* (= *Original subtotal amount* \[666.67\] &minus; *New subtotal amount* \[500\])

    The same logic that was used earlier is used to calculate the discount. The discount is the difference between the gross amount without tax (ignoring the manually adjusted tax) and the line amount without tax (calculated to include a discount of 100 and the new manually adjusted tax).
