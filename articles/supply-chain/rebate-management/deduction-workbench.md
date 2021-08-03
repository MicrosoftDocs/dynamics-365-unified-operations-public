---
title: Manage deductions using the deduction workbench
description: This topic describes how to use the deduction workbench to process customer payments that include deductions.
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
> The deduction workbench has been part of the sales and marketing functionality in Microsoft Dynamics 365 Supply Chain Management for a long time. However, it has now been enhanced so that it also works with the newer **Rebate management** module. This topic describes how to use both older features and Rebate management features of the deduction workbench. However, if you haven't [turned on the **Rebate management** module for your system](rebate-management-enable.md), some of the functionality that is described here won't be available to you.

## Prerequisites

### Set up the old deduction management system

You can use the deduction workbench together with the old deduction management capabilities of Supply Chain Management, even if you aren't using the **Rebate management** module. However, you must first prepare your system as described in this section.

Before you can use the deduction workbench, you must complete the setup tasks that are described in [Set up deduction management](/dynamicsax-2012/appuser-itpro/set-up-deduction-management). You should also have some type of rebate agreement set up for the customer: either a customer rebate, as described in [Setting up and maintaining customer rebates](/dynamicsax-2012/appuser-itpro/setting-up-and-maintaining-customer-rebates), or a trade allowance rebate.

If you're applying a deduction to a customer rebate, you must complete these tasks:

- [Set up your customer rebates](/dynamicsax-2012/appuser-itpro/setting-up-and-maintaining-customer-rebates).
- Approve and process the rebate, so that you can use the deduction workbench.

If you're applying a deduction to a trade allowance rebate, you must complete these tasks:

- Set up billback rebates.
- Apply billback rebates.

### <a name="accounts-receivable-deductions"></a>Configure accounts receivable and deductions

The system records all deduction events in a claim journal. Therefore, your system must include a journal that can be used for this purpose. If you don't already have a claim journal, set it up now. This journal is required to create deductions directly on the deduction workbench, customer settlement, or customer page.

To set up a new claim journal for deductions, follow these steps.

1. Go to **General ledger \> Journal setup \> Journal names**.
1. Select **New**, and set the following fields for the new journal name:

    - **Name** – Enter a unique name for the claim journal.
    - **Description** – Enter a description of the new journal.
    - **Journal type** – Select *Daily*.
    - **Voucher series** – Assign an existing number sequence. Alternatively, create a new number sequence that has company scope, and assign it to the new journal name.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Deductions** tab, on the **General** FastTab, set the **Claim journal name** field to the journal name that you just created.
1. On the **Return order** FastTab, set the following fields:

    - **Create return order** – Set this option to specify what the system should do when a quantity-based claim is approved:

        - *Yes* – Create a return order.
        - *No* – Create a negative sales order.

    - **Creation without attached invoice** – Select a value to specify what the system should do when a quantity-based claim is approved but no invoice is attached:

        - *Accept* – Create a return order.
        - *Warning* – Create a return order, but show the following warning message: "Claim is not attached to an invoice."
        - *Error* – Don't create a return order, and show the following error message: "Claim is not attached to an invoice. Update has been canceled."

    - **Create return order prior to deduction approval** – Set this option to *Yes* if return orders can be created before the claim is approved. This setting applies only to quantity-based claims where the **Create return order** option is set to *Yes*.

### Configure General ledger parameters

When the system creates a claim journal for a new deduction, it also creates two new customer transactions: one to offset the amount of the claim against the original invoice and one to register a customer's debt to the amount of the claim (because the claim hasn't yet been approved). Therefore, you must set up your system so that a single voucher can have multiple customer lines.

To enable a single voucher to have multiple customer lines, follow these steps.

1. Go to **General ledger \> Ledger setup \> General ledger parameters**.
1. On the **Ledger** tab, on the **General** FastTab, set the **Allow multiple transactions within one voucher** option to *Yes*.
1. If you receive a warning message, select **Close** to accept the change.

### <a name="deduction-reasons"></a>Create deduction reasons

The system requires that users specify a reason for each deduction that they enter directly on the deduction workbench, customer settlement, or customer page. The reason determines how the deduction is handled when it's approved.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction reasons**.
1. Select **New** to add a row to the grid, and then set the following fields for it:

    - **Claim reason** – Enter a unique name for the reason.
    - **Description** – Enter a description of the reason to provide more information about how it should be used.
    - **Claim basis** – Select a claim basis for the claim reason:

        - *Price based* – Create a free text credit upon approval.
        - *Quantity based* – Create a negative sales order or return order upon approval.

    - **Return reason code** – Select a return reason code to apply as the **Return reason code** value for the return order.
    - **Type** – Select a deduction type. The **Deduction offset** value for the selected type will be used to set the **Deduction offset** field when a deduction or claim is created. Deduction types are defined on the **Deduction types** page (**Sales and marketing \> Trade allowances \> Deductions \> Deduction types**).
    - **Claim posting account** – This field is available only when the **Claim basis** field is set to *Price based*. When a price-based claim is approved, the system assigns the ledger account that you select here as the **Main account** value for the draft free text credit note.

### Set up the settle approved deductions periodic task

For deductions that are created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page, you can set up the *Settle approved deductions* periodic task to automatically match deductions and credits that have matching **Deduction ID** values and amounts.

To schedule this task, go to **Sales marketing \> Periodic tasks \> Settle approved deductions**, and set up options, filters, and a schedule, just as for other types of periodic tasks.

> [!NOTE]
> If the **Automatic settlement** option is set to *Yes* on the **Settlement** tab of the **Accounts receivable parameters** page (**Account receivable \> Setup \> Accounts receivable parameters**), the *Settle approved deductions* periodic task won't do anything, because the credit will automatically be settled.

## Create a deduction

### Create a deduction journal entry by using the customer payment journal

To create a deduction journal entry, follow these steps.

1. Go to **Accounts receivable \> Payments \> Customer payment journal**.
1. Select **New** to add a row to the grid.
1. In the **Name** field for the new row, select the name of the journal.
1. On the Action Pane, select **Lines**.
1. Enter the date, company account, and customer account number.
1. In the **Invoice** field, select the invoice that the deduction is associated with.
1. In the **Credit** field, enter the amount that the customer paid.
1. Select **OK** to confirm that the amount is less than the total amount of the marked transaction.
1. Select the offset account type and the offset account.
1. On the toolbar above the grid, select **Deductions**.
1. On the **Deduction** page, on the Action Pane, select **New** to add a row to the grid. The **Deduction ID** field for the new row is automatically set.
1. In the **Type** field, select the deduction type.
1. In the **Amount** field, enter the amount that is shown in the **Balance** field below the deduction list. This amount represents the amount that the customer deducted from the payment.
1. Close the **Deduction** page. You're returned to the **Customer payments** page, which now shows a new line for the deduction.
1. On the Action Pane, select **Validate \> Validate**. You should receive the following message: "Journal is OK."
1. On the Action Pane, select **Post**.

### Create a deduction by using the deduction workbench

The create a new deduction on the deduction workbench, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. On the Action Pane, select **Maintain \> New deduction**.

    In the **New deduction** dialog box, the **Deduction ID** field is set based on the **Deduction ID** number sequence that is defined on the **Trade allowance management parameters** page (**Sales and marketing \> Setup \> Trade allowances \> Trade allowance management parameters**).

1. Set the following fields:

    - **Customer account** – Select the customer account that the deduction applies to.
    - **External claim number** – Enter the customer's claim reference.
    - **Claim amount** – Enter the tax-inclusive claim amount. The value must be positive.
    - **Currency** – Select the currency for the deduction. The default value is the currency that is set for the selected customer account.
    - **Claim basis** – Select the claim basis. The claim basis determines the type of credit transaction that is created after the deduction or claim is approved.

        - *Price based* – A draft free text invoice will be created.
        - *Quantity based* – A negative sales order or return order will be created.

    - **Claim date** – Select the date of the claim. The default value is the current date.
    - **Claim reason** – Select the reason code that applies to the current deduction. The claim basis that you selected affects the options that apply. For more information about how to create and configure the claim reasons that are available for selection here, see the [Create deduction reasons](#deduction-reasons) section earlier in this topic.
    - **Notes** – Add any notes that apply. When the claim is approved, the approver will be able to edit or add to the claim's notes.
    - **Create claim journal** – Set this option to specify whether the claim journal should be created when the claim or deduction is created:

        - *Yes* – The system will create and post a general journal by using the claim journal that is set up on the **Accounts receivable parameters** page. (For more information, see the [Configure accounts receivable and deductions](#accounts-receivable-deductions) section earlier in this topic.) When an invoice is attached to the claim, the claim journal is used to reduce the balance of the applicable invoice. If the claim is later rejected, the claim journal and settlements (if an invoice was attached) will be reversed.
        - *No* – No claim journal is created at this time. It will be created when the claim is approved. An invoice can still be attached to the new claim, even though a claim journal isn't created. However, settlement can't be done without the claim journal.

1. Select **OK**.

    A new deduction is created. If you set the **Create claim journal** option to *Yes*, the following transactions are posted:

    - **Two new customer transactions** – One transaction offsets the amount of the claim against the original invoice. The other transaction registers a customer's debt to the amount of the claim, because the claim hasn't yet been approved. The original invoice transaction and the offsetting claim transaction will automatically be marked for settlement when you attach the invoice by selecting **Maintain \> Attach invoice** on the Action Pane.
    - **Two offsetting transactions** – These transactions are posted to the **Deduction offset** ledger account.
    - **Claim journal** – To view the claim journal for each deduction that is shown on the deduction workbench, select the **References** tab. The claim journal is shown in the **Journal batch number** field. You can also view the claim journal on the **Deduction events** tab. There, it will have an **Update type** value of *Match*.

### Create a deduction from a customer settlement

The process of creating a deduction from a customer settlement resembles the process of creating a deduction via the deduction workbench. However, the customer and invoice currency are automatically set, and the invoice is attached. You don't have to select **Maintain \> Attach invoice** on the Action Pane when you create a claim or deduction via the customer settlement page.

1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select the customer to create a deduction for.
1. On the Action Pane, on the **Collect** tab, in the **Settle** group, select **Settle transactions**.
1. In the **Setting transactions** dialog box, on the **Overview** tab, select the invoice to create the deduction against.
1. On the toolbar, select **Deductions \> New deduction**.

    In the **New deduction** dialog box, the **Deduction ID** field is set based on the **Deduction ID** number sequence that is defined on the **Trade allowance management parameters** page (**Sales and marketing \> Setup \> Trade allowances \> Trade allowance management parameters**). The **Customer account** field is set to the customer account that the deduction applies to.

1. Set the following fields:

    - **External claim number** – Enter the customer's claim reference.
    - **Claim amount** – Enter the tax-inclusive claim amount. The value must be positive.
    - **Currency** – Select the currency for the deduction. The default value is the currency that is set for the selected customer account.
    - **Claim basis** – Select the claim basis. The claim basis determines the type of credit transaction that is created after the deduction or claim is approved.

        - *Price based* – A draft free text invoice will be created.
        - *Quantity based* – A negative sales order or return order will be created.

    - **Claim date** – Select the date of the claim. The default value is the current date.
    - **Claim reason** – Select the reason code that applies to the current deduction. The claim basis that you selected affects the options that apply. For more information about how to create and configure the claim reasons that are available for selection here, see the [Create deduction reasons](#deduction-reasons) section earlier in this topic.
    - **Notes** – Add any notes that apply. When the claim is approved, the approver will be able to edit or add to the claim's notes.
    - **Create claim journal** – Set this option to specify whether the claim journal should be created when the claim or deduction is created:

        - *Yes* – The system will create and post a general journal by using the claim journal that is set up on the **Accounts receivable parameters** page. (For more information, see the [Configure accounts receivable and deductions](#accounts-receivable-deductions) section earlier in this topic.) When an invoice is attached to the claim, the claim journal is used to reduce the balance of the applicable invoice. If the claim is later rejected, the claim journal and settlements (if an invoice was attached) will be reversed.
        - *No* – No claim journal is created at this time. It will be created when the claim is approved. An invoice can still be attached to the new claim, even though a claim journal isn't created. However, settlement can't be done without the claim journal.

1. Select **OK**.

    A new deduction is created. If you set the **Create claim journal** option to *Yes*, the following transactions are posted:

    - **Two new customer transactions** – One transaction offsets the amount of the claim against the original invoice. The other transaction registers a customer's debt to the amount of the claim, because the claim hasn't yet been approved. The original invoice transaction and the offsetting claim transaction will automatically be marked for settlement when you attach the invoice by selecting **Maintain \> Attach invoice** on the Action Pane.
    - **Two offsetting transactions** – These transactions are posted to the **Deduction offset** ledger account.
    - **Claim journal** – To view the claim journal for each deduction that is shown on the deduction workbench, select the **References** tab. The claim journal is shown in the **Journal batch number** field. You can also view the claim journal on the **Deduction events** tab. There, it will have an **Update type** value of *Match*.

    You're returned to the **Settle transactions** page, which now shows the selected invoice as marked. The **Post** button is available only if you set the **Create claim journal** option to *Yes*. If it's available, select **Post** to reduce the balance on the invoice by the **Claim amount** value.

### Create a deduction from a customer page

The process of creating a deduction from a customer page resembles the process of creating a deduction via the deduction workbench. However, the customer is automatically set.

1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select the customer to create a deduction for.
1. On the Action Pane, on the **Collect** tab, in the **Deductions** group, select **Create deductions**.

    In the **New deduction** dialog box, the **Deduction ID** field is set based on the **Deduction ID** number sequence that is defined on the **Trade allowance management parameters** page (**Sales and marketing \> Setup \> Trade allowances \> Trade allowance management parameters**). The **Customer account** field is set to the customer account that the deduction applies to.

1. Set the following fields:

    - **External claim number** – Enter the customer's claim reference.
    - **Claim amount** – Enter the tax-inclusive claim amount. The value must be positive.
    - **Currency** – Select the currency for the deduction. The default value is the currency that is set for the selected customer account.
    - **Claim basis** – Select the claim basis. The claim basis determines the type of credit transaction that is created after the deduction or claim is approved.

        - *Price based* – A draft free text invoice will be created.
        - *Quantity based* – A negative sales order or return order will be created.

    - **Claim date** – Select the date of the claim. The default value is the current date.
    - **Claim reason** – Select the reason code that applies to the current deduction. The claim basis that you selected affects the options that apply. For more information about how to create and configure the claim reasons that are available for selection here, see the [Create deduction reasons](#deduction-reasons) section earlier in this topic.
    - **Notes** – Add any notes that apply. When the claim is approved, the approver will be able to edit or add to the claim's notes.
    - **Create claim journal** – Set this option to specify whether the claim journal should be created when the claim or deduction is created:

        - *Yes* – The system will create and post a general journal by using the claim journal that is set up on the **Accounts receivable parameters** page. (For more information, see the [Configure accounts receivable and deductions](#accounts-receivable-deductions) section earlier in this topic.) When an invoice is attached to the claim, the claim journal is used to reduce the balance of the applicable invoice. If the claim is later rejected, the claim journal and settlements (if an invoice was attached) will be reversed.
        - *No* – No claim journal is created at this time. It will be created when the claim is approved. An invoice can still be attached to the new claim, even though a claim journal isn't created. However, settlement can't be done without the claim journal.

1. Select **OK**.

    A new deduction is created. If you set the **Create claim journal** option to *Yes*, the following transactions are posted:

    - **Two new customer transactions** – One transaction offsets the amount of the claim against the original invoice. The other transaction registers a customer's debt to the amount of the claim, because the claim hasn't yet been approved. The original invoice transaction and the offsetting claim transaction will automatically be marked for settlement when you attach the invoice by selecting **Maintain \> Attach invoice** on the Action Pane.
    - **Two offsetting transactions** – These transactions are posted to the **Deduction offset** ledger account.
    - **Claim journal** – To view the claim journal for each deduction that is shown on the deduction workbench, select the **References** tab. The claim journal is shown in the **Journal batch number** field. You can also view the claim journal on the **Deduction events** tab. There, it will have an **Update type** value of *Match*.

## Create a credit note for a customer

After an approved rebate exists for a customer, you can create a credit note on the customer's account to represent the rebate, as required. The credit then appears on the deduction workbench, where it can be matched to a deduction.

To create a credit note, follow these steps.

1. Go to **Sales and marketing \> Customers \> All customers**.
1. Select the customer.
1. On the Action Pane, on the **Collect** tab, in the **Settle** group, select **Settle transactions**.
1. In the **Settle transactions** dialog box, select the transaction that the rebate was applied to.
1. On the toolbar, on the **Functions** menu, select the type of rebate program that applies.
1. On the **Rebate** page, on the **Overview** tab, select the **Mark** checkbox next to the relevant rebate ID.
1. On the Action Pane, select **Functions \> Create credit note**.

## Process a deduction on the deduction workbench

On the deduction workbench, you can match deductions to open credit transactions, split deductions, deny deductions, and write off deductions.

Depending on how you want to process a deduction, complete one or more of the procedures in the following subsections. You can combine the procedures as required. For example, you can split a deduction into two parts, and then match one part to a credit but leave the remaining part on the workbench so that it be matched to another credit later. You can also match a deduction to a credit that is smaller than the deduction amount, and then deny or write off the remaining balance of the deduction.

### Match a deduction to a credit

To match a deduction to a credit, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** checkbox for the deduction to process.
1. In the **Open transactions** section, select the **Mark** checkbox for the credit to match to the deduction. If multiple credits are listed, you can select more than one credit to match to the deduction. If you want the system to automatically select credits that match the amount of the deduction, on the toolbar, select an appropriate option on **Select deduction amount** menu.
1. On the Action Pane, select **Maintain \> Match**. The system matches the deduction to the credit. If a balance remains in the deduction, it's shown in the **Remaining amount** field on the **Deductions** tab.

    > [!NOTE]
    > For deductions that were created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page, the **Maintain \> Match** command is available only if the **Claim status** field is set to *Accepted*. This command can be used to manually match the price-based or quantity-based transaction to the associated credit in the **Open transactions** section. This credit is created either when the deduction is approved (by using the **Maintain \> Approve deduction** command), or when it's attached to an existing credit as described in the [Credits created outside the approve deduction process](#credits-outside-approval) section later in this topic. The *Settle approved deductions* periodic task (**Sales marketing \> Periodic tasks \> Settle approved deductions**) can also be used to automatically match deductions and credits that have matching **Deduction ID** values and amounts.

### Split a deduction

To split a deduction, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** checkbox for the deduction to process.
1. On the Action Pane, select **Maintain \> Split**.
1. In the **Split** dialog box, in the **Split amount** field, enter the amount to split from the main deduction. Then select **OK**.
1. On the **Deductions** tab, notice that a new record appears for the split amount. The original deduction record contains the remainder of the deduction balance. You can now manage the two parts of the original rebate separately.
1. Select the original deduction record, and then select the **References** tab. The **Split amount** field shows the amount that was split off from the original amount.

### Attach an invoice to a deduction

You can attach an invoice to a deduction if the deduction was created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page, and if no invoice is currently attached to it (that is, the **Invoice** column is blank).

To attach an invoice to a deduction, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** checkbox for the deduction to process.
1. On the Action Pane, select **Maintain \> Attach invoice**.
1. In the **Attach invoice** dialog box, select an invoice, and then select **OK**.
1. In the **Settle transactions** dialog box, follow one of these steps, depending on whether a claim journal was posted when the deduction was created:

    - If a claim journal was posted, the invoice that you selected and the claim journal's customer credit transaction show a check mark in the **Mark** column. Select **Post**. The remaining balance on the attached invoice is reduced by the claim amount.
    - If a claim journal wasn't posted, no transaction shows a check mark in the **Mark** column. Because you can't offset against a claim journal until the deduction is approved, select **Cancel**.

### Detach an invoice from a deduction

You can detach an invoice from a deduction if the deduction was created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page, if an invoice is currently attached to it (that is, the **Invoice** column shows an invoice number), and if the **Claim status** field is set to *Open*. You might complete this task because an incorrect invoice was attached. The invoice is removed from the deduction, and its remaining balance is updated if it was reduced when the invoice was attached.

To detach an invoice, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** checkbox for the deduction to process.
1. On the Action Pane, select **Maintain \> Detach invoice**.

### Approve a deduction

You can approve deductions that were created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page. However, you can approve only deductions where the **Claim status** field is set to *Open*.

To approve a deduction, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** checkbox for the deduction to process.
1. On the Action Pane, select **Maintain \> Approve deduction**.
1. In the **Approve deduction** dialog box, edit or add information to the **Note** value as required.
1. If the deduction is price-based, and an invoice hasn't been attached to it, select an item sales tax group. Typically, the tax item group is set on the invoice. Therefore, the tax item code must be specified when it isn't attached to an invoice.
1. Select **OK**.

    At this point, no further changes can be made to the deduction. If the **Create claim journal** option was set to *No* when the deduction was created, the claim journal is created and posted when the deduction is approved. After the deduction is approved, the credit is automatically created and opened. The type depends on the deduction's **Claim basis** value:

    - *Price based* – If the deduction is price-based, a free text invoice is created for the customer account. You can add a description and post the credit. The following fields are filled in by the deduction when the draft is created:

        - **Deduction ID** – This field is added to the header to enable traceability back to the deduction.
        - **Main account** – The value is determined by the **Claim posting account** value that is set for the deduction reason that is assigned to the deduction.
        - **Item sales tax group** – The value is determined by the attached invoice or by the value that you selected when you approved the deduction.
        - **Unit price** – The value is the credit of the deduction's claim amount.
        - **Invoice text** – By default, this field is set to the deduction's **Notes** value.

    - *Quantity based* – If the deduction is quantity-based, an open sales order or return order is created. The **Create return order** setting on the **[Accounts receivable parameters](#accounts-receivable-deductions)** page determines whether a sales order or a return order is created when the deduction is approved. The **Copy orders** page appears and is filtered to show rows where the **Invoice account** field is set to the deduction's customer account. Follow these steps:

        1. On the **Invoices** FastTab, the **Headers** section shows sales invoices where the **Invoice account** value matches the deduction's customer account. Select an applicable sales invoice.
        1. The **Lines** section shows lines from the selected sales invoice. Select the **Select** checkbox for each line that you want to copy. Alternatively, in the **Headers** section, select the **Select all** checkbox for the sales order to select all its lines.
        1. Adjust the **Quantity** value for one or more lines as required.

            All the lines that you've selected so far are listed on the **Selected lines or header to be copied** FastTab.

        1. Repeat the previous two steps as required until all the required lines are listed on the **Selected lines or header to be copied** FastTab.
        1. Select **OK**.

            The new return order is opened, and the following fields are automatically set:

            - **Deduction ID** – This field is added to the header to enable traceability back to the deduction.
            - **Return reason code** – By default, this field is set to the **Return reason code** value that is set for the deduction reason that is assigned to the deduction.

After the credit is invoiced, it appears in the **Open transactions** section of the deduction workbench against the applicable **Deduction ID** value, and its **Claim type** field is set to *Other credits*. The credit will be available until it's settled with the deduction in one of the following ways:

- You manually settle it by selecting **Maintain \> Match** on the Action Pane.
- It's automatically settled by the *Settle approved claims* periodic job (**Sales and marketing \> Periodic tasks \> Settle approved claims**).
- It's automatically settled because the **Automatic settlement** option on the **Settlement** tab of the **Accounts receivable parameters** page is set to *Yes*.

To view the credit that is created when the deduction is approved, you can also use the **Open credit** button in the **Open transactions** section of the deduction workbench.

### Create a return order

You can create a return order for deductions that were created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page. However, all the following conditions must be met:

- The **Claim basis** field is set to *Quantity based*.
- The **Claim status** field is set to *Open*.
- The **Create return order** option on the **Deductions** tab of the **[Accounts receivable parameters](#accounts-receivable-deductions)** page is set to *Yes*.
- The **Create return order prior to deduction approval** option on the **Deductions** tab of the **[Accounts receivable parameters](#accounts-receivable-deductions)** page is set to *Yes*.

To create a return order, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** checkbox for the deduction to process.
1. On the Action Pane, select **Maintain \> Create return order**.
1. In the **Approve deduction** dialog box, edit or add information to the existing **Notes** value as required, and then select **OK**.
1. In the **Copy orders** dialog box, on the **Invoices** FastTab, the **Headers** section shows sales invoices where the **Invoice account** value matches the deduction's customer account. Select an applicable sales invoice.
1. The **Lines** section shows lines from the selected sales invoice. Select the **Select** checkbox for each line you want to copy. Alternatively, in the **Headers** section, select the **Select all** checkbox for the sales order to select all its lines.
1. Adjust the **Quantity** value for one or more lines as required.

    All the lines that you've selected so far are listed on the **Selected lines or header to be copied** FastTab.

1. Repeat the previous two steps as required until all the required lines are listed on the **Selected lines or header to be copied** FastTab.
1. Select **OK**.

    The new return order is opened, and the following fields are automatically set:

    - **Deduction ID** – This field is added to the header to enable traceability back to the deduction.
    - **Return reason code** – By default, this field is set to the **Return reason code** value that is set for the deduction reason that is assigned to the deduction.

### Deny a deduction

To deny a deduction, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** checkbox for the deduction to process.
1. On the Action Pane, select **Maintain \> Deny**.
1. In the **Deny** dialog box, select the reason code for the denial, and then select **OK**.
1. In the **Show** field below the Action Pane, select *Closed*.

    The **Deductions** tab shows the denied deduction, and the **Remaining amount** field for the deduction is set to *0.00*.

    For deductions that were created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page, the following events occur:

    - On the **References** tab, fields in the **Denial** section are updated.
    - If you selected to create the claim journal when the deduction was created, and if an invoice has been attached to the deduction that reduced the invoice's balance, the invoice is detached, and the remaining balance of the previously attached invoice is increased by the rejected claim's amount.
    - The deduction's **Status** field is set to *Closed*.
    - The deduction's **Claim status** field is set to *Rejected*.

To reverse a denial, follow these steps.

1. On the **Deductions** tab, select a denied deduction.
1. On the Action Pane, select **Reverse denial**.

    For deductions that were created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page, the following events occur:

    - On the **References** tab, fields in the **Denial** section are updated.
    - The deduction's **Status** field is set to *Open*.
    - The deduction's **Claim status** field is set to *Open*.

### Write off a deduction

To write off a deduction, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** checkbox for the deduction to process.
1. On the Action Pane, select **Maintain \> Write-off**.
1. In the **Write-off** dialog box, select the reason code for the write-off, and then select **OK**.
1. In the **Show** field, select *Closed*.

    The **Deductions** tab shows the written-off deduction, and the **Remaining amount** field for the deduction is set to *0.00*.

    For deductions that were created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page, the following events occur:

    - On the **References** tab, fields in the **Write-off** section are updated.
    - If you created the claim journal when the deduction was created, a claim journal is posted to the deduction's write-off reason code. You can view this entry on the **Deduction events** tab, where it has an **Update type** value of *Write-off*.
    - The deduction's **Status** field is set to *Closed*
    - The deduction's **Claim status** field is set to *Write-off*.

To reverse a write-off, follow these steps.

1. On the **Deductions** tab, select a denied deduction.
1. On the Action Pane, select **Reverse write-off**.

    For deductions that were created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page, the following events occur:

    - On the **References** tab, fields in the **Write-off** section are updated.
    - If you created the claim journal when the deduction was created, a claim journal is posted to the deduction's write-off reason code. You can view this entry on the **Deduction events** tab, where it has an **Update type** value of *Reverse write-off*.
    - The deduction's **Status** field is set to *Open*.
    - The deduction's **Claim status** field is set to *Open*.

## <a name="credits-outside-approval"></a>Credits created outside the Approve deduction process

This section applies only to deductions that were created by using the **New deduction** command on the deduction workbench, customer settlement, or customer page.

Different users might already have created a free text invoice, return order, or negative sales order for a customer's claim outside the **Approve deduction** process. When the existing deduction is approved on the deduction workbench, the system automatically creates another free text invoice, return order, or negative sales order. This section describes how to attach existing credits to a deduction before the deduction is approved, to help prevent duplicate credits.

### Attach a credit to deduction

This section describes how you can attach a credit to a deduction from the credit.

After a credit is attached to the deduction, you can view it by using the **Open credit** button on the toolbar in the **Open transactions** section of the deduction workbench.

After a credit is invoiced, and the deduction is approved, the credit appears in the **Open transactions** section of the deduction workbench against the applicable **Deduction ID** value, and its **Claim type** field is set to *Other credits*.

#### Attach a free text invoice to a deduction

To attach a free text invoice to a deduction, follow these steps.

1. Go to **Accounts receivable \> Invoices \> All free text invoices**.
1. Select the applicable invoice.
1. On the Action Pane, on the **Invoice** tab, select **Attach credit to deduction**. This button is available only if the free text invoice's **Deduction ID** field is blank. A blank field indicates that the free text invoice isn't already attached to a deduction.
1. On the **Attach credit to deduction** page, you can select *one* deduction. Only open *price-based* deductions are available for selection.
1. Select **OK**. The **Deduction ID** field is set on the free text invoice's header.

#### Attach a return order to a deduction

To attach a return order to a deduction, follow these steps.

1. Go to **Accounts receivable \> Orders \> All return orders**.
1. Select the applicable received or open return merchandise authorization (RMA) number.
1. On the Action Pane, on the **Return order** tab, select **Attach credit to deduction**. This button is available only if the return order's **Deduction ID** field is blank. A blank field indicates that the return order isn't already attached to a deduction.
1. On the **Attach credit to deduction** page, you can select *one* deduction. Only open *quantity-based* deductions are available for selection.
1. Select **OK**. The **Deduction ID** field is set on the return order's header.

#### Attach a sales order to a deduction

To attach a sales order to a deduction, follow these steps.

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Select the applicable open, delivered, or invoiced sales order.
1. On the Action Pane, on the **Invoice** tab, select **Attach credit to deduction**. This button is available only if the sales order's **Deduction ID** field is blank. A blank field indicates that the sales order isn't already attached to a deduction.
1. On the **Attach deduction** page, you can select *one* deduction. Only open *quantity-based* deductions are available for selection.
1. Select **OK**. The **Deduction ID** field is set on the sales order's header.

#### Detach a deduction from a credit

If the incorrect deduction has been attached, you can detach it from the credit. However, all the following conditions must be met:

- A credit is attached to the deduction.
- The **Claim status** field is set to *Open*.

To detach a deduction from a credit, follow one of these steps, depending on the credit type:

- **Free text invoices:** On the **All free text invoices** page, select an invoice. Then, on the Action Pane, on the **Invoice** tab, select **Detach credit from deduction**.
- **Return orders:** On the **All return orders** page, select an order. Then, on the Action Pane, on the **Return order** tab, select **Detach credit from deduction**.
- **Sales orders:** On the **All sales orders** page, select an order. Then, on the Action Pane, on the **Invoice** tab, select **Detach credit from deduction**.

### Attach a deduction to a credit

This section describes how you can attach a deduction to a credit from the deduction.

#### Attach a deduction to a free text, return order, or sales order credit

To attach a deduction to a free text, return order, or sales order credit, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the applicable open deduction.
1. On the Action Pane, select **Maintain \> Attach deduction to credit**. This button is available only if the **Claim status** field is set to *Open*.
1. On the **Attach credit** page, you can select *one* credit. The type of credits that is shown depends on the deduction's **Claim basis** value:

    - *Price based* – The page shows free text invoices for the customer account where the **Deduction ID** field is blank. Customer requisitions are also shown because the free text invoice might be unposted. Therefore, it might not have a number that can be referenced.
    - *Quantity based* – The type of credits that is shown depends on the setting of the **Create return order** option on the **[Accounts receivable parameters](#accounts-receivable-deductions)** page:

        - *Yes* – The page shows return orders for the customer account where the **Deduction ID** field is blank.
        - *No* – The page shows sales orders for the customer account where the **Deduction ID** field is blank.

1. Select **OK**. The **Deduction ID** field is set on the credit's header.

After a credit is attached to the deduction, you can view it by using the **Open credit** button on the toolbar in the **Open transactions** section of the deduction workbench.

After a credit is invoiced, and the deduction is approved, the credit appears in the **Open transactions** section of the deduction workbench against the applicable **Deduction ID** value, and its **Claim type** field is set to *Other credits*.

#### Detach a credit from the deduction

If the incorrect credit has been attached, you can detach it from the deduction. On the Action Pane, in the **Maintain** group, select **Detach deduction from credit**. The **Deduction ID** value is removed from the credit.

The **Detach deduction from credit** button is available only if the following conditions are met:

- A credit is attached to the deduction.
- The **Claim status** field is set to *Open*.

## Create a one-time promotion

Sometimes, you might not have an approved rebate that you can match to a deduction. In this case, you can use the *one-time promotion* feature to match the deduction to a trade allowance that is associated with the customer. The *one-time promotion* feature creates a new trade allowance agreement and a lump sum merchandising event. It then matches the lump sum to the deduction and makes the postings that are required to close the deduction.

This feature is useful if you use trade allowances. For more information about trade allowances, see [Trade allowance management](../sales-marketing/trade-allowance.md).

First, you must set up a template that can be used to create the new trade allowance agreement. To set up a template, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Templates**.
1. On the Action Pane, select **New**.
1. In the fields, enter the information that should appear in the agreements that are created from the template.
1. On the **Customers** FastTab, in the **Hierarchy** field, select a hierarchy level.
1. In the hierarchy list, select the customer that has an unmatched deduction, and then select the right arrow button (**\>**). The customer is added to the **Trade allowance agreement customers** list.
1. Set the remaining fields as you require, and then close the page.
1. Go to **Sales and marketing \> Setup \> Trade allowance \> Trade allowance management parameters**.
1. On the **Overview** tab, in the **One-time promotion template** field, select the name of the template to use to create one-time promotions.

Next, you can create a one-time promotion on the deduction workbench. To create a one-time promotion, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the **Mark** checkbox next to the deduction to process.
1. On the Action Pane, select **Maintain \> Settle deduction as one-time promotion**.
1. In the **One-time promotion** dialog box, follow these steps to associate the deduction with one or more funds:

    1. Select **New**, and then, in the **Fund ID** field, select a fund ID. Repeat this step to add as many funds as you require.
    1. In the **Percent** field next to each fund ID, enter the percentage of the deduction to allocate to the fund. The amounts that you enter in the **Percent** fields must total 100 percent.

1. Select **OK**. The system creates a new trade allowance agreement that has a lump sum merchandising event and matches the lump sum to the deduction.

## Do a mass update of deductions

If you must make the same change to multiple deductions, you can select those deductions and do a mass update of their fields.

To do a mass update, follow these steps.

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. In the **Show** field below the Action Pane, select the type of deductions to view.
1. Select the checkbox next to each deduction that you want to update. Then, on the Action Pane, select **Maintain \> Mass update**.
1. The **Mass update** dialog box shows the selected deductions. Update the fields as you require, and then select **OK** to accept the changes.
