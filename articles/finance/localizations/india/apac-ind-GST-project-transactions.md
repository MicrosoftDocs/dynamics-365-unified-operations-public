---
title: Goods and Service Tax (GST) project transactions
description: Learn about transactions for Goods and Service Tax (GST) projects, including processes for creating project categories and project quotations.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-07-02
ms.dyn365.ops.version: 7.3.1
---

# Goods and Service Tax (GST) project transactions

[!include [banner](../../includes/banner.md)]

## Create a project category

1. Go to **Project management and accounting** > **Setup** > **Categories** > **Project categories**.
1. On the **Project** FastTab, in the **Service accounting code** field, select a value.
1. Close the page.

## Create a project quotation

1. Go to **Project management and accounting** > **Quotations** > **Project quotations**.
1. Create a project quotation.

    :::image type="content" source="../media/gst-proj-trans-01.png" alt-text="Screenshot of the Project quotations page.":::

1. Select **Tax information**.

    :::image type="content" source="../media/gst-proj-trans-02.png" alt-text="Screenshot of the Tax information dialog box when creating a project quotation.":::

1. Select **OK**.
1. On the Action Pane, on the **Quote** tab, in the **Tax** group, select **Tax document**.

    :::image type="content" source="../media/gst-proj-trans-03.png" alt-text="Screenshot of the Tax document page when creating a project quotation.":::

1. Close the page.
1. On the Action Pane, select **Workflow** > **Submit** to start the quotation workflow.
1. Update the comment, and then select **Submit**.

### After the quotation is approved

1. On the Action Pane, on the **Quote** tab, in the **Process** group, select **Send quotation**.
1. Select **OK**.
1. On the Action Pane, on the **Follow up** tab, in the **Generate** group, select **Confirm**.
1. Select **OK**.

## Create a project contract

1. Go to **Project management and accounting** > **Projects** > **Project contracts**.
1. Create a project contract.
1. On the Action Pane, on the **Project contract** tab, in the **Attachments** group, select **Tax information**.

    :::image type="content" source="../media/gst-proj-trans-04.png" alt-text="Screenshot of the Tax information dialog box.":::

## Create a project

1. On the **Project contracts** page, on the Action Pane, on the **Maintain** tab, in the **New** group, select **Project**.
1. In the **Project type** field, select **Time and material**.
1. Enter a project name.
1. Select a project group.
1. Select the project contract ID.
1. Select **Create project**.
1. On the Action Pane, on the **Project** tab, in the **Setup** group, select **Tax information**.

    :::image type="content" source="../media/gst-proj-trans-05.png" alt-text="Screenshot of the Tax information dialog box when creating a project.":::

1. Select **OK**.

## Create an expense journal

1. On **Projects**, on the Action Pane, on the **Project** tab, in the **Journals** group, select **Expense**.
1. Select **New** to create a journal, and then select **Lines** to create a project expense journal.

    :::image type="content" source="../media/gst-proj-trans-06.png" alt-text="Screenshot of the Journal voucher page.":::

1. Select the **General** tab.
1. On the **Invoice** tab, enter the invoice information.
1. Select **Tax information** \> **Cost**.

    :::image type="content" source="../media/gst-proj-trans-07.png" alt-text="Screenshot of the Tax information dialog box when creating an expense journal.":::

1. Select **OK**, and then select **Tax information** \> **Invoice**.

    :::image type="content" source="../media/gst-proj-trans-08.png" alt-text="Screenshot of the Tax information dialog box for invoices when creating an expense journal.":::

1. Select **OK**, and then select **Tax document**.

    :::image type="content" source="../media/gst-proj-trans-09.png" alt-text="Screenshot of the Tax document page when creating an expense journal.":::

1. Close the page.
1. Select **Post** \> **Post**.
1. Select **Inquiries** \> **Voucher**.

    The following illustration shows an example of what you see.

    | Ledger account name      | Debit amount (Rs.) | Credit amount (Rs.) |
    |--------------------------|--------------------|---------------------|
    | Purchases account        | 5,000.00           |                     |
    | CGST recoverable account | 500                |                     |
    | SGST recoverable account | 500                |                     |
    | Vendor account           |                    | 6,000.00            |

1. Close the page.

## Create an hour journal

1. On **Projects**, on the Action Pane, on the **Project** tab, in the **Journals** group, select **Hour**.
1. Select **New** to create a journal, and then select **Lines**.
1. Create a project hour journal.

    :::image type="content" source="../media/gst-proj-trans-10.png" alt-text="Screenshot of the Journal lines for hours page.":::

1. Select the **General** tab.

    :::image type="content" source="../media/gst-proj-trans-11.png" alt-text="Screenshot of the General tab of the Journal lines for hours page.":::

1. Save the record, and then select **Tax information**.

    :::image type="content" source="../media/gst-proj-trans-12.png" alt-text="Screenshot of the Tax information dialog box for creating an hour journal.":::

1. Select **OK**.
1. Select **Post**.
1. Select **OK**.
1. Close the page.

## Create an Item journal

1. On **Projects**, on the Action Pane, on the **Project** tab, in the **Journals** group, select **Item**.
1. Select **New** to create a journal, and then select **Lines**.
1. Create an item journal.

    :::image type="content" source="../media/gst-proj-trans-13.png" alt-text="Screenshot of the Journal lines, inventory page.":::

1. Select the **Project** tab.

    :::image type="content" source="../media/gst-proj-trans-14.png" alt-text="Screenshot of the Project tab of the Journal lines, inventory page.":::

1. Save the record, and then select **Tax information**.

    :::image type="content" source="../media/gst-proj-trans-15.png" alt-text="Screenshot of the Tax information dialog box for creating an item journal.":::

1. Select **OK**.
1. Select **Post**.
1. Select **OK**.
1. Close the page.

## Create a fee journal

1. On **Projects**, on the Action Pane, on the **Project** tab, in the **Journals** group, select **Fee**.
1. Select **New** to create a journal, and then select **Lines**.
1. Create a journal line.
1. Select the **General** tab.

    :::image type="content" source="../media/gst-proj-trans-16.png" alt-text="Screenshot of the Journal lines page.":::

1. Select **Tax information**.

    :::image type="content" source="../media/gst-proj-trans-17.png" alt-text="Screenshot of the Tax information dialog box for creating a fee journal.":::

1. Select **OK**.
1. Select **Post**.
1. Select **OK**.
1. Close the page.

## Create an on-account transaction

1. On **Projects**, on the Action Pane, on the **Manage** tab, in the **Bill** group, select **On-account transactions**.
1. Select **New**, and enter a sales price.

    :::image type="content" source="../media/gst-proj-trans-18.png" alt-text="Screenshot of the On-account page.":::

1. Select **Tax information**.
1. On the **GST** FastTab, in the **Service accounting codes** field, select the Services Accounting Code (SAC).

    :::image type="content" source="../media/gst-proj-trans-19.png" alt-text="Screenshot of the Tax information dialog box for creating an on-account transaction.":::

1. Select **OK**.
1. Close the page.

## Create a project invoice proposal

1. On **Projects**, on the Action Pane, on the **Manage** tab, in the **New** group, select **Invoice proposal**.
1. Select the project transactions for invoicing, and then select **OK**.
1. Select **View details**.
1. Select **Tax information**.

    :::image type="content" source="../media/gst-proj-trans-20.png" alt-text="Screenshot of the Tax information dialog box for creating a project invoice proposal.":::

1. Select **OK**.
1. Close the page.
1. Select **Tax document**.

    :::image type="content" source="../media/gst-proj-trans-21.png" alt-text="Screenshot of the Tax document page when creating a project invoice proposal.":::

1. Close the page.

### Update additional fees

1. On **Projects**, select **Create Fees**.
1. Enter the values, and then select **OK**.
1. On the **Fee** tab, select the additional fee record, and then select **View details**.
1. Select **Tax information**.

    :::image type="content" source="../media/gst-proj-trans-22.png" alt-text="Screenshot of the Tax information dialog box for updating additional fees.":::

1. Select **OK**.
1. Close the page.
1. Select **Tax document**.

    :::image type="content" source="../media/gst-proj-trans-23.png" alt-text="Screenshot of the Tax document page when updating additional fees.":::

1. Close the page.
1. Select **Post**.
1. Select **OK**.
1. Select **OK**.

## Create a customer advance invoice

1. On **Projects**, on the Action Pane, on the **Manage** tab, in the **Bill** group, select **Customer advance** > **Request a customer advance**.
1. Enter a description and the customer advance amount.
1. Select **OK**.
1. Select **View details**.
1. Select **Tax information**.
1. On the **GST** FastTab, in the **Service accounting codes** field, select the SAC.

    :::image type="content" source="../media/gst-proj-trans-24.png" alt-text="Screenshot of the Tax information dialog box for creating a customer advance invoice.":::

1. Select **OK**.
1. Close the page.
1. Select **Tax document** to validate the tax computation.
1. Close the page.
1. Select **Post**.
1. Select **Print invoice**, and then select **OK**.
1. Select **OK**.

## Validate the tax report

The following illustration shows an example of the **Tax invoice** report.

:::image type="content" source="../media/gst-proj-trans-25.png" alt-text="Screenshot of the Tax invoice report.":::

## Create a service management

1. Go to **Service management** > **Common** > **Service agreements** > **Service agreements**.
1. Create a service agreement.
1. Select **Create service orders**.

    :::image type="content" source="../media/gst-proj-trans-26.png" alt-text="Screenshot of the Create service orders dialog box.":::

1. Select **OK**.

### Validate a service order

1. On the **Service agreements** page, on the Action Pane, on the **Deliver** tab, in the **Service orders** group, select **View**.

    :::image type="content" source="../media/gst-proj-trans-27.png" alt-text="Screenshot of the Service orders page.":::

1. Select **Edit**.
1. On the Action Pane, on the **Service order** tab, in the **Show** group, switch to the header view.
1. Select the **Sign off** check box.
1. On the Action Pane, on the **Dispatch** tab, in the **Service stage** group, select **Next stage**.
1. On the Action Pane, on the **Invoice** tab, in the **Post** group, select **Service order**.

    :::image type="content" source="../media/gst-proj-trans-28.png" alt-text="Screenshot of the Post service orders dialog box.":::

1. Select **OK**.

## Create and post a project invoice proposal

1. On **Service agreements**, on the Action Pane, on the **Invoice** tab, in the **Related information** group, select **Project invoice proposals**.
1. Select **New** > **Invoice proposal**.
1. Select a project, and then select **Search**.
1. Select **OK**.
1. Select **Post**.
1. Select **OK**.
1. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
