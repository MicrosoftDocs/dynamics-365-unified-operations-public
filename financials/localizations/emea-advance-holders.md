---
# required metadata

title: Advance holders
description: Learn about advance holder functionality in Microsoft Dynamics 365 for Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-12 21 - 45 - 42
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 262574
ms.assetid: 87924785-6032-4125-8279-5b1a758f4d80
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Advance holders

Learn about advance holder functionality in Microsoft Dynamics 365 for Operations.

An *advance holder* is an employee of a company who is accountable for an expense amount that is provided by the organization. Only a company's worker can be an advance holder. When a procurement happens, an advance holder reports to the company about the expenditures that were made. The company reimburses the employee for the expense amount. A company controls a balance for each advance holder. Users in legal entities in Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia can reflect specific transactions accompanying operations with company’s employees who are accountable for the expense amount that is provided by the organization.

## Set up an advance holder
To set up an advance holder, the following tasks should be completed in order.
1.  Create advance holder groups.
2.  Set up an employee posting profile.
3.  Set up account payable parameters.
4.  Create a specific terms of payment for the advance holder.
5.  Create an advance holder.

### Advance holder groups

Use the **Advance holder groups** page to create an advance holder group. You can specify the name, description, and offset account for the advance holder group.
### Employee posting profile

Use the **Employee posting profiles** page to create a profile for advance holder transactions. You can specify the following information for the employee posting profile.
|Field |Description|
|------|-----------|
|Posting profile|Enter the posting profile identification code for the advance holder.|
|Description|Enter a brief description of the posting profile.|
|Valid for|Select one of the following options for the level of grouping for setting up the posting profile: 
**Table** – This option is used to set up the posting profile for one advance holder. You must indicate the advance holder code in the Reference field.
**Group** – This option is used to set up the posting profile for a group of advance holders. You must indicate the group code in the Reference field.
**All** – This option is used to set up the posting profile for all advance holders.|
|Reference|Select the advance holder code if Table is selected in the Valid for field, or select the advance holder group if Group is selected in the Valid for field.|
|Summary account|Select the summary account for posting the transactions.|



### Account payable parameters

To reflect advance holder’s transactions you must set up the following on the **Account payable parameters** page in the **Advance holders** section.
|                                                |                   |
|------------------------------------------------|-------------------|
|  **Field**                                     | **Description**                                                                                                                                                                  |
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
### Create an advance holder creation

Before you can create an advance holder, you must have already set up workers. For more information, see [Enter worker information (Task guide).](http://ax.help.dynamics.com/en/wiki/enter-worker-information/) Use the **Advance holders** page to set up a worker as an advance holder. Select the worker to use as an advance holder, click **Edit**, and then set the **Advance holder** option to **True**. You must also complete the following fields.
|                |                                                                                             |
|----------------|---------------------------------------------------------------------------------------------|
| **Field**      | **Description**                                                                             |
| **Group**      | Select an advance holder group.                                                             |
| **Series**     | Enter the series of the document that is used to verify the identity of the advance holder. |
| **Number**     | Enter the number of the document that is used to verify the identity of the advance holder. |
| **Issue date** | Select or enter the document issue date.                                                    |
| **Issued by**  | Enter the details of the authority or person who issued the document.                       |

## Advance holder inquiries and reports
### Advance holder transactions inquiry

For a list of transactions for an advance holder, click the **Transactions** button on the **Advance holders** page. To see transactions for all advance holders or to create a specific inquiry based on advance holders’ transactions, click **Accounts payable** &gt; **Inquiries and reports** &gt; **Advance holders inquiries and reports** &gt; Transactions. Click **Voucher** to open the **Voucher transactions** page.
### Advance holder balance inquiry

To see balance for an Advance holder use the **Advance holders** page. To see balance for all advance holders or to create a specific inquiry based on advance holders’ accounts, click **Accounts payable** &gt; **Inquiries and reports** &gt; **Advance holders inquiries and reports** &gt; **Balance.**
### Advance holder balance report

To preview and print a report based on information about advance holders’ balance, click **Accounts payable** &gt; **Inquiries and reports** &gt; **Advance holders inquiries and reports** &gt; **Advance holder balance report**.
### Advance holder transactions report

To preview and print a report based on advance holders’ transactions, click **Accounts payable** &gt; **Inquiries and reports** &gt; **Advance holders inquiries and reports** &gt; **Advance holder transactions report**.



See also
--------

[Advance holder transactions](emea-advance-holders-transactions.md)

