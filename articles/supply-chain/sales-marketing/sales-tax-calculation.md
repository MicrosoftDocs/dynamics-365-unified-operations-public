---
title: Calculating sales totals when prices include sales tax
description: This article provides example scenarios that illustrate how sales totals are calculated when prices include sales tax.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 12/08/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Calculating sales totals when prices include sales tax

[!include [banner](../includes/banner.md)]

This article provides example scenarios that illustrate how sales totals and discounts are calculated when prices include sales tax compared to when prices don't include sales tax.

## Prerequisites

The example scenarios in this article assume the following setup in Supply Chain Management:

- Sales tax code *AV_CAST* with a tax rate of 50%
- Sales tax group *CA*, which includes sales tax code *AV_CAST*
- Item sales tax group *ALL*, which includes sales tax code *AV_CAST*

## Example scenario 1: Sales total calculation when prices don't include sales tax

Follow these steps to see how sales totals are calculated when prices don't include sales tax.

1. Create a sales order and add a sales order line with the following settings:
    - An appropriate **Item**, **Site**, **Warehouse**, and **Quantity**
    - A **Unit price** of *1000*.
    - An **Item sales tax group** of *ALL*.
    - A **Sales tax group** of *CA*.
1. On the Action Pane, open the **Sales order** tab and select **Totals**.
1. The **Totals** dialog opens. Note the following values, which result from your tax settings:
    - **Invoice amount:** *1500*
    - **Subtotal amount:** *1000*
    - **Sales tax:** *500* (Subtotal amount &times; 50%)
1. Select **OK** to close the dialog.
1. Edit the sales line to set **Discount** to *100*. <!-- KFM: This field was locked for me in USMF. Are we missing some steps here? -->
1. Open the **Totals** dialog again and note the following new values:
    - **Invoice amount:** *1350* (Unit price &minus; Discount)
    - **Subtotal amount:** *900* (Unit price &minus; Discount)
    - **Sales tax:** *450* (Subtotal amount &times; 50%)
    - **Line discount:** *100*

## Example scenario 2: Sales total calculation when prices include sales tax

Follow these steps to see how sales totals are calculated when prices include sales tax.

1. Create a new sales order.
1. Go to the **Header** tab for the sales order, expand the **Setup** FastTab and set **Prices include sales tax** to *Yes*.
1. Go back to the **Lines** tab and add a sales order line with the following settings:
    - An appropriate **Item**, **Site**, **Warehouse**, and **Quantity**
    - A **Unit price** of *1000*.
    - An **Item sales tax group** of *ALL*.
    - A **Sales tax group** of *CA*.
1. On the Action Pane, open the **Sales order** tab and select **Totals**.
1. The **Totals** dialog opens. Note the following values, which result from your tax settings:
    - **Invoice amount:** *1000*
    - **Subtotal amount:** *666.67* (Invoice amount &minus; Sales tax)
    - **Sales tax:** *333.33* (Subtotal amount &times; 50%)
1. Edit the sales line to set **Discount** to *100*. <!-- KFM: This field was locked for me in USMF. Are we missing some steps here? -->
1. Open the **Totals** dialog again and note the following new values:
    - **Invoice amount:** *900* (Unit price &minus; Discount)
    - **Subtotal amount:** *600* (Invoice amount &minus; Sales tax)
    - **Sales tax:** *300* (Subtotal amount &times; 50%)
    - **Line discount:** *66.67* (Original subtotal amount (666.67) &minus; New subtotal amount (600))

    Because tax is included in the price, the line discount doesn't equal 100 but is calculated as the difference between the gross amount without tax (calculated without the discount) and the line amount without tax (calculated to include the discount).

1. Suppose now that you need to apply a manual adjustment to the sales tax amount. On the Action Pane, open the **Sell** tab and select **Sales tax**.
1. The **Temporary sales tax transactions** dialog opens. For the row with a **Sales tax code** of *AV_CAST*, do the following: <!-- KFM: Please confirm this step and the following list. I think this is what you mean. -->
    - Set **Actual sales tax amount** to *400*.
    - Select the **Override calculated sales tax** check box*.
1. Select **OK** to close the dialog.
1. Open the **Totals** dialog again and note the following new values:
    - **Invoice amount:** *900* (Unit price &minus; Discount)
    - **Subtotal amount:** *500* (Invoice amount &minus; Sales tax)
    - **Sales tax:** *400* (Manually adjusted amount)
    - **Line discount:** *166.67* (Original subtotal amount (666.67) &minus; New subtotal amount (500))

    The discount (calculated using the same logic as previously) is the difference between gross amount without tax (ignoring the manually adjusted tax) and the line amount without tax (calculated including a discount of 100 and the new manually adjusted tax).
