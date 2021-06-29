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

<!-- KFM: add text to intro explaining that the workbench works both with and without Rebate management. maybe also add section mentioning that many features described here require the rebate management feature in FM  -->

## Prerequisites

### Set up the legacy deduction management system

<!-- KFM: @sherry, this is legacy info. We need to evaluate how this fits in considering the new Rebate management module.  -->

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

The system records all deduction events in a claims journal. Therefore, your system must include a journal for this purpose. If you don't have one already, set one up now. This journal is is required to create deductions directly on the deduction workbench, customer settlement, or customer pages.

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
        - *Error* – Do not create a return order and show the error, "Claim is not attached to an invoice. Update has been cancelled."
    - **Create return order prior to deduction approval** – Set to *Yes* if return orders can be created before the claim has been approved. This setting only applies to quantity-based claims where **Create return order** is set to *Yes*.

### Configure general ledger parameters

When the system creates a claim journal for a new deduction, it also creates two new customer transactions: one to offset the amount of claim against the original invoice, and one to register a customer's debt to the amount of the claim (because the claim has not been approved yet). You must therefore set your system to allow multiple customer lines in one voucher.

To allow multiple customer lines in one voucher:

1. Go to **General ledger \> Ledger setup \> General ledger parameters**.
1. Open the **Ledger** tab
1. On the **General** FastTab, set **Allow multiple transactions within one voucher** to *Yes*.
1. A warning appears. Select **Yes** to accept the change.

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

### Create a deduction journal entry using the payment journal

<!--KFM: This section is from AX2012 doc set. Requires verification. -->

Enter the deduction information into the payment journal.

To create a deduction journal entry, follow these steps.

1. Select **Accounts receivable \> Journals \> Payments \> Payment journal**.

1. Select **New**, and then, in the **Name** field, select the name of the deduction journal.

1. On the Action Pane, select **Lines**.

1. Enter the date, company account, and customer account number. In the **Invoice** field, select the invoice that the deduction is associated with.

1. In the **Credit** field, enter the amount that the customer paid. Select **OK** to confirm that the amount is less than the total of the marked transaction.

1. Select the offset account type and the offset account.

1. On the Action Pane, select **\>\>**, and then select **Deductions**. In the **Deduction** page, select **New**.

1. The **Deduction ID** field is populated automatically. Select the deduction type in the list.

1. In the **Amount** field, enter the amount that is displayed in the **Balance** field above the deduction list. This amount represents the amount that the customer deducted from the payment.

1. Close the **Deduction** page. In the **Journal voucher** page, a new line is displayed for the deduction.

1. On the Action Pane, select **Validate**, and then select **Validate**. You should receive the following message: "Journal is OK."

1. On the Action Pane, select **Post**, and then select **Post**.

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
    - **Claim reason** – Select the reason code that applies for the current deduction. The selected selected **Claim basis** affects the claim reason options that will apply. For more information about how to create and configure the values available here, see [Create deduction reasons](#deduction-reasons).
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
    - **Claim reason** – Select the reason code that applies for the current deduction. The selected selected **Claim basis** affects the claim reason options that will apply. For more information about how to create and configure the values available here, see [Create deduction reasons](#deduction-reasons).
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
    - **Claim reason** – Select the reason code that applies for the current deduction. The selected selected **Claim basis** affects the claim reason options that will apply. For more information about how to create and configure the values available here, see [Create deduction reasons](#deduction-reasons).
    - **Notes** – Add any notes that apply. When the claim is approved, the approver will be able to edit or add to the claim's notes.
    - **Create claim journal** – Choose whether the claim journal should be created when the claim or deduction is created. Set the slider to one of the following values:
        - *Yes* – The system will create and post a general journal using the **Claim journal** as set up on the **Accounts receivable parameters** page (see also [Configure accounts receivable and deductions](#accounts-receivable-deductions)). When an invoice is attached to the claim, the claim journal is used to reduce the balance of the applicable invoice. If the claim is later rejected, the claim journal and settlements (if invoice was attached) will be reversed.
        - *No* – No claim journal is created at this time. It will first be created when the claim is approved. An invoice can still be attached to the new claim without a claim journal created, but settlement will not be possible without the claim journal.

1. Select **OK**. This will create a new deduction and, if **Create claim journal** was set to *Yes*, the following transactions will be posted:
    - **Two new customer transactions** – One transaction is to offset the amount of claim against the original invoice. The other transaction is to register a customer's debt to amount of the claim as the claim has not been approved yet. The original invoice transaction and the offsetting claim transaction will be automatically marked for settlement when the invoice is attached by selecting **Maintain \> Attach invoice** on the Action Pane.
    - **Two offsetting transactions** – These are posted to the **Deduction offset** ledger account.
    - **Claim journal** – You can see the claim journal for each deduction shown on the workbench by going to the **References** tab, where it is shown in the **Journal batch number** field. You can also see it on the **Deduction events** tab, where it will show an **Update type** of *Match*.

## Create a credit note for a customer

<!--KFM: This section is from AX2012 doc set. Requires verification. -->

Once an approved rebate exists for a customer, you can create a credit note on the customer's account to represent the rebate if necessary. The credit then appears in the deduction workbench, where it can be matched to a deduction.

To create a credit note, follow these steps.

1. Go to **Sales and marketing \> Common \> Customers \> All customers**.
1. Select the customer, and then, on the **Collect** tab, in the **Settle** group, select **Settle open transactions**.
1. Select the transaction that the rebate was applied to. On the Action Pane, select **Functions**, and then select the type of rebate program that applies.
1. On the **Overview** tab, select the **Mark** check box next to the rebate ID. Select **Functions**, and then select **Create credit note**.

## Process a deduction in the deduction workbench

In the deduction workbench, you can match deductions to open credit transactions, split deductions, deny deductions, and write off deductions.

To process a deduction in the deduction workbench, follow these steps.

1. Go to **Trade allowance management \> Common \> Deduction workbench**.
1. Select the **Mark** check box for the deduction you want to process.
1. Depending on how you want to process the deduction, complete one or more of the procedures provided in the following subsections.

You can combine the procedures described in this section. For example, you can split a deduction into two parts, and then match one part to a credit but leave the remaining part in the workbench to be matched to another credit later. You can also can match a deduction to a credit that is smaller than the deduction amount, and then deny or write off the remaining balance of the deduction.

### Match a deduction to a credit

To match a deduction to a credit:

1. In the **Open transactions** section, select the **Mark** check box for the credit to match to the deduction. If multiple credits are listed, you can select more than one credit to match to the deduction. Or, if you want the system to automatically select credits that match the amount of the deduction, open the **Select deduction amount** menu in the toolbar and select an appropriate option.
1. On the Action Pane, select **Maintain \> Match**. The system matches the deduction to the credit. If a balance remains in the deduction, this balance appears in the **Remaining amount** field on the **Deductions** tab.

> [!NOTE]
> For deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page, the **Maintain \> Match** option will only be enabled if **Claim status** is set to *Accepted*. This can be used to manually match the price or quantity-based transaction to its associated credit in the **Open transactions** section created either when the deduction is approved (via **Maintain \> Approve deduction**) or by attaching the deduction to an existing credit as described in [Credits created outside the approve deduction process](#credits-outside-approval). The periodic task **Sales marketing \> Periodic tasks \> Settle approved deductions** can also be used to automatically match deductions and their credit where the credit's **Deduction ID** matches to the deduction's **Deduction ID** and the amounts match.

### Split a deduction

To split a deduction:

1. On the Action Pane, select **Maintain \> Split**.
1. The **Split** dialog opens. In the **Split amount** field, enter the amount to split from the main deduction.
1. Select **OK**.
1. On the **Deductions** tab, notice that a new record appears for the split amount. The original deduction record contains the remainder of the deduction balance. You can now manage the two parts of the original rebate separately.
1. Select the original deduction record, and then open the **References** tab. The **Split amount** field shows the amount that was split off from the original amount.

### Attach an invoice to a deduction

For deductions created using the **New deduction** command from the deduction workbench, customer settle, or customer page, you can attach an invoice to any deduction that doesn't already have one attached (these are deductions where the **Invoice** column is blank).

To attach an invoice to a deduction:

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

To detach an invoice, select a deduction and, on the Action Pane, select **Maintain \> Detach invoice**.

### Approve a deduction

You can approve deductions created using **New deduction** command from the deduction workbench, customer settle, or customer page. You can only approve deductions where **Claim status** is set to *Open*.

To approve a deduction:

1. On the Action Pane, select **Maintain \> Approve deduction**.
1. The **Approve deduction** dialog opens. Edit or add to the **Note** field as needed.
1. If an invoice has not been attached to a price-based deduction, select an **Item sales tax group**. Normally, the tax item group is on the invoice, and therefor the tax item code must be specified when not attached to an invoice.
1. Select **OK**. No further changes will be allowed to the deduction. If the **Create claim journal** was set to *No* when the deduction was created, the claim journal will be created and posted when the deduction is approved. After the deduction has been approved, the credit will be automatically created and opened. The type will depend on the deduction's **Claim basis** as follows:<!--KFM: Continue here -->
    - For deductions with a **Claims basis** of *Price based* – If the deduction is price based a draft, a free text invoice will be created for the customer account. You can add a **Description** and **Post** the credit. The following fields will be populated by the deduction when the draft is created:
      - **Deduction ID** on the Header for traceability back to the deduction.
      - **Main account** is determined by **Claim posting account** on the **Deduction reason** assigned to the deduction.
      - **Item sales tax group** will be determined by the attached invoice else as selected by user when approving the deduction.
      - **Unit price** is the credit of the deduction's **Claim amount**
      - **Invoice text** will default from deduction's **Notes**

    - For deductions with a **Claims basis** of *Quantity based* – If the deduction is quantity based, an open sales order or return order will be created. The **Create return order** setting on **[Accounts receivable parameters](#_Configure_Accounts_receivable)** will determine if a sales order or return order is created when the deduction is approved. The **Copy orders** page will be opened, filtered to **Invoice account** set to the deduction's Customer account.
      1. Select the applicable **Sales order** and **Lines** and **Quantity** to be copied.
      1. Press **OK**.

        The following fields will be populated by the deduction when the draft is created:
        - **Deduction ID** on the Header for traceability back to the deduction.
        - **Return reason code**, if Return order is created, will default to the **Deduction reason**'s **Return reason code** assigned to the deduction.

1. Once the credit has been invoiced, it will be available on the Deduction workbench's **Open transactions** as **Claim type** set to *Other credits* against the applicable Deduction ID. The credit will be available until settled with the deduction by either:

    - Manually settled using **Maintain \> Match** or
    - Periodic job **Sales and marketing \> Periodic tasks \> Settle approved claims**.

    > [!NOTE]
    > If the **Automatic settlement** parameter in **Accounts receivable parameters \> Settlement** is set to *Yes*, the settle approved claims will not work as the credit will have already been automatically settled.

    The credit that is created when the deduction is approved, open or invoice, can also be viewed using the **Open credit** button available on the **Deduction workbench\> Open transaction** section.

### Create a return order

For deductions created using **New deduction** command from the deduction workbench, customer settle, or customer page is only enabled where:

- **Claim basis** is set to *Quantity based*
- **Claim status** is set to *Open*
- **Create return order** setting on **Deductions** tab in **[Accounts receivable parameters](#_Configure_Accounts_receivable)** is set to *Yes,* and
- **Allow unapproved** setting on **Deductions** tab in **[Accounts receivable parameters](#_Configure_Accounts_receivable)**is set to *Yes*.

1. On the Action Pane, in the **Maintain** group, select **Create a return order**.
1. The **Approve** claim is automatically opened and user has the option to edit or add to the existing **Notes** for the deduction.
1. Press **OK**.
1. The **Copy orders** page will be opened, filtered to **Invoice account** set to the deduction's Customer account.
1. Select the applicable **Sales order** and **Lines** and **Quantity** to be copied.
1. Press **OK**. The following fields on the Return order, will be populated by the deduction when the draft is created:
    - **Deduction ID** on the Header for traceability back to the deduction.
    - **Return reason code** will default to the **Deduction reason**'s **Return reason code** assigned to the deduction.

### Deny a deduction

To deny a deduction:

1. On the Action Pane, in the **Maintain** group, select **Deny**.
1. Select the reason code for the denial. Select **OK** at the top of the **Deny** page and then close the page.
1. In the **Show** field below the Action Pane, select **Closed**. The denied deduction is displayed on the **Deductions** tab, and the remaining amount for the deduction is set to **0.00**.
1. For deductions created using **New deduction** command from the deduction workbench, customer settle, or customer page: The **Denial** fields under References will be updated and if the user selected to create the claim journal when the deduction was created and an invoice has been attached to the deduction which reduced the invoice's balance: The invoice will be detached and the previously attached invoice's remaining balance will be increased again by the rejected claim's amount. The deduction's **Status** has now been set to *Closed* and **Claim status** set to *Rejected*.
1. To reverse the denial, select the deduction record, and then, on the Action Pane, in the **Reverse** group, select **Reverse denial**.

For deductions created using **New deduction** command from the deduction workbench, customer settle, or customer page: The **Denial** fields under References will be updated and the deduction's **Status** has now been set to *Open* and **Claim status** set to *Open*.

### Write off a deduction

To write off a deduction:

1. On the Action Pane, in the **Maintain** group, select **Write-off**.
1. Select the reason code for the write-off. Select **OK** at the top of the **Write-off** page and then close the page.
1. In the **Show** field, select **Closed**. The written-off deduction is displayed on the **Deductions** tab, and the remaining amount for the deduction is set to **0.00**.
1. For deductions created using **New deduction** command from the deduction workbench, customer settle, or customer page and only enabled where **Claim status** is set to *Open*: The **Write-off** fields under References will be updated and if the user selected to create the claim journal when the deduction was created, a claim journal will be posted to the Deduction's Write-off reason code. It can be viewed under **Deduction events** with **Update type** set to *Write-off*. The deduction's **Status** will also be set to *Closed* and **Claim status** set to *Write-off*.
1. To reverse the write-off, select the deduction record, and then, on the Action Pane, in the **Reverse** group, select **Reverse write-off**.

For deductions created using **New deduction** command from the deduction workbench, customer settle, or customer page and only enabled where **Claim status** is set to *Write-off*: The **Write-off** fields under References will be updated and if the user selected to create the claim journal when the deduction was created, a claim journal will be posted to the Deduction's Write-off reason code. It can be viewed under **Deduction events** with **Update type** set to *Reverse write-off*. The deduction's **Status** will also be set to *Open* and **Claim status** set to *Open*.

<a name="credits-outside-approval"></a>

## Credits created outside the Approve deduction process

For deductions created using **New deduction** command from the deduction workbench, customer settle, or customer page.

Different users could have already created a free text, return order, or negative sales order for the customer's claim outside of the **Approve deduction** process. When the existing deduction is approved in the Deduction workbench, the system will automatically create another free text, return order or negative sales order. The following process will describe how you can attach existing credits to a deduction before the deduction is approved to prevent duplicate credits.

### Attach credit to deduction

The following subsections describe how you can attach a credit to a deduction, while on the credit.

Once the credit has been attached to the deduction, it will be available to view using the **Open credit** button on the **Deduction workbench**'s **Open transactions**

In addition, after the credit have been invoiced and the deduction approved, it will be displayed under **Open transactions** as **Claim type** set to *Other credits* against the applicable **Deduction ID**.

### Attach a free text to a deduction

To attach a **free text** to a deduction:

1. Go to **Accounts receivable \> Invoices \> All free text invoices**.
1. Select the applicable posted or draft **Invoice**.
1. On the Action Pane, on the **Invoice** tab, select **Attach credit to deduction**. This is only enabled if the Free text's **Deduction ID** is blank and therefor not already attached to a deduction.
1. The **Attach deduction** page will open, and you can select *one* deduction. Only open *price-based* deductions will be available for selection.
1. Select **OK**. This will populate the **Deduction ID** on the credit's header.

### Attach a return order to a deduction

To attach a return order to a deduction:

1. Go to **Accounts receivable \> Orders \> All return orders**.
1. Select the applicable received or open **RMA number**.
1. On the Action Pane, on the **Return order** tab, select **Attach credit to deduction**. This is only enabled if the Return order's **Deduction ID** is blank and therefor not already attached to a deduction.
1. The **Attach deduction** page will open, and you can select *one* deduction. Only open *quantity-based* deductions will be available for selection.
1. Select **OK**. This will populate the **Deduction ID** on the credit's header.

### Attach a sales order to a deduction

To attach a sales order to a deduction:

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Select the applicable open, delivered or invoices **Sales order**.
1. On the Action Pane, on the **Invoice** tab, select **Attach credit to deduction**. This is only enabled if the **Deduction ID** is blank and therefor not already attached to a deduction.
1. The **Attach deduction** page will open, and you can select *one* deduction. Only open *quantity-based* deductions will be available for selection.
1. Select **OK**. This will populate the **Deduction ID** on the credit's header.

### Detach a deduction from a credit

If the incorrect deduction has been attached, select this option to detach the deduction from the credit. Only enabled for:

- Deduction has a credit attached, and
- **Claim status** is set to *Open*.

The **Detach credit from deduction** option is available from:
    - Free text: On the Action Pane, on the **Invoice** tab, select **Detach credit from deduction**
    - Return order: On the Action Pane, on the **Return order** tab, select **Detach credit from deduction**
    - Sales order: On the Action Pane, on the **Invoice** tab, select **Detach credit from deduction**

### Attach deduction to credit

This section describes how you can attach a deduction to a credit, while on the deduction.

#### Attach a deduction to a free text, return order, or sales order credit

To attach a deduction to a free text, return order, or sales order credit:

1. Go to **Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**.
1. Select the applicable open **Deduction ID**.
1. On the Action Pane, in the **Maintain** group, select **Attach deduction to credit**. This is only enabled where **Claim status** set to *Open*.
1. The **Attach credit** page will open, and you can select *one* credit. The type of credits displayed will depend on the deduction's **Claim basis**:
    - **Price based** – Free text invoices for the customer account with blank **Deduction ID**. Customer requisition will also be displayed since the free text might be unposted and therefor have no number to reference.
    - **Quantity based**, where **Create return order** setting on **[Accounts receivable parameters](#_Configure_Accounts_receivable)** is set to:
        - **Yes** – Return orders for the customer account with blank **Deduction ID**.
        - **No** – Sales order for the customer account with blank **Deduction ID**.
1. Select **OK**. This will populate the **Deduction ID** on the credit's header.

Once the credit has been attached to the deduction, it will be available to view using the **Open credit** button on the **Deduction workbench**'s **Open transactions**

And after the credit have been invoiced and the deduction approved, it will be displayed under **Open transactions** as **Claim type** set to *Other credits* against the applicable **Deduction ID**.

#### To detach a credit from the deduction

If the incorrect credit has been attached, select this option to detach the credit from the deduction. Only enabled for:
    - Deduction that has a credit attached, and
    - **Claim status** is set to *Open*.

On the Action Pane, in the Maintain group, select **Detach deduction from credit**. This removes the **Deduction ID** from the credit.

## Create an end-of-period promotion

Sometimes, you might not have an approved rebate that you can match to a deduction. In this case, you can use the **End of period promotion** feature to match the deduction to a trade allowance that is associated with the customer. The **End of period promotion** feature creates a new trade allowance agreement and a lump sum merchandising event. The feature then matches the lump sum to the deduction and makes the postings that are required to close the deduction.

This feature is useful if you use trade allowances. For more information about trade allowances, see [Working with Trade allowance management](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/working-with-trade-allowance-management).

First, you must set up a template to use to create the new trade allowance agreement. To set up a template, follow these steps.

1. Select **Trade allowance management \> Periodic \> Templates**.
1. On the Action Pane, in the **New** group, select **Templates**.
1. Fill in the fields with the information that should appear in the agreements that are created from the template. For more information about the fields in a trade allowance agreement, see Set up a trade allowance template.
1. On the **Customers** FastTab, in the **Hierarchy** field, select a hierarchy level. In the hierarchy list, select the customer who has an unmatched deduction, and then select **\>**. The customer is added to the **Trade allowance agreement customers** list.
1. Continue to fill in the remaining fields as you require, and then close the page.
1. Select **Trade allowance management \> Setup \> Trade allowance management parameters**.
1. On the **General** FastTab, in the **End of period template** field, select the name of the template to use to create end-of-period promotions.

Next, you can create an end-of-period promotion in the deduction workbench. To create an end-of-period promotion, follow these steps.

1. Select **Trade allowance management \> Common \> Deduction workbench**.
1. Select the **Mark** check box next to the deduction to process.
1. On the Action Pane, in the **Maintain** group, select **End of period promotion**.
1. If you want to associate the deduction with one or more funds, follow these steps:
    1. Select **New**, and then, in the **Fund ID** field, select a fund ID. Repeat this step to add as many funds as you require.
    1. In the **Percent** field next to each fund ID, enter the percentage of the deduction to allocate to the fund. The amounts that you enter in the **Percent** fields must total 100 percent.
1. On the Action Pane, select **OK**. The system creates a new trade allowance agreement that has a lump sum merchandising event and matches the lump sum to the deduction.

## Perform a mass update of deductions

If you have to make the same change to multiple deductions, you can select those deductions and perform a mass update of their fields.

To perform a mass update, follow these steps.

1. Select **Trade allowance management \> Common \> Deduction workbench**.
1. In the **Show** field below the Action Pane, select the type of deductions to view ( **Created**, **Open**, or **Closed** ).
1. Select the **Mark** check box next to each deduction to update. On the Action Pane, in the **Maintain** group, select **Mass update**.
1. The selected deductions are listed in the **Mass update** page. Update the fields as you require, and then select **OK** at the top of the page to accept the changes.
