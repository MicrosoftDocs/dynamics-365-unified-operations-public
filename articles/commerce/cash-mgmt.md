---
# required metadata

title: Cash management overview
description: This article provides an overview of the cash management capabilities in Microsoft Dynamics 365 Commerce POS. It also provides guidance about setting up the cash traceability capability for two-sided transactions.
author: ShalabhjainMSFT
ms.date: 01/06/2023
ms.topic: overview
audience: Application User
ms.reviewer: v-chgriffin
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-05-21

---

# Cash management overview

[!include [banner](includes/banner.md)]

This article provides an overview of the cash management capabilities in Microsoft Dynamics 365 Commerce point of sale (POS). It also provides guidance about setting up the cash traceability capability for two-sided transactions.

> [!NOTE]
> For background information about the cash management capabilities in Commerce, see [Shift and cash drawer management](shift-drawer-management.md).

Cash management is a key function for retailers in physical stores. Retailers want their stores to have systems that can help provide complete traceability and accountability of cash and its movement across the different registers and cashiers in a store. They must be able to reconcile any differences and determine accountability.

Dynamics 365 Commerce provides cash management capabilities in its POS application. Retailers have two cash management options:

- **One-sided cash transactions** – This option lets retailers reconcile the cash for a store, but it doesn't let them precisely determine accountability in the event of a cash discrepancy. After a one-sided cash transaction is run, it requires no further action because it's considered completed.
- **Two-sided cash transactions** – This option enables the cash traceability capability, which enforces two-sided cash transactions and helps determine accountability for all cash movements. When a cashier performs an operation (for example, **Tender removal**), the other cashier who receives the money must reconcile this action to ensure that the amount of the transaction is correct.

## Set up cash traceability functionality

To set up cash traceability functionality by configuring the functionality profile for stores, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select a functionality profile that's linked to the stores that you want to set up cash traceability functionality for.
1. In the **Functions** section of the functionality profile, under **Advanced cash management**, set the **Enable cash traceability** option to **Yes**.

> [!NOTE]
> To use the cash traceability functionality, you must first set up one or more safes for the store. This setup is required because the system expects a safe to be selected for the **Declare start amount** and **Safe drop** operations.

### Set up a safe

You can define and maintain multiple safes for a store.

To set up a safe in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. In the **Retail Channel ID** field, select the retail channel ID of the store that you want to set up a safe for.
1. On the Action Pane, on the **Set up** tab, in the **Set up** group, select **Safes**.
1. On the **Safe declaration** page, select **New**.
1. In the **Name** field, enter a name for the safe.
1. Repeat steps 4 and 5 for each additional safe that you want to add.
1. Run the **1070 Channel configuration** distribution schedule job to sync the safe configurations to the channel database.

## How cash management is handled when the cash traceability feature is enabled

Cash management is handled in the following ways when the cash traceability feature is enabled:

- A user who runs a **Declare start amount** operation must enter the source of cash. The user can search for the available safes that are defined in the store. They can then select the safe that the cash is being taken out of so that it can be put into the register.
- A user who runs a **Tender removal** operation is prompted to select from a list of open float entry transactions. If the corresponding float entry doesn't exist in the system, the user can create a non-linked tender removal transaction.
- A user who runs a **Float entry** operation is prompted to select from a list of open tender removal transactions. If the corresponding tender removal doesn't exist in the system, the user can create a non-linked float entry transaction.
- A user who runs a **Safe drop** operation is prompted to select the safe where the cash is being dropped.

## Transaction reconciliation

When a user chooses to close a shift, the system validates that there are no unreconciled cash management transactions in the shift. A shift can't be closed if there are unreconciled transactions.

Transactions can be reconciled either automatically by the system or manually by the user.

### Automatic transaction reconciliation

Automatic transaction reconciliation occurs when the system automatically reconciles transactions after specific actions are taken.

For example, a user performs a cash management operation (such as **Tender removal**) in shift A to send $20 to shift B. When the user in shift B performs a **Float entry** operation and selects the transaction, the two transactions are automatically reconciled.

### Manual transaction reconciliation

Manual transaction reconciliation is required when automatic transaction reconciliation doesn't occur.

For the previous example, if the user in shift B doesn't perform a **Float entry** operation or doesn't select the correct transaction during the **Float entry** operation, the tender removal action remains unreconciled and requires manual reconciliation.

To perform a manual reconciliation within a shift or across shifts, users who have the necessary permissions can perform the **Manage shifts** operation. The **Manage shifts** view makes it easy to view shifts that have unreconciled transactions. The user can select a shift and then select **Reconcile** to view a list of reconciled and unreconciled transactions on separate tabs. The user can then either select unreconciled transactions and reconcile them, or select previously reconciled transactions and unreconcile them. During reconciliation, if a selected transaction doesn't balance, the user must enter a description of the reason for the unbalanced reconciliation. The user can continue to reconcile and unreconcile transactions until the shift is closed. However, transactions can't be unreconciled after a shift is closed.

## Safe management

In Dynamics 365 Commerce, cash reconciliation can be done only at the shift level. To manage cash in a safe, you must manage the safe via a shift.

> [!IMPORTANT]
> Safe management requires a dedicated register that isn't used for any sales transactions.

### Example business process for cash management using a safe

The following example outlines the business process for cash management that uses a safe.

At the start of the day, the store manager declares the start amount in the safe. Here are the steps that the store manager must follow.

1. Open a shift on the dedicated register for the safe.
1. Go to the **Manage safe** operation, select a safe, and then select **Declare start amount**.
1. Enter the amount, and then select **Save**.

When the cashier is ready to start the day, they open the shift and get the starting amount from the safe via the store manager. Here are the steps that the cashier and the store manager must follow.

1. The cashier opens the shift on a register (for example, shift A).
1. The store manager goes to the **Manage safe** operation on the dedicated register for the safe, performs the **Tender removal** operation, and selects the correct amount and shift for the removal. It's important that the shift is opened on the register that the money from the safe is being transferred to.
1. The cashier takes the money, performs a **Declare start amount** operation on their register, and selects the transaction that was created earlier to reflect the start amount. These actions trigger the automatic reconciliation of the two transactions.

The cashier then runs regular sale transactions throughout the day.

When the cash in the cash drawer is above the defined limit, the cashier is notified about the excess cash and performs a safe drop. Here are the steps that the cashier and the store manager must follow.

1. The cashier hands the money to the store manager. Alternatively, the cashier drops the money into the safe by selecting **Safe drop**, entering the amount, and selecting the safe to drop the money into.
1. The store manager counts the money and then goes to the **Manage safe** operation on the dedicated register for the safe.
1. The store manager selects the safe, selects **Float entry**, and then selects the transaction that was created earlier. These actions trigger the automatic reconciliation of the two transactions.

At the end of the day, the cashier drops the whole amount of cash in the cash drawer into the safe, declares the tender, and [blind-closes](shift-drawer-management.md#blind-close-shift) the shift. Here are the steps that the cashier must follow.

1. Select **Safe drop**, enter the amount, and select the safe to drop the money into.
1. Select **Tender declaration**, and then select **0** (zero) as the amount.
1. Select **Blind close** to blind-close the shift.
1. Hand the money to the store manager, or drop it into the safe.

The manager reconciles the last safe drop transaction, performs a bank drop, and closes both shifts (the cashier's shift and the shift for the safe). Here are the steps that the store manager must follow.

1. Go to the **Manage safe** operation on the dedicated register for the safe.
1. Select a safe, select **Float entry**, and then select the transaction that was created earlier. These actions trigger the automatic reconciliation of the two transactions.
1. For the selected safe, select **Bank drop**, and then select the money that must be dropped into the bank.
1. Exit the **Manage safe** operation, and then select **Tender declaration** to declare the balance in the safe.
1. Go to the **Manage shifts** operation, select the blind-closed shift for the cashier, and then close the shift. The shift on the dedicated register for the safe will now show one unreconciled transaction (**Declare start amount**) that was performed for the safe. Because the money is expected to be added from an external source (such as a bank), this transaction can't be automatically reconciled. It must be manually reconciled. The store manager selects the unreconciled transaction and then closes the shift.

### Important notes about safe management

- Money that's left in the safe at the end of the day isn't automatically carried over to the next day. The store manager must declare the start amount in the safe on the next day.
- For all safe-related actions, the user must use the **Manage safe** operation. There's no other way to select the safe that the cash transactions are recorded for. The **Declare start amount**, **Float entry**, **Tender removal**, and **Bank drop** operations must be performed in the context of the **Manage safe** operation.
- Before the shift that's associated with the safe can be closed, the user must perform the **Tender declaration** operation on the dedicated register for the safe. This operation is the only one that doesn't occur in the context of a safe. Therefore, it isn't available in the **Manage safe** operation. If the same register is used to manage multiple safes, the tender declaration should be the sum of the money in all those safes.
- The **Declare start amount** operation on the safe isn't automatically reconciled. It must be manually reconciled.
- The **Declare start amount** operation is available at two levels in the **Manage safe** operation: the shift level and the safe level. To declare the start amount for a safe on the dedicated register for that safe, the user must run the **Declare start amount** operation in the **Manage safe** operation. The **Declare start amount** operation at the shift level can be used if there's any additional money in the cash drawer that's associated with that register.
- To transfer money in either direction between a safe and a shift, the shift must be opened on the register that's sending or receiving the money. In the preceding example for [safe management](#safe-management), shift A must be open before the money can be transferred from the safe to that shift.
- If the cash traceability feature is enabled, the user can do a safe drop by selecting a single tender type in one transaction. If the cash drawer includes multiple tenders (for example, cash in US dollars \[USD\], cash in Canadian dollars \[CAD\], and check), the user must perform one safe drop per tender type.
- The system supports posting the safe drops and bank drops into the appropriate general ledger (GL) accounts, as defined on the **Tender** page in Commerce headquarters (**Store \> Payment methods \> Tender**). When the **Bank drop** operation is used to move money from the safe to the bank, the money is reduced from the safe drop GL and increased in the bank drop GL. Although amounts that are dropped into the safe are recorded in the safe drop GL, money that's moved out of the safe doesn't update this GL. Other cash management transactions (for example, **Float entry** and **Tender removal**) aren't recorded in any specific GL.

## Financial reconciliation in store

When cash management transactions are processed in headquarters, the parameters that are defined in the **Statement/closing** section of the **All stores** page are used to perform validations on those transactions. However, if the user enables the financial reconciliation functionality in headquarters, the POS user will see the result of these validations in POS when they try to close the shift.

To set up the financial reconciliation functionality in headquarters, follow these steps.

1. In the **Feature management** workspace, turn on the **Retail statements - Trickle feed** feature.
1. In the POS functionality profile for the appropriate store, set the **Enable financial reconciliation in store** option to **Yes**.

For more information about the financial reconciliation functionality, see [Financial reconciliation in store](fin-recon.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
