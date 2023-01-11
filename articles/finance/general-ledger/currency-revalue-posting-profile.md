---
# required metadata

title: Currency revaluation posting profiles
description: This article describes the Currency revaluation posting profiles.
author: moaamer
ms.date: 01/10/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerClosingSheet
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 14091
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2022-11-28
ms.dyn365.ops.version: AX 10.0.0

---

# Currency revaluation posting profiles

The currency revaluation posting profile allows you to post currency revaluation adjustment to different accounts per module (General ledger, Accounts payable, Accounts 
receivable and Bank). It provides the ability to post to the lower granular level on each module where you can define a currency revaluation posting 
account per currency code and the lowest level of ledger account, vendor, customer or bank. The differentiation could be for unrealized gain or loss for all modules. Realized gain or loss is available only for accounts payable and accounts receivable.  

## Create a currency posting profile

To create a new currency posting profile:
1. Go to **General ledger > Currencies > Currency revaluation posting profile**. 
2. In the **Currency code** field, select **All** currencies or define specific currency by selecting **Table** in the **Currency code** field. 
3. In the **Account code** field, you can select **All**, **Group** or **Table** to identify an account or main account depending on the module page selected. The **Main account** is a mandatory field where you select the currency revaluation posting account that will be used during the currency revaluation adjustment. 


As an example, the Unrealized gain for General ledger post the currency revaluation of EUR transactions on main account 600120 to adjustment account 801602. To post 
currency revaluation of all currencies on accounts that belongs to Travel and Expense (TANDEEXP) main category to adjustment account 801601. To post currency 
revaluation of all currencies on all accounts to adjustment account 801600.


[![Currency revaluation posting profile.](./media/Postingprofile1.png)](./media/Postingprofile1.png)


**Table** – The posting profile applies to a specified ledger account. 
**Group** – The posting profile applies to the selected main account category. 
**All** – The posting profile applies to all main accounts that have the **Foreign currency revaluation** option set to **Yes**. 

### Accounts payable
As an example, the Unrealized gain for Accounts payable post the currency revaluation of EUR transactions on main account 1001 to adjustment account 801602. To post currency revaluation of all currencies on vendors that belongs to Parts vendors (10) vendor group to adjustment account 801601. To post currency revaluation of all currencies on all vendors to adjustment account 801600.

**Table** – The posting profile applies to a single vendor. 
**Group** – The posting profile applies to a vendor group. 
**All** – The posting profile applies to all vendors. 


### Accounts receivable
As an example, the Unrealized gain for Accounts receivable post the currency revaluation of EUR transactions on customer account US-001 to adjustment account 801602. To post currency revaluation of all currencies on accounts that belongs to Wholesales customers (10) customer group to adjustment account 801601. To post currency revaluation of all currencies on all customers to adjustment account 801600.

**Table** – The posting profile applies to a single customer. 
**Group** – The posting profile applies to a customer group. 
**All** – The posting profile applies to all customers. 


## Bank         
As an example, the Unrealized gain for Bank post the currency revaluation of EUR transactions on bank account USMF EUR to adjustment account 801602. To post currency revaluation of all currencies on accounts that belongs to BankEUR bank group to adjustment account 801601. To post currency revaluation of all currencies on all bank accounts to adjustment account 801600.


**Table** – The posting profile applies to a single Bank ID. 
**Group** – The posting profile applies to a bank group. 
**All** – The posting profile applies to all banks. 

The **Lowest level of defaulting** option determines the lowest level of the posting in the case of overlapped setting. 


For example, on the **Currency revaluation posting profile** for an unrealized gain under general ledger that have potential overlapped setting. 
 - Post currency revaluation adjustment of EUR currency for all accounts to account 801605. 
 - Post currency revaluation adjustment of all currencies for account 601400 to account 801603. 

Based on the **Lowest level of defaulting** option will determine which account to take priority: 
-	**Currency**: Priority is given to the currency and will post currency revaluation to 801605 account. 
-	**Account**: Priority is given to the account and will post currency revaluation to 801603 account.

[![Posting example.](./media/Lowestlevel2.png)](./media/Lowestlevel2.png)


>[!Note] 
>If the **Currency revaluation posting profile** is not configured, the accounts that are selected on the **Ledger** page, **Accounts for currency revaluation** FastTab will be used. 















