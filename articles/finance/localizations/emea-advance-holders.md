---
title: Advance holders overview
description: This article provides information about advance holder functionality.
author: AdamTrukawka
ms.date: 09/15/2021
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 262574
ms.collection: get-started
ms.search.form: HcmWorkerAdvHolderTableListPage_RU
---

# Advance holders overview

[!include [banner](../includes/banner.md)]

An *advance holder* is an employee of a company who is accountable for an expense amount that is provided by the organization. Only a company's worker can be an advance holder. When a procurement happens, an advance holder reports to the company about the expenditures that were made. The company reimburses the employee for the expense amount. A company controls a balance for each advance holder. Users in legal entities in Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia can reflect specific transactions accompanying operations with company’s employees who are accountable for the expense amount that is provided by the organization.

## Set up an advance holder
Complete the folloiwng tasks to up an advance holder. Be sure to complete these tasks in the following order.

1. Create advance holder groups.
2. Set up an employee posting profile.
3. Set up account payable parameters.
4. Create a specific terms of payment for the advance holder.
5. Create a specific terms of payment for the advance holder.
6. Create an advance holder.


### Advance holder groups

Use the **Advance holder groups** page to create an advance holder group. You can specify the name, description, and offset account for the advance holder group.
### Employee posting profile

Use the **Employee posting profiles** page to create a profile for advance holder transactions. You can specify the following information for the employee posting profile.

|      Field      |                                            Description                                            |
|-----------------|---------------------------------------------------------------------------------------------------|
| **Posting profile** |  Enter the posting profile identification code for the advance holder.               |
|   **Description**   |  Enter a brief description of the posting profile.                         |
|    **Valid for**    |  Select one of the following options for the level of grouping for setting up the posting profile: <ul> <li>**Table** – This option is used to set up the posting profile for one advance holder. You must indicate the advance holder code in the **Reference** field.</li> <li>**Group** – This option is used to set up the posting profile for a group of advance holders. You must indicate the group code in the **Reference** field.</li> <li>**All** – This option is used to set up the posting profile for all advance holders.</li></ul> |
| **Reference** | Select the advance holder code if **Table** is selected in the **Valid for** field, or select the advance holder group if **Group** is selected in the **Valid for** field. |
| **Summary account** | Select the summary account for posting the transactions. |



### Account payable parameters

To reflect advance holder’s transactions you must set up the following fields on the **Account payable parameters** page in the **Advance holders** section.

|  Field                                         | Description       |
|------------------------------------------------|-------------------|
| **Posting profile**                            | Select the default profile to complete transactions for advance holders.                                                                                                         |
| **Advance holder sorting**                     | If selected, advance holders will be displayed at the beginning of the list in the **Advance holders** page.                                                                     |
| **Issue when balance is open**                 | If selected, issue of a cash advance to an advance holder who has an open positive balance will be allowed.                                                                      |
| **Balance closing via cash field group: Name** | Select the cash slip journal code. This journal code is used to generate cash disbursement slips and reimbursement slips when closing an advance holder’s balances through cash. |
| **Cash**                                       | Select the cash account to determine the vouchers that are used for closing the balances for the advance holder.                                                                 |
| **Balance closing via bank field group: Name** | Select the journal code for transactions to close the balances through a bank.                                                                                                   |
| **Account type**                               | Select a bank to close the balances for an advance holder through a bank.                                                                                                        |
| **Main account**                               | Select a bank account code to close the balances for an advance holder through a bank.                                                                                           |

### Terms of payment for advance holder

To correctly register and post a purchase order through an advance holder, you must use a Terms of payment that was set up with the **From advance holder** option set to **True**.

### Create an advance holder

Before you can create an advance holder, you must have already set up workers. For more information, see [Enter worker information (Task guide)](../../human-resources/hr-personnel-enter-worker-information.md). 

1. Go to **Accounts payable** > **Advance holders** > **Advance holders**.

    > [!NOTE]
    > You can't add or delete employees on the **Advance holders** page. Employees must first be hired in the **Human resources** module. On the **Employee posting profiles** page, you can set up the employee posting profile that is used to post advance holder balances.

2. Select an employee, and then select **Edit**.
3. On the **General** FastTab, set the **Advance holder** option to **Yes** to indicate that the employee is an advance holder.
4. In the **Group** field, select the advance holder group that the employee belongs to.
5. Under **Identity document**, provide the details of an identification document.
    - **Series**: Enter the series of the document that is used to verify the identity of the advance holder.
    - **Number**: Enter the number of the document that is used to verify the identity of the advance holder.
    - **Issue date**: Select or enter the document issue date.
    - **Issued by**: Enter the details of the authority or person who issued the document.
6. Select **Save**, or close the page.

> [!NOTE]
> If the **Advance holder sorting** option is set to **Yes** on the **Accounts payable parameters** page, advance holders appear at the top of the grid on the **Advance holders** page.


## Advance holder inquiries and reports

### Advance holder transactions inquiry

For a list of transactions for an advance holder, select **Transactions** on the **Advance holders** page. To see transactions for all advance holders or to create a specific inquiry based on advance holders’ transactions, go to **Accounts payable** > **Inquiries and reports** > **Advance holders inquiries and reports** > **Transactions**. Select **Voucher** to open the **Voucher transactions** page.

### Advance holder balance inquiry

To see balance for an Advance holder use the **Advance holders** page. To see balance for all advance holders or to create a specific inquiry based on advance holders’ accounts, click **Accounts payable** &gt; **Inquiries and reports** &gt; **Advance holders inquiries and reports** &gt; **Balance.**
### Advance holder balance report

To preview and print a report based on information about advance holders’ balance, click **Accounts payable** &gt; **Inquiries and reports** &gt; **Advance holders inquiries and reports** &gt; **Advance holder balance report**.
### Advance holder transactions report

To preview and print a report based on advance holders’ transactions, click **Accounts payable** &gt; **Inquiries and reports** &gt; **Advance holders inquiries and reports** &gt; **Advance holder transactions report**.

## Advance holder transactions

Transactions for workers who are advance holders can be posted by using advance holder accounts. The worker ID that is specified for each advance holder can be used to track all advance holder transactions. This number is retrieved as an account number for advance holder transactions on the **General journals** and **Advance holder transactions** pages.

### Create and post a purchase order with advance holder details
For more general information about purchase orders, see [Purchase order overview](../../supply-chain/procurement/purchase-order-overview.md). If a vendor invoice is created and posted with advance holder details, the advance holder’s balances will be posted to the employee balance account instead of the vendor balance account. To add advance holder details to a purchase order, do the following:

1. In the **Terms of payment** field in the **Price and discount** section, select the payment term. For more information about **Terms of payment**, see [Define vendor payment terms](../accounts-payable/tasks/define-vendor-payment-terms.md). 
2. Select a payment term that has the **From advance holder** option selected on the **Terms of payment** page. 
3. On the **Price and discount** FastTab, in the **Advance holder** field, select the advance holder for the purchase order.

The purchase order posting process creates two vendor transactions with opposite amounts and one advance holder transaction. Without advance holder details, only one vendor transaction is created.

### Settle advance holder balances by using the bank
When you settle advance holder balances by using the bank, journal entries for closing the advance holder balances are created in the general journal. You can set up the code for the journal and the bank in the **Advance holders** section on the **Accounts payable parameters** page. 

1. To close an advance holder’s balance by using the bank, go to **Accounts payable** > **Advance holders** > **Advance holders**. 
2. On the Action PAne, select **Balance** > **Close via bank**. 
3. Enter the following information on the **Close via bank** page.

    | Field                    | Description |
    |------------------------------|-------------------|
    | **Date of payment**          | Enter the date that the payment should be posted.|
    | **Amount to be transferred** | Enter the balance amount while closing. The amount that is indicated in the **Amount** field on the **Balance** page is displayed by default. |
    | **Automatic**                | Select the **Automatic** check box to automatically create and post a journal that is preset on the **Accounts payable parameters** page.|

### Settle advance holder balances by using cash
When you settle advance holder balances by using cash, journal entries for closing the advance holder balances are created in a slip journal. You can set up the code for the journal and the cash in the **Advance holders** tab on the **Accounts payable parameters** page. 

1. To close an advance holder’s balance using cash, go to **Accounts payable** > **Advance holders** > **Advance holders**. 
2. On the Action Pane, select **Balance** > **Close via cash**. 
3. Enter the following information on the **Close via cash** page.

    | Field                    | Description
    |------------------------------|-----------------|
    | **Date of payment**          | Enter the date that the payment should be posted.|
    | **Amount to be transferred** | Enter the balance amount while closing. The amount that is indicated in the **Amount** field on the **Balance** page is displayed by default. |
    | **Automatic**                | Select the **Automatic** check box to automatically create and post a journal that is preset on the **Accounts payable parameters** page.     |

After the slip journal is processed, if the amount in the **Amount to be transferred** field was negative, a disbursement slip is generated for the advance holder when the balances are closed. If the amount in the **Amount to be transferred** field was positive, a reimbursement slip is generated.

## Additional resources

- [Advance payment to an employee (Eastern Europe)](tasks/advance-payment-employee.md)
- [Advance holders for Russia overview](rus-advance-holders.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
