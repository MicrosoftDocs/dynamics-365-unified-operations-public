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

When a user chooses to close a shift, the system validates that there are no unreconciled cash management transactions in the shift. A shift cannot be closed if there are unreconciled transactions. 

A transaction can be reconciled systematically or manually. 

### Systematic transaction reconciliation

Let's use an example to understand systematic transaction reconciliation. When a user performs a cash management operation e.g. "Tender removal" for $20 on shift 1 to be sent to shift 2, then, when the user on shift 2 performs a "Float entry" action and chooses the above transaction, then these two transactions are systematically reconciled. 
		
### Manual transaction reconciliation

Referring to the above example, if the user on shift 2 does not perform a float entry action or does not choose the correct transaction during float entry, then this tender removal action would remain unreconciled and thus would need manual reconciliation. To perform a manual reconciliation within a shift or across shifts, the users, with the necessary permissions, can use the **"Manage shifts"** operation. This view makes it easy to view shifts with unreconciled transactions. The user can select a shift and press **Reconcile** button to view a list of reconciled and unreconciled transactions on separate tabs. From this view, users can either select unreconciled transactions and reconcile them, or select previously reconciled transactions and unreconcile them. During reconciliation, if the selected transaction doesn't balance, the user must enter a description of the reason for the unbalanced reconciliation. Users can continue to reconcile and unreconcile transactions until the shift is closed. However, after a shift is closed, the transactions can't be unreconciled.

## Safe management

In Dynamics 365 Commerce, the cash reconciliation can only be done at a shift level. So to manage cash in a safe, the safe must be managed via a shift. Additionally, it is required to have a dedicated register for safe management such that this register is not used for any sale transactions. 

> [!IMPORTANT]
> A dedicated register for a safe is required and this register should not be used for sale transactions

A sample business process for cash management using safe is explained below:
- At the start of the day, the store manager declares the start amount in the safe. To do so, the store manager needs to do the following:
    - Open a shift in a dedicated register for the safe
    - Navigate to the "Manage safe" operation, select a safe and press the "Declare start amount" button
    - Enter the amount and save

- When the cashier is ready to start the day, they open the shift and get the starting amount from the safe via store manager. To do so, the cashier and the store manager needs to do the following:
    - The cashier needs to open the shift on a register e.g. Shift A
    - The store manager would navigate to the "Manage safe" operation on the dedicated register for safe and perform the "Tender removal" operation and choose the right amount and the right shift i.e. Shift A for this removal. **Note:** It is important that the shift is opened on the register to which the money is being transferred from the safe.
    - The cashier would take the money and perform a "Declare start amount" on their register and choose the transaction created above to reflect the start amount. This will systematically reconcile the two transactions

- The cashier performs the regular sale transactions throughout the day
- When the cash is the cash drawer is above the defined limit, the cashier is notified about the excess cash and the cashier performs a safe drop. To do so, the cashier needs to do the following:
    - Press the "Safe drop" button, enter the amount and select safe to drop the money
    - Hand over the money to store manager or drop it in the safe
    - The store manager would count the money and then navigate to the "Manage safe" operation on the dedicated register for the safe
    - Select the safe, press the "Float entry" button and select the transaction created above. This will systematically reconcile the two transactions.

- At the end of the day, the cashier drops the entire cash from the cash drawer to the safe, declares the tender and blind closes the shift. To do so, the cashier needs to do the following:
    - Press the "Safe drop" button, enter the amount and select safe to drop the money.
    - Press the "Tender declaration" button and select the amount as 0.
    - Press the "Blind close" button to blind close the shift.
    - Hand over the money to store manager or drop it in the safe.

- The manager reconciles the last safe drop transaction, performs a bank drop and closes both the shifts i.e. the cashier's shift and the shift for the safe. To do so, the store manager needs to do the following:
    - Navigate to the "Manage safe" operation on the dedicated register for the safe.
    - Select a safe, press the "Float entry" button and select the transaction created above. This will systematically reconcile the two transactions.
    - For the selected safe, press the "Bank drop" button and select the money to be dropped at the bank
    - Navigate out of the "Manage safe" operation and **press the "Tender declaration" button to declare the balance in the safe**
    - Navigate to the **"Manage shifts"** operation and select the blind closed shift for the cashier and close the shift
    - The shift on the dedicated register for the safe will show one unreconciled transaction i.e. "Declare start amount" transaction performed for the safe. This transaction cannot be systematically reconciled because this money is expected to be added from an external source e.g. a Bank and thus this needs to be manually reconciled. The store manager would select the unreconciled transaction and then close the shift
		
**A few important things to note:**
- Any money left in the safe by the end of the day is not automatically carried over the next day. The store manager needs to declare the start amount in the safe the next day.
- For all safe related actions, the user must use the "Manage safe" operation as this is the only way to select the safe for which the cash transactions are recorded. Thus, the "Declare start amount", "Float entry", "Tender removal" and "Bank drop" operations must be performed in the context of the safe. 
- Before the shift associated with the safe can be closed, the user must perform the **"Tender declaration"** on the dedicated register for the safe. This is the only operation that does not have to be in the context of a safe and thus this operation is not available in the "Manage safe" operation. If there the same register is used to manage multiple safes, then the tender declaration should be a sum of the money in all these safes.
- The "Declare start amount" operation on the safe is not reconciled automatically and thus it needs manual reconciliation
- The "Declare start amount" operation is available at two levels i.e. at the **shift** level and at the **safe** level (within the "Manage safe" operation). On the dedicated register for the safe, to declare the start amount for a safe, the user must use the "Declare start amount" within the "Manage safe" operation. The one at the shift level can be used if there is any additional money in the cash drawer associated with this register.
- To transfer the money to or from safe to a shift, it is required that the shift is opened on the register which is sending or receiving the money. In the example used above for Safe management, the shift A is required to be open before the money could be transferred from Safe to this shift.
- If the cash traceability feature is enabled, then the user can to do a safe drop by selecting a single tender type in one transaction. Thus, if the cash drawer includes multiple tenders e.g. Cash (USD), Cash (CAD), Check, then the user needs to perform one safe drop per tender type. 
- The system supports posting the safe drops and bank drops into respective General Ledger (GL) accounts as defined on the **Store** -> "Payment methods" -> Tender (e.g. Cash) form in HQ. When the money is moved from safe to bank using the bank drop operation, the money is reduced from the safe drop GL and increased in the bank drop GL. However, there is a limitation that only the amounts that are dropped to the safe are recorded in safe drop GL, but the money moving out of the safe does not update this GL. Secondly, other cash management transactions e.g. Float entry and Tender removal are not recorded in any specific GL.

## Financial reconciliation in store

When these cash management transactions are processed in the Commerce Headquarters (HQ) the parameters defined on the **Statement/closing** section of the **All stores** page in HQ are used to perform validations on these transactions. However, if the user enables the following configurations, the POS user will see the result of these validations in POS when they attempt to close the shift. Refer the below image showing the financial reconciliation view.
	
![Financial reconciliation in store](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Shalabh_cashmanagement/articles/commerce/media/FinancialReconciliation.png)

- In the Feature management workspace, turn on the **Retail statements - Trickle feed feature.**
- In the POS functionality profile for the appropriate store, set the **Enable financial reconciliation in store** option to **Yes**.

Please refer the following link for more details on this feature: [Financial reconcialiation in store](fin-recon.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
