---
title: Sales tax applicability and sales tax group determination logic
description: Learn about the logic for determining sales tax applicability and sales tax groups in the tax feature setup, including an overview on matching logic.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 03/18/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Sales tax applicability and sales tax group determination logic

[!include [banner](../../includes/banner.md)]

This article explains the logic for determining sales tax applicability and sales tax groups in the tax feature setup.

## Matching logic

The applicability logic tries to match the condition that includes the most input fields. Each field that has a value has a *weight* of 10. A condition that has a higher total weight has a higher priority.

### Example

The following example shows how the matching logic works.

The **Tax group applicability** tab is configured as shown in the following table.

| Business process | Currency | Item code | Tax group | Weight |
|------------------|----------|-----------|-----------|--------|
| Purchase         | EUR      |           | TG\_A     | 20     |
| Purchase         | EUR      | D0001     | TG\_B     | 30     |

For the first line in the table, two input fields are set. Therefore, the line has a weight of 20. For the second line, three fields are set. Therefore, the line has a weight of 30.

When sales tax is calculated for a purchase order that has the EUR currency and item D0001, Tax Calculation uses the condition that has a higher weight. Therefore, it uses the second line in the table.

## Adjust execution sequence

You can adjust the execution sequence of the applicability rules that have equal weight.

### Example

The following example shows how the **Adjust execution sequence** button works.

The **Tax group applicability** tab is configured as shown in the following table.

| Business process | Currency | Item code | Tax group | Weight |
|------------------|----------|-----------|-----------|--------|
| Purchase         | EUR      | &nbsp;    | TG\_A     | 20     |
| Purchase         | &nbsp;   | D0001     | TG\_B     | 20     |

According to the matching logic, the rules in the table have equal weight. If you purchase item **D0001** with the transaction currency **EUR**, the first rule (Tax group **TG\_A**) applies.

Complete the following steps to adjust the rule that applies.

1. Select **Adjust execution sequence**.
1. Select the second rule, and then select **Move up**.
1. Select **Complete**.

Now, the second rule (Tax group **TG\_B**) is moved above the first one and applies first.

> [!NOTE]
> You can't move a rule above or under another rule that has a different **Weight**.

## Sales tax group and item sale tax group determination logic

When you create a document line on a business document, such as a sales order, purchase order, or vendor invoice, the system sets the **Sales tax group** and **Item sales tax group** fields to the values from the master data. Then, when tax is calculated, the system updates these fields according to the conditions that you configure in the Tax feature setup on the **Tax group applicability** and **Item tax group applicability** tabs.

If you don't configure an applicability rule for the tax group or item tax group in the Tax feature setup, Tax Calculation uses the default rules from the master data in Microsoft Dynamics 365 Finance.

> [!NOTE]
> You must create and maintain the sales tax group and item sales tax group in the Tax calculation feature.

## Override sales tax

You can update the tax groups that Tax Calculation determines without having to reconfigure the Tax feature. For example, you might need to update the tax groups because the rule is incorrectly set up, or because you need an exception to the rule. By setting the **Override sales tax** option to **Yes** on the line details page for a document line, you can select the required sales tax group and item sales tax group.

:::image type="content" source="../media/Pict1%20Override%20sales%20tax%20parameter.jpg" alt-text="Screenshot of the Override sales tax option set to Yes on the line details page for a document line.":::

The system calculates the tax codes based on the intersection of the tax codes that you define on the **Tax group** and **Item tax group** tabs in the Tax feature setup.
In Finance, the value of the **Source** field indicates that the system synchronizes the tax groups from the Tax feature setup.

:::image type="content" source="../media/Pict2%20Source%20field%20in%20Item%20sales%20tax%20group.jpg" alt-text="Screenshot of the Source field set to Tax calculation service for an item sales tax group on the Item sales tax groups page.":::

> [!NOTE]
> If you leave the **Sales tax group** or **Item sales tax group** field blank, and set the **Override sales tax** option to **Yes**, the system doesn't send the line to the Tax calculation service for processing.

The system adds the **Override sales tax** checkbox to the **Customer** and **Vendor** master data on the **Invoice and delivery** FastTab. The system also adds the checkbox to the Sales order, Purchase order, Free text invoice header, and to the line level of those documents.

The following process combines tax code determination logic with override sales tax:

#### Scenario 1: Override sales tax = Yes

The flow that combines tax code determination logic with override sales tax yes.

:::image type="content" source="../media/OverrideSalesTax_Yes.jpg" alt-text="Screenshot of the flow that combines tax code determination logic with override sales tax yes.":::

#### Scenario 2: Override sales tax = No and applicability rule can be matched

The flow that combines tax code determination logic with override sales tax no and matched applicability rules.

:::image type="content" source="../media/OverrideSalesTax_No1.jpg" alt-text="Screenshot of the flow that combines tax code determination logic with override sales tax no and matched applicability rules.":::

#### Scenario 3: Override sales tax = No and applicability rule can't be matched

The flow that combines tax code determination logic with override sales tax no and applicability rules mismatch.

:::image type="content" source="../media/OverrideSalesTax_No2.jpg" alt-text="Screenshot of the flow that combines tax code determination logic with override sales tax no and applicability rules mismatch.":::

### Update order lines

You can bulk update lines if you change the **Override sales tax** checkbox on the header level. You can also add this checkbox to the **Update order lines** parameters pages for Sales order, Sales quotation, and Purchase order.
For example, if you set the option to **Prompt**, when you change the **Override sales tax** checkbox on the header of the document, the dialog box opens. You can select whether the document lines should be updated.

> [!NOTE]
> Header-level and line-level charges inherit the **Override sales tax** option from the header or line of the document, respectively.
>
> Current limitation:
> When you update the **Override sales tax** checkbox on a header or line level, the respective charges don't inherit this checkbox if you already created the charges.

### Reverse charge applicability rules

For information about the configuration for reverse charge rules, see [Set up reverse charge rules](emea-reverse-charge.md#reverse-charge-rules).

When the document lines meet the reverse charge rules that you configure in Finance, the **Override sales tax** checkbox is set to **Yes** for the affected lines. The default value for **Sales tax group** comes from the **Purchase order sales tax group** or **Sales order sales tax group** field. You specify these fields on the **General ledger parameters** page, on the **Reverse charge** tab. For more information about these fields, see [Set up default parameters](emea-reverse-charge.md#set-up-default-parameters).

> [!NOTE]
> For reverse charges, you also need to create and maintain the sales tax groups and item sales tax groups in the Tax feature setup.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
