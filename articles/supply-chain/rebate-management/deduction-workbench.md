---
title: Manage deductions using the deduction workbench
description: This topic describes how to use the deduction workbench to process customer payments that include deductions
author: sherry-zheng
ms.date: 08/02/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: chuzheng
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
---

# Manage deductions using the deduction workbench

[!include [banner](../includes/banner.md)]

This topic describes how to use the deduction workbench to process customer payments that include deductions.

A customer who is owed a rebate can decide not to wait for a rebate payout. Instead, the customer can send a payment that includes a deduction for the amount of the rebate. To handle this type of transaction, you can use the deduction workbench to match deductions to open credit transactions, split deductions, deny deductions, and write off deductions.

> [!NOTE]
> The deduction workbench has long been a part of Dynamics 365 Supply Chain Management sales and marketing functionality, however it has now been enhanced to also work with the newer Rebate management module. This topic describes how to use both legacy and Rebate management features of the deduction workbench. However, if you haven't [enabled the Rebate management module](rebate-management-enable.md), then some of the functionality described here won't be available to you.

## Prerequisites

### Set up the legacy deduction management system

You can use the deductions workbench together with the legacy deduction management capabilities of Supply Chain Management, even if you aren't using the new Rebate management module. To do so, you must prepare your system as described in this section before you can use the deduction workbench.

Before you can use the workbench, you must complete the setup tasks that are described in [Set up deduction management](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-deduction-management). You should also have some type of rebate agreement set up for the customer: either a customer rebate, as described in [Setting up and maintaining customer rebates](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/setting-up-and-maintaining-customer-rebates), or a trade allowance rebate.

If you are applying a deduction to a customer rebate:

- [Set up your customer rebates](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/setting-up-and-maintaining-customer-rebates)
- Approve and process the rebate before you can use the deduction workbench.

If you are applying a deduction to a trade allowance rebate:

- Set up billback rebates
- Apply billback rebates

<a name="accounts-receivable-deductions"></a>

### Configure accounts receivable and deductions

The system records all deduction events in a claims journal. Therefore, your system must include a journal for this purpose. If you don't have one already, set one up now. This journal is required to create deductions directly on the deduction workbench, customer settlement, or customer pages.

To set up a new claims journal for deductions:

1. Go to **General ledger \> Journal setup \> Journal names**

1. Select **New**. Make the following settings for the new journal name:
    - **Name** – Enter a unique name for the claim journal.
    - **Description** – Enter a description for the new journal.
    - **Journal type** – Select *Daily*.
    - **Voucher series** – Assign an existing number sequence or create a new number sequence with company scope and assign it to the new journal name.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.

1. Open the **Deductions** tab.

1. On the **General** FastTab, set **Claim journal name** to the journal name you just created.

1. Expand the **Return order** FastTab and make the following settings:
    - **Create return order** – Choose what the system should do when a *Quantity-based* claim is approved. Select one of the following options:
        - *Yes* – Create a return order.
        - *No* –  Create a negative sales order.
    - **Creation without attached invoice** – Choose what the system should do when a quantity-based claim is approved and an invoice hasn't been attached. Select one of the following options:
        - *Accept* – Create a return order.
        - *Warning* – Create a return order, but show the warning, "Claim is not attached to an invoice."
        - *Error* – Do not create a return order and show the error, "Claim is not attached to an invoice. Update has been canceled."
    - **Create return order prior to deduction approval** – Set to *Yes* if return orders can be created before the claim has been approved. This setting only applies to quantity-based claims where **Create return order** is set to *Yes*.

### Configure general ledger parameters

When the system creates a claim journal for a new deduction, it also creates two new customer transactions: one to offset the amount of claim against the original invoice, and one to register a customer's debt to the amount of the claim (because the claim has not been approved yet). You must therefore set your system to allow multiple customer lines in one voucher.

To allow multiple customer lines in one voucher:

1. Go to **General ledger \> Ledger setup \> General ledger parameters**.
1. Open the **Ledger** tab
1. On the **General** FastTab, set **Allow multiple transactions within one voucher** to *Yes*.
1. If a warning appears, just select **Close** to accept the change.

<a name="deduction-reasons"></a>

### Create deduction reasons

The system requires users to specify a reason for each deduction they enter directly in the deduction workbench, customer settlement, or customer page. The reason also establishes the way the deduction will be handled when the deduction is approved.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction reasons**.

1. Select **New** to add a new row to the grid and then make the following settings for it:
    - **Claim reason** – Enter a unique name for the reason.
    - **Description** – Enter a description for the reason to provide more information about how it should be used.
    - **Claim basis** – Select a claim basis for the claim reason. Choose one of the following values:
        - *Price based* – Create a free text credit upon approval.
        - *Quantity based* – Create a negative sales order or return order upon approval.
    - **Return reason code** – Select a return reason code to apply as the **Return reason code** for the return order.
    - **Type** – Select a deduction type (as specified on **Sales and marketing \> Trade allowances \> Deductions \> Deduction types**). This **Deduction offset** for the selected type will be used to populate the **Deduction offset** when creating a deduction or claim.
    - **Claim posting account** – This setting is only enabled when **Claim basis** is set to *Price based*. When the price-based claim is approved, the system will assign the ledger account selected here as the **Main account** for the draft free text credit note.

### Set up the settle approved deductions periodic task

For deductions created using the **New deduction** command from the deduction workbench, customer settlement, or customer page, you can set up the *Settle approved deductions* periodic task to automatically match deductions and their credit where the credit's **Deduction ID** matches to the deduction's **Deduction ID** and the amounts match.

To schedule this task, go to **Sales marketing \> Periodic tasks \> Settle approved deductions** and set up its options, filters, and schedule just as you would with other types of periodic tasks.

> [!NOTE]
> If **Automatic settlement** is set to *Yes* on the **Settlement** tab of the **Account receivable \> Setup \> Accounts receivable parameters** page, the *Settle approved deductions* periodic task won't do anything because the credit will have already been settled automatically.

## Create a deduction

### Create a deduction journal entry using the customer payment journal

To create a deduction journal entry, follow these steps.

1. Select **Accounts receivable \> Payments \> Customer payment journal**.
1. Select **New** to add a new row to the grid and then, in the **Name** field for the new row, select the name of the  journal.
1. On the Action Pane, select **Lines**.
1. Enter the date, company account, and customer account number. In the **Invoice** field, select the invoice that the deduction is associated with.
1. In the **Credit** field, enter the amount that the customer paid. Select **OK** to confirm that the amount is less than the total of the marked transaction.
1. Select the **Offset account type** and the **Offset account**.
1. From the toolbar above the grid, select **Deductions**.
1. The **Deduction** page opens. Select **New** on the Action Pane to add a new row to the grid.
1. The **Deduction ID** field is populated automatically. Select the deduction **Type** in the list.
1. In the **Amount** field, enter the amount that is displayed in the **Balance** field below the deduction list. This amount represents the amount that the customer deducted from the payment.
1. Close the **Deduction** page. You return to the **Customer payments** page, which now shows a new line for the deduction.
1. On the Action Pane, select **Validate \> Validate**. You should receive the following message: "Journal is OK."
1. On the Action Pane, select **Post**.

### Create a deduction using the deduction workbench

The create a new deduction in the deduction workbench, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. On the Action Pane, select **Maintain \> New deduction**
1. The **New deduction** dialog opens. Make the following settings:
    - **Deduction ID** – This will be assigned by the **Deduction ID** number sequence set on the **Trade allowance management parameters** page (**Sales and marketing \> Setup \> Trade allowances \> Trade allowance management parameters**).
    - **Customer account** – Select the customer account the deduction applies to.
    - **External claim number** – Enter the customer's claim reference.
    - **Claim amount** – Enter the tax-inclusive claim amount (must be a positive value).
    - **Currency** – Select the currency for the deduction. This defaults to the currency set for the selected **Customer account**.
    - **Claim basis** – After the deduction/claim has been *approved* the claim basis will determine the type of credit transaction created. Select one of the following values:
        - *Price based* – a draft free text invoice will be created.
        - *Quantity based* – a negative sales order or return order will be created.
    - **Claim date** – Select the date of the claim. Defaults to today's date.
    - **Claim reason** – Select the reason code that applies for the current deduction. The selected **Claim basis** affects the claim reason options that will apply. For more information about how to create and configure the values available here, see [Create deduction reasons](#deduction-reasons).
    - **Notes** – Add any notes that apply. When the claim is approved, the approver will be able to edit or add to the claim's notes.
    - **Create claim journal** – Choose whether the claim journal should be created when the claim or deduction is created. Set the slider to one of the following values:
        - *Yes* – The system will create and post a general journal using the **Claim journal** as set up on the **Accounts receivable parameters** page (see also [Configure accounts receivable and deductions](#accounts-receivable-deductions)). When an invoice is attached to the claim, the claim journal is used to reduce the balance of the applicable invoice. If the claim is later rejected, the claim journal and settlements (if invoice was attached) will be reversed.
        - *No* – No claim journal is created at this time. It will first be created when the claim is approved. An invoice can still be attached to the new claim without a claim journal created, but settlement will not be possible without the claim journal.

1. Select **OK**. This will create a new deduction and, if **Create claim journal** was set to *Yes*, the following transactions will be posted:
    - **Two new customer transactions** – One transaction is to offset the amount of claim against the original invoice. The other transaction is to register a customer's debt to amount of the claim as the claim has not been approved yet. The original invoice transaction and the offsetting claim transaction will be automatically marked for settlement when the invoice is attached by selecting **Maintain \> Attach invoice** on the Action Pane.
    - **Two offsetting transactions** – These are posted to the **Deduction offset** ledger account.
    - **Claim journal** – You can see the claim journal for each deduction shown on the workbench by going to the **References** tab, where it is shown in the **Journal batch number** field. You can also see it on the **Deduction events** tab, where it will show an **Update type** of *Match*.

### Create a deduction from a customer settlement

Creating a deduction from a customer settlement is similar to creating a new deduction via the deduction workbench, but the customer and invoice currency is defaulted and the invoice is attached. You don't have to select **Maintain \> Attach invoice** on the Action Pane when creating a new claim or deduction via the customer settlement page.

1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select the customer you want to create a deduction for.
1. On the Action Pane, on the **Collect** tab, in the **Settle** group, select **Settle transactions**.
1. The **Setting transactions** dialog opens. On the **Overview** tab, select exactly one invoice against which to create the deduction.
1. On the toolbar, select **Deductions \> New deduction**.
1. The **New deduction** dialog opens. Make the following settings:
    - **Deduction ID** – This will be assigned by the **Deduction ID** number sequence set on the **Trade allowance management parameters** page (**Sales and marketing \> Setup \> Trade allowances \> Trade allowance management parameters**).
    - **Customer account** – This is the customer account the deduction applies to. It shows the customer you selected.
    - **External claim number** – Enter the customer's claim reference.
    - **Claim amount** – Enter the tax-inclusive claim amount (must be a positive value).
    - **Currency** – Select the currency for the deduction. This defaults to the currency set for the selected **Customer account**.
    - **Claim basis** – After the deduction/claim has been *approved* the claim basis will determine the type of credit transaction created. Select one of the following values:
        - *Price based* – a draft free text invoice will be created.
        - *Quantity based* – a negative sales order or return order will be created.
    - **Claim date** – Select the date of the claim. Defaults to today's date.
    - **Claim reason** – Select the reason code that applies for the current deduction. The selected **Claim basis** affects the claim reason options that will apply. For more information about how to create and configure the values available here, see [Create deduction reasons](#deduction-reasons).
    - **Notes** – Add any notes that apply. When the claim is approved, the approver will be able to edit or add to the claim's notes.
    - **Create claim journal** – Choose whether the claim journal should be created when the claim or deduction is created. Set the slider to one of the following values:
        - *Yes* – The system will create and post a general journal using the **Claim journal** as set up on the **Accounts receivable parameters** page (see also [Configure accounts receivable and deductions](#accounts-receivable-deductions)). When an invoice is attached to the claim, the claim journal is used to reduce the balance of the applicable invoice. If the claim is later rejected, the claim journal and settlements (if invoice was attached) will be reversed.
        - *No* – No claim journal is created at this time. It will first be created when the claim is approved. An invoice can still be attached to the new claim without a claim journal created, but settlement will not be possible without the claim journal.

1. Select **OK**. This will create a new deduction and, if **Create claim journal** was set to *Yes*, the following transactions will be posted:
    - **Two new customer transactions** – One transaction is to offset the amount of claim against the original invoice. The other transaction is to register a customer's debt to amount of the claim as the claim has not been approved yet. The original invoice transaction and the offsetting claim transaction will be automatically marked for settlement when the invoice is attached by selecting **Maintain \> Attach invoice** on the Action Pane.
    - **Two offsetting transactions** – These are posted to the **Deduction offset** ledger account.
    - **Claim journal** – You can see the claim journal for each deduction shown on the workbench by going to the **References** tab, where it is shown in the **Journal batch number** field. You can also see it on the **Deduction events** tab, where it will show an **Update type** of *Match*.

1. You return to the **Settle transactions** page, which now shows the selected invoice as marked. The **Post** button will only be enabled if the **Create claim journal** was set to *Yes.* It it's enabled, select **Post** to reduce the balance on the invoice by the **Claim amount**.

### Create a deduction from a customer page

Create a deduction from a customer page is similar to creating a new deduction via the deduction workbench, but the customer is defaulted.

1. Go to **Accounts receivable \> Customers \> All customers**
1. Select the customer you want to create a deduction for.
1. On the Action Pane, on the **Collect** tab, in the **Deductions** group, select **Create deductions**
1. The **New deduction** dialog opens. Make the following settings:
    - **Deduction ID** – This will be assigned by the **Deduction ID** number sequence set on the **Trade allowance management parameters** page (**Sales and marketing \> Setup \> Trade allowances \> Trade allowance management parameters**).
    - **Customer account** – This is the customer account the deduction applies to. It shows the customer you selected.
    - **External claim number** – Enter the customer's claim reference.
    - **Claim amount** – Enter the tax-inclusive claim amount (must be a positive value).
    - **Currency** – Select the currency for the deduction. This defaults to the currency set for the selected **Customer account**.
    - **Claim basis** – After the deduction/claim has been *approved* the claim basis will determine the type of credit transaction created. Select one of the following values:
        - *Price based* – a draft free text invoice will be created.
        - *Quantity based* – a negative sales order or return order will be created.
    - **Claim date** – Select the date of the claim. Defaults to today's date.
    - **Claim reason** – Select the reason code that applies for the current deduction. The selected **Claim basis** affects the claim reason options that will apply. For more information about how to create and configure the values available here, see [Create deduction reasons](#deduction-reasons).
    - **Notes** – Add any notes that apply. When the claim is approved, the approver will be able to edit or add to the claim's notes.
    - **Create claim journal** – Choose whether the claim journal should be created when the claim or deduction is created. Set the slider to one of the following values:
        - *Yes* – The system will create and post a general journal using the **Claim journal** as set up on the **Accounts receivable parameters** page (see also [Configure accounts receivable and deductions](#accounts-receivable-deductions)). When an invoice is attached to the claim, the claim journal is used to reduce the balance of the applicable invoice. If the claim is later rejected, the claim journal and settlements (if invoice was attached) will be reversed.
        - *No* – No claim journal is created at this time. It will first be created when the claim is approved. An invoice can still be attached to the new claim without a claim journal created, but settlement will not be possible without the claim journal.

1. Select **OK**. This will create a new deduction and, if **Create claim journal** was set to *Yes*, the following transactions will be posted:
    - **Two new customer transactions** – One transaction is to offset the amount of claim against the original invoice. The other transaction is to register a customer's debt to amount of the claim as the claim has not been approved yet. The original invoice transaction and the offsetting claim transaction will be automatically marked for settlement when the invoice is attached by selecting **Maintain \> Attach invoice** on the Action Pane.
    - **Two offsetting transactions** – These are posted to the **Deduction offset** ledger account.
    - **Claim journal** – You can see the claim journal for each deduction shown on the workbench by going to the **References** tab, where it is shown in the **Journal batch number** field. You can also see it on the **Deduction events** tab, where it will show an **Update type** of *Match*.

## Create a credit note for a customer

Once an approved rebate exists for a customer, you can create a credit note on the customer's account to represent the rebate if necessary. The credit then appears in the deduction workbench, where it can be matched to a deduction.

To create a credit note, follow these steps.

1. Go to **Sales and marketing \> Customers \> All customers**.
1. Select the customer.
1. On the Action Pane, open the **Collect** tab and, in the **Settle** group, select **Settle transactions**.
1. The **Settle transactions** dialog opens. Select the transaction that the rebate was applied to.
1. On the toolbar, open the **Functions** menu and then select the type of rebate program that applies.
1. The **Rebate** page opens. On the **Overview** tab, select the **Mark** check box next to the relevant rebate ID.
1. On the Action Pane, select  **Functions \> Create credit note**.

## Process a deduction in the deduction workbench

In the deduction workbench, you can match deductions to open credit transactions, split deductions, deny deductions, and write off deductions.

Depending on how you want to process a deduction, complete one or more of the procedures provided in the following subsections. You can combine the procedures as needed. For example, you can split a deduction into two parts, and then match one part to a credit but leave the remaining part in the workbench to be matched to another credit later. You can also can match a deduction to a credit that is smaller than the deduction amount, and then deny or write off the remaining balance of the deduction.

### Match a deduction to a credit

To match a deduction to a credit:

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** check box for the deduction you want to process.
1. In the **Open transactions** section, select the **Mark** check box for the credit to match to the deduction. If multiple credits are listed, you can select more than one credit to match to the deduction. Or, if you want the system to automatically select credits that match the amount of the deduction, open the **Select deduction amount** menu in the toolbar and select an appropriate option.
1. On the Action Pane, select **Maintain \> Match**. The system matches the deduction to the credit. If a balance remains in the deduction, this balance appears in the **Remaining amount** field on the **Deductions** tab.

> [!NOTE]
> For deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page, the **Maintain \> Match** option will only be enabled if **Claim status** is set to *Accepted*. This can be used to manually match the price or quantity-based transaction to its associated credit in the **Open transactions** section created either when the deduction is approved (via **Maintain \> Approve deduction**) or by attaching the deduction to an existing credit as described in [Credits created outside the approve deduction process](#credits-outside-approval). The periodic task **Sales marketing \> Periodic tasks \> Settle approved deductions** can also be used to automatically match deductions and their credit where the credit's **Deduction ID** matches to the deduction's **Deduction ID** and the amounts match.

### Split a deduction

To split a deduction:

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** check box for the deduction you want to process.
1. On the Action Pane, select **Maintain \> Split**.
1. The **Split** dialog opens. In the **Split amount** field, enter the amount to split from the main deduction.
1. Select **OK**.
1. On the **Deductions** tab, notice that a new record appears for the split amount. The original deduction record contains the remainder of the deduction balance. You can now manage the two parts of the original rebate separately.
1. Select the original deduction record, and then open the **References** tab. The **Split amount** field shows the amount that was split off from the original amount.

### Attach an invoice to a deduction

For deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page, you can attach an invoice to any deduction that doesn't already have one attached (these are deductions where the **Invoice** column is blank).

To attach an invoice to a deduction:

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** check box for the deduction you want to process.
1. On the Action Pane, select **Maintain \> Attach invoice**.
1. The **Attach invoice** dialog opens. Select an invoice.
1. Select **OK**.
1. The **Settle transactions** dialog opens.
    - If a claim journal was posted when the deduction was created:
        - The invoice you selected and the claim journal's customer credit transaction shows a check mark in the **Mark** column.
        - Select **Post**. The remaining balance on the attached invoice will be reduced by the claim amount.
    - If a claim journal was not posted when the deduction was created:
        - No transaction will show a check mark in the **Mark** column.
        - You aren't able to offset against a claim journal until the deduction has been approved, so just select **Cancel**.

### Detach an invoice from a deduction

For deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page, you can detach an invoice to any deduction that currently has one attached (these are deductions where the **Invoice** column shows an invoice number) and where **Claim status** is set to *Open*. You might do this because an incorrect invoice has been attached. This removes the invoice from the deduction and updates the remaining balance of the previously attached invoice if it was reduced by attaching the invoice.

To detach an invoice:

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** check box for the deduction you want to process.
1. On the Action Pane, select **Maintain \> Detach invoice**.

### Approve a deduction

You can approve deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page. You can only approve deductions where **Claim status** is set to *Open*.

To approve a deduction:

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** check box for the deduction you want to process.
1. On the Action Pane, select **Maintain \> Approve deduction**.
1. The **Approve deduction** dialog opens. Edit or add to the **Note** field as needed.
1. If an invoice has not been attached to a price-based deduction, select an **Item sales tax group**. Normally, the tax item group is on the invoice, and thereforee the tax item code must be specified when not attached to an invoice.
1. Select **OK**. No further changes will be allowed to the deduction. If **Create claim journal** was set to *No* when the deduction was created, the claim journal is created and posted when the deduction is approved. After the deduction has been approved, the credit is automatically created and opened. The type will depend on the deduction's **Claim basis** as follows:
    - For deductions with a **Claims basis** of *Price based*:<br>If the deduction is price-based, a free text invoice is created for the customer account. You can add a **Description** and **Post** the credit. The following fields are populated by the deduction when the draft is created:
      - **Deduction ID** – Added to the **Header** for traceability back to the deduction.
      - **Main account** – Determined by **Claim posting account** on the **Deduction reason** assigned to the deduction.
      - **Item sales tax group** – Determined by the attached invoice or the value you selected when approving the deduction.
      - **Unit price** – The credit of the deduction's **Claim amount**
      - **Invoice text** – Defaults from deduction's **Notes**

    - For deductions with a **Claims basis** of *Quantity based*:<br>If the deduction is quantity-based, an open sales order or return order is created. The **Create return order** setting on the **[Accounts receivable parameters](#accounts-receivable-deductions)** page determines whether a sales order or return order is created when the deduction is approved. The **Copy orders** page opens, filtered to show rows where the **Invoice account** is set to the deduction's customer account.
        1. Expand the **Invoices** FastTab.
        1. The **Headers** section of the **Invoices** FastTab shows sales invoices where the **Invoice account** matches the deduction's customer account. Select an applicable sales invoice.
        1. The **Lines** section of the **Invoices** FastTab shows lines from the selected sales invoice. Mark the **Select** check box for each line you want to copy (or select the **Select all** check box for the sales order in the **Headers** section to select all of its lines).
        1. If necessary, adjust the **Quantity** for one or more lines as needed.
        1. The lines you selected so far are listed on the **Selected lines or header to be copied** FastTab. Repeat the previous two steps as needed until all the required lines are listed here.
        1. Select **OK**. The new return order opens, with the following fields populated automatically:
            - **Deduction ID** – Added to the **Header** for traceability back to the deduction.
            - **Return reason code** – Defaults to the **Return reason code** set for the **Deduction reason** assigned to the deduction.

1. Once the credit has been invoiced, it will be shown on the deduction workbench's **Open transactions** section with its **Claim type** set to *Other credits* against the applicable **Deduction ID**. The credit will be available until settled with the deduction in one of the following ways:

    - Manually settled by selecting **Maintain \> Match** on the Action Pane.
    - Automatically settled by the periodic job **Sales and marketing \> Periodic tasks \> Settle approved claims**.
    - Automatically settled because the **Automatic settlement** parameter in **Accounts receivable parameters \> Settlement** is set to *Yes*.

    The credit that is created when the deduction is approved can also be viewed using the **Open credit** button available on the **Open transactions** section of the deduction workbench.

### Create a return order

For deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page, you can create a return order when all of the following are true:

- **Claim basis** is set to *Quantity based*.
- **Claim status** is set to *Open*.
- **Create return order** setting on the **Deductions** tab of the **[Accounts receivable parameters](#accounts-receivable-deductions)** page is set to *Yes*.
- **Create return order prior to deduction approval** setting on the **Deductions** tab of the **[Accounts receivable parameters](#accounts-receivable-deductions)** page is set to *Yes*.

To create a return order:

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** check box for the deduction you want to process.
1. On the Action Pane, select **Maintain \> Create return order**.
1. The **Approve deduction** dialog opens. Edit or add to the existing **Notes** as needed and then select **OK**.
1. The **Copy orders** dialog opens. Expand the **Invoices** FastTab.
1. The **Headers** section of the **Invoices** FastTab shows sales invoices where the **Invoice account** matches the deduction's customer account. Select an applicable sales invoice.
1. The **Lines** section of the **Invoices** FastTab shows lines from the selected sales invoice. Mark the **Select** check box for each line you want to copy (or select the **Select all** check box for the sales order in the **Headers** section to select all of its lines).
1. If necessary, adjust the **Quantity** for one or more lines as needed.
1. The lines you selected so far are listed on the **Selected lines or header to be copied** FastTab. Repeat the previous two steps as needed until all the required lines are listed here.
1. Select **OK**. The new return order opens, with the following fields populated automatically:
    - **Deduction ID** – Added to the **Header** for traceability back to the deduction.
    - **Return reason code** – Defaults to the **Return reason code** set for the **Deduction reason** assigned to the deduction.

### Deny a deduction

To deny a deduction:

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** check box for the deduction you want to process.
1. On the Action Pane, select **Maintain \> Deny**.
1. The **Deny** dialog opens. Select the **Reason code** for the denial and select **OK**.
1. In the **Show** field below the Action Pane, select *Closed*. The denied deduction is displayed on the **Deductions** tab, and the **Remaining amount** for the deduction is set to *0.00*.
1. For deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page, the following occur:
    - On the **References** tab, fields in the **Denial** field group are updated.
    - If you selected to create the claim journal when the deduction was created and if an invoice has been attached to the deduction that reduced the invoice's balance, the invoice will be detached and the previously attached invoice's remaining balance will be increased by the rejected claim's amount.
    - The deduction's **Status** has now been set to *Closed* and **Claim status** set to *Rejected*.

To reverse a denial:

1. Select a denied deduction on the **Deductions** tab.
1. On the Action Pane, select **Reverse denial**.
1. For deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page, the following occur:
    - On the **References** tab, fields in the **Denial** field group are updated.
    - The deduction's **Status** is set to *Open*.
    - The deduction's **Claim status** is set to *Open*.

### Write off a deduction

To write off a deduction:

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** check box for the deduction you want to process.
1. On the Action Pane, select **Maintain \> Write-off**.
1. The **Write-off** dialog opens. Select the **Reason code** for the write-off and then select **OK**.
1. In the **Show** field, select *Closed*. The written-off deduction is displayed on the **Deductions** tab, and the remaining amount for the deduction is set to *0.00*.
1. For deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page, the following occur:
    - On the **References** tab, fields in the **Write-off** field group are updated.
    - If you created the claim journal when the deduction was created, a claim journal will be posted to the deduction's write-off reason code. You can see this entry on the **Deduction events** tab, where it is shown with an **Update type** of *Write-off*.
    - The deduction's **Status** is set to *Closed*
    - The deduction's  **Claim status** is set to *Write-off*.

To reverse a write off:

1. Select a denied deduction on the **Deductions** tab.
1. On the Action Pane, select **Reverse write-off**.
1. For deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page, the following occur:
    - On the **References** tab, fields in the **Write-off** field group are updated.
    - If you created the claim journal when the deduction was created, a claim journal will be posted to the deduction's Write-off reason code. You can see this entry on the **Deduction events** tab, where it is shown with an **Update type** of *Reverse write-off*.
    - The deduction's **Status** is set to *Open*.
    - The deduction's **Claim status** is set to *Open*.

<a name="credits-outside-approval"></a>

## Credits created outside the Approve deduction process

This section only applies to deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page.

Different users could have already created a free text, return order, or negative sales order for a customer's claim outside of the **Approve deduction** process. When the existing deduction is approved in the deduction workbench, the system automatically creates another free text, return order, or negative sales order. The following process describes how to attach existing credits to a deduction before the deduction is approved, which will prevent duplicate credits.

### Attach a credit to deduction

The following subsections describe how you can attach a credit to a deduction, while on the credit.

Once a credit has been attached to the deduction, it will be available to view using the **Open credit** button on the deduction work bench **Open transactions** section toolbar.

After a credit has been invoiced and the deduction approved, it will be displayed in the deduction work bench **Open transactions** section against the applicable **Deduction ID** with its **Claim type** set to *Other credits*.

#### Attach a free text to a deduction

To attach a **free text** to a deduction:

1. Go to **Accounts receivable \> Invoices \> All free text invoices**.
1. Select the applicable invoice.
1. On the Action Pane, on the **Invoice** tab, select **Attach credit to deduction**. This is only enabled if the Free text's **Deduction ID** is blank and therefore not already attached to a deduction.
1. The **Attach credit to deduction** page opens, where you can select *one* deduction. Only open *price-based* deductions can be selected.
1. Select **OK**. The **Deduction ID** is populated on the free text's header.

#### Attach a return order to a deduction

To attach a return order to a deduction:

1. Go to **Accounts receivable \> Orders \> All return orders**.
1. Select the applicable received or open **RMA number**.
1. On the Action Pane, on the **Return order** tab, select **Attach credit to deduction**. This is only enabled if the return order's **Deduction ID** is blank and therefore not already attached to a deduction.
1. The **Attach credit to deduction** page opens, where you can select *one* deduction. Only open *quantity-based* deductions can be selected.
1. Select **OK**. The **Deduction ID** is populated on the return order's header.

#### Attach a sales order to a deduction

To attach a sales order to a deduction:

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Select the applicable open, delivered, or invoiced **Sales order**.
1. On the Action Pane, on the **Invoice** tab, select **Attach credit to deduction**. This is only enabled if the **Deduction ID** is blank and therefore not already attached to a deduction.
1. The **Attach deduction** page opens, where you can select *one* deduction. Only open *quantity-based* deductions will be available for selection.
1. Select **OK**. The **Deduction ID** is populated on the sales order's header.

#### Detach a deduction from a credit

If the incorrect deduction has been attached, you can detach the deduction from the credit provided the following are true:

- The deduction has a credit attached.
- **Claim status** is set to *Open*.

To detach a deduction from a credit, do one of the following, depending on the credit type:
    - **Free text invoices**: Open the **All free text invoices** page and select an invoice. On the Action Pane, on the **Invoice** tab, select **Detach credit from deduction**
    - **Return orders**: Open the **All return orders** page and select an order. On the Action Pane, on the **Return order** tab, select **Detach credit from deduction**
    - **Sales orders**: Open the **All sales orders** page and select an order. On the Action Pane, on the **Invoice** tab, select **Detach credit from deduction**

### Attach a deduction to a credit

This section describes how you can attach a deduction to a credit, while on the deduction.

#### Attach a deduction to a free text, return order, or sales order credit

To attach a deduction to a free text, return order, or sales order credit:

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the applicable open **Deduction ID**.
1. On the Action Pane, select **Maintain \> Attach deduction to credit**. This is only enabled where **Claim status** set to *Open*.
1. The **Attach credit** page will open, and you can select *one* credit. The type of credits displayed will depend on the deduction's **Claim basis**:
    - **Price based** – Free text invoices for the customer account with blank **Deduction ID**. Customer requisition will also be displayed since the free text might be unposted and therefore have no number to reference.
    - **Quantity based**, where **Create return order** setting on **[Accounts receivable parameters](#accounts-receivable-deductions)** is set to:
        - **Yes** – Return orders for the customer account with blank **Deduction ID**.
        - **No** – Sales order for the customer account with blank **Deduction ID**.
1. Select **OK**. This will populate the **Deduction ID** on the credit's header.

Once the credit has been attached to the deduction, it will be available to view using the **Open credit** button on the **Deduction workbench**'s **Open transactions**

And after the credit has been invoiced and the deduction approved, it will be displayed under **Open transactions** as **Claim type** set to *Other credits* against the applicable **Deduction ID**.

#### Detach a credit from the deduction

If the incorrect credit has been attached, select this option to detach the credit from the deduction. Only enabled for:
    - Deduction that has a credit attached, and
    - **Claim status** is set to *Open*.

On the Action Pane, in the Maintain group, select **Detach deduction from credit**. This removes the **Deduction ID** from the credit.

## Create a one-time promotion

Sometimes, you might not have an approved rebate that you can match to a deduction. In this case, you can use the *one-time promotion* feature to match the deduction to a trade allowance that is associated with the customer. The *one-time promotion* feature creates a new trade allowance agreement and a lump sum merchandising event. The feature then matches the lump sum to the deduction and makes the postings that are required to close the deduction.

This feature is useful if you use trade allowances. For more information about trade allowances, see [Trade allowance management](../sales-marketing/trade-allowance.md).

First, you must set up a template to use to create the new trade allowance agreement. To set up a template, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Templates**.
1. On the Action Pane, select **New**.
1. Fill in the fields with the information that should appear in the agreements that are created from the template.
1. On the **Customers** FastTab, in the **Hierarchy** field, select a hierarchy level. In the hierarchy list, select the customer who has an unmatched deduction, and then select **\>**. The customer is added to the **Trade allowance agreement customers** list.
1. Continue to fill in the remaining fields as you require, and then close the page.
1. Go to **Sales and marketing \> Setup \> Trade allowance \> Trade allowance management parameters**.
1. On the **Overview** tab, in the **One-time promotion template** field, select the name of the template to use to create one-time promotions.

Next, you can create a one-time promotion in the deduction workbench. To create a one-time promotion, follow these steps.

1. Select **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** check box next to the deduction to process.
1. On the Action Pane, select **Maintain \> Settle deduction as one-time promotion**.
1. The **One-time promotion** dialog opens. If you want to associate the deduction with one or more funds, follow these steps:
    1. Select **New**, and then, in the **Fund ID** field, select a fund ID. Repeat this step to add as many funds as you require.
    1. In the **Percent** field next to each fund ID, enter the percentage of the deduction to allocate to the fund. The amounts that you enter in the **Percent** fields must total 100 percent.
1. Select **OK**. The system creates a new trade allowance agreement that has a lump sum merchandising event and matches the lump sum to the deduction.

## Perform a mass update of deductions

If you have to make the same change to multiple deductions, you can select those deductions and perform a mass update of their fields.

To perform a mass update, follow these steps.

1. Select **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. In the **Show** field below the Action Pane, select the type of deductions to view.
1. Select the check box next to each deduction to update. On the Action Pane, select **Maintain \> Mass update**.
1. The **Mass update** dialog opens, showing the selected deductions. Update the fields as you require, and then select **OK** to accept the changes.
