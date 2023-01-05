---
# required metadata

title: Cash management overview
description: This article provides an overview of the cash management capabilities in Microsoft Dynamics 365 Commerce POS, focusing on the cash traceability capability of two-sided transactions.
author: ShalabhjainMSFT
ms.date: 01/04/2023
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

This article provides an overview of the cash management capabilities in Microsoft Dynamics 365 Commerce point of sale (POS), focusing on the cash traceability capability of two-sided transactions.

Cash management is a key function for retailers in physical stores. Retailers want their stores to have systems that can help them provide complete traceability and accountability of cash and its movement across the different registers and cashiers in a store. They must be able to reconcile any differences and determine accountability.

Microsoft Dynamics 365 Commerce provides cash management capabilities in its point of sale (POS) application. Retailers have two cash management options:

- **One-sided cash transactions** - This option enables retailers to reconcile the cash for a store, but doesn't allow them to precisely determine accountability in the event of a cash discrepancy. Once performed, a one-sided cash transaction requires no further action since it is considered completed.
- **Two-sided cash transactions** This option enables the cash traceability capability, which enforces two-sided cash transactions and helps determine accountability for all cash movements. When a cashier performs an operation (for example, tender removal), the other cashier who receives the money must reconcile this action to ensure that the amount of the transaction is correct.

> [!NOTE]
> As a prerequisite for better understanding this article, first see [Shift and cash drawer management](shift-drawer-management.md).

## Set up cash traceability functionality

To set up cash traceability functionality by configuring the functionality profile for stores, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select a functionality profile that is linked to the stores where you want to set up cash traceability functionality.
1. In the **Functions** section of the functionality profile, under **Advanced cash management**, set the **Enable cash traceability** option to **Yes**.

> [!NOTE]
> To use the cash traceability functionality, you must first set up one or more safes for the store. This is because the system expects a safe to be selected for the "Declare start amount" and "Safe drop" actions.

### Set up a safe

You can define and maintain multiple safes for a store.

To set up a safe in Commerce headquarters, follow these steps.
	
1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. Select the **Retail Channel ID** of the store for which you want to set up a safe.
1. On the Action Pane of the store page, select the **Set up** tab. 
1. in the **Set up** group, select **Safes**. 
1. On the **Safe declaration** page, select **+New**.
1. Under **Name**, enter a name for the safe. 
1. To add additional safes, repeat steps 5 and 6 for each new safe. 
1. Run the **1070 Channel configuration** distribution schedule job to sync the safe configurations to the channel database.

## How cash management is handled when the cash traceability feature is enabled

Cash management is handled in the following ways when the cash traceability feature is enabled.

- A user who runs a "Declare start amount" operation must enter the source of cash. The user can search for the available safes that are defined in the store and select the safe that the cash is being taken out of so that it can be put into the register. 
- A user who runs a "Tender removal" operation is prompted to select from a list of open "Float entry" transactions. If the corresponding float entry doesn't exist in the system, the user can create a non-linked tender removal transaction.
- A user who runs a "Float entry" operation is prompted to select from a list of open "Tender removal" transactions. If the corresponding tender removal doesn't exist in the system, the user can create a non-linked float entry transaction.
- A user who runs a "Safe drop" operation is prompted to select the safe where the cash is being dropped.

## Transaction reconciliation

When a user chooses to close a shift, the system validates that there are no unreconciled cash management transactions in the shift. A shift can't be closed if there are unreconciled transactions. 

A transaction can be reconciled systematically or manually. 

### Systematic transaction reconciliation

Systematic transaction reconciliation occurs when transactions are automatically reconciled once certain actions are taken. 

For example, when a user performs a cash management operation (such as **Tender removal**) for $20 on shift 1 to be sent to shift 2, when the user on shift 2 performs a **Float entry** operation and selects the transaction, the two transactions are systematically reconciled. 
		
### Manual transaction reconciliation

Manual transaction reconciliation is needed when systematic transaction reconciliation does not occur.

Continuing with the example above, if the user on shift 2 doesn't perform a **Float entry** action, or doesn't choose the correct transaction during the **Float entry** action, then the tender removal action remains unreconciled and requires manual reconciliation. 

To perform a manual reconciliation within a shift or across shifts, users with the necessary permissions can perform the **Manage shifts** operation. The **Manage shifts** view makes it easy to view shifts with unreconciled transactions. The user can select a shift and select **Reconcile** to view a list of reconciled and unreconciled transactions on separate tabs. Users can then either select unreconciled transactions and reconcile them, or select previously reconciled transactions and unreconcile them. During reconciliation, if the selected transaction doesn't balance, the user must enter a description of the reason for the unbalanced reconciliation. Users can continue to reconcile and unreconcile transactions until the shift is closed. However, transactions can't be unreconciled after a shift is closed.

## Safe management

In Dynamics 365 Commerce, cash reconciliation can only be done at the shift level. To to manage cash in a safe, the safe must be managed via a shift. 

> [!IMPORTANT]
> It's required to have a dedicated register for safe management that isn't used for any sale transactions.

A sample business process for cash management using a safe is explained below.

At the start of the day, the store manager declares the start amount in the safe. To do so, the store manager must do the following:
    1. Open a shift in a dedicated register for the safe.
    1. Navigate to the **Manage safe** operation, select a safe, and then select **Declare start amount**.
    1. Enter the amount, and then select **Save**.

When the cashier is ready to start the day, they open the shift and get the starting amount from the safe via the store manager. To do so, the cashier and the store manager must do the following:
    1. The cashier opens the shift on a register (for example, Shift A).
    1. The store manager navigates to the **Manage safe** operation on the dedicated register for the safe, performs the **Tender removal** operation, and selects the correct amount and shift for this removal. It's important that the shift is opened on the register to which the money is being transferred from the safe.
    1. The cashier takes the money, performs a **Declare start amount** operation on their register, and selects the transaction created above to reflect the start amount. These actions systematically reconcile the two transactions.

The cashier performs the regular sale transactions throughout the day.

When the cash in the cash drawer is above the defined limit, the cashier is notified about the excess cash and the cashier performs a safe drop. To do so, the cashier and the store manager must do the following:
    1. Select the **Safe drop** button, enter the amount, and select the safe to drop the money into.
    1. The cashier hands over the money to store manager, or drops it in the safe.
    1. The store manager counts the money and then navigates to the **Manage safe** operation on the dedicated register for the safe.
    1. The store manager selects the safe, selects the **Float entry** button, and then selects the transaction created above. This systematically reconciles the two transactions.

At the end of the day, the cashier drops the entire amount of cash in the cash drawer to the safe, declares the tender, and blind closes the shift. To do so, the cashier must do the following:
    1. Select the **Safe drop** button, enter the amount, and select the safe to drop the money into.
    1. Select the **Tender declaration** button, and then select the amount as "0" (zero).
    1. Select the **Blind close** button to blind close the shift.
    1. Hand over the money to the store manager, or drop it in the safe.

The manager reconciles the last safe drop transaction, performs a bank drop, and closes both of the shifts (the cashier's shift and the shift for the safe). To do so, the store manager must do the following:
    1. Navigate to the **Manage safe** operation on the dedicated register for the safe.
    1. Select a safe, select the **Float entry** button, and then select the transaction created above. This systematically reconciles the two transactions.
    1. For the selected safe, select the **Bank drop** button, and then select the money to be dropped into the bank.
    1. Navigate out of the **Manage safe** operation, and then select the **Tender declaration** button to declare the balance in the safe.
    1. Navigate to the **"Manage shifts"** operation, select the blind closed shift for the cashier, and then close the shift. The shift on the dedicated register for the safe will show one unreconciled transaction ("Declare start amount) performed for the safe. This transaction can't be systematically reconciled because this money is expected to be added from an external source (for example, a bank) and so must be manually reconciled. The store manager selects the unreconciled transaction and then closes the shift.
		
> [!IMPORTANT]
> - Any money left in the safe by the end of the day is not automatically carried over the next day. The store manager must declare the start amount in the safe the next day.
> - For all safe-related actions, the user must use the **Manage safe** operation since that is the only way to select the safe for which the cash transactions are recorded. The **Declare start amount**, **Float entry**, **Tender removal** and **Bank drop** operations must be performed in the context of the safe. 
> - Before the shift associated with the safe can be closed, the user must perform the **Tender declaration** operation on the dedicated register for the safe. This is the only operation that does not take place in the context of a safe, so this operation is not available in the **Manage safe** operation. If the same register is used to manage multiple safes, then the tender declaration should be the sum of the money in all these safes.
> - The **Declare start amount** operation on the safe is not reconciled automatically and must be reconciled manually.
> - The **Declare start amount** operation is available at two levels within the **Manage safe** operation: the **shift** level and the **safe** level. On the dedicated register for the safe, to declare the start amount for a safe the user must run the **Declare start amount** operation within the **Manage safe** operation. The one at the shift level can be used if there is any additional money in the cash drawer associated with this register.
> - To transfer money in either direction between a safe and a shift, the shift must be opened on the register that is sending or receiving the money. In the example used above for Safe management, the shift A is required to be open before the money can be transferred from the safe to this shift.
> - If the cash traceability feature is enabled, then the user can to do a safe drop by selecting a single tender type in one transaction. If the cash drawer includes multiple tenders (for example, cash (USD), cash (CAD), and check), then the user must perform one safe drop per tender type. 
> - The system supports posting the safe drops and bank drops into respective general ledger (GL) accounts as defined on the **Store \> Payment methods \> Tender** form in headquarters. When the money is moved from the safe to the bank using the bank drop operation, the money is reduced from the safe drop GL and increased in the bank drop GL. Although amounts dropped to the safe are recorded in the safe drop GL, money moving out of the safe does not update this GL. Other cash management transactions (for example, **Float entry** and **Tender removal**) are not recorded in any specific GL.

## Financial reconciliation in store

When cash management transactions are processed in headquarters, the parameters defined on the **Statement/closing** section of the **All stores** page are used to perform validations on those transactions. However, if the user enables the following configurations, the POS user will see the result of these validations in POS when they attempt to close the shift, as shown in the following example image of the financial reconciliation view.
	
![Financial reconciliation in store](media/FinancialReconciliation.png)

To set up the financial reconciliation functionality in headquarters, follow these steps.

1. In the Feature management workspace, turn on the **Retail statements - Trickle feed** feature.
1. In the POS functionality profile for the appropriate store, set the **Enable financial reconciliation in store** option to **Yes**.

For more information on the financial reconciliation functionality, see [Financial reconciliation in store](fin-recon.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
