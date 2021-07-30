---
# required metadata

title: Default financial dimensions on financial journals 
description: This topic explains why opening balances might be missing when you close a year, and how to rebuild those balances if they are missing.
author: kweekley
ms.date: 08/04/2021
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2020-12-14
ms.dyn365.ops.version: 10.0.17

---

# Default financial dimensions on financial journals

[!include [banner](../includes/banner.md)]

The following rules define how financial dimension values default on transactions that are entered through financial journals (but not inventory or project journals). This also includes details in the event that you’re using fixed dimensions.

## Symptom
A voucher is entered into a journal, such as the general journal. The account is a Vendor account and the Offset account is a Bank account.  The vendor’s default financial dimensions will be entered by default on the account but the bank’s default financial dimensions don’t default.  Instead, the offset account defaults the dimension values from the Account.   
OR

A fixed dimension is assigned to a main account. The fixed dimension doesn’t default on the Account or Offset account but is assigned during the posting. I’m expecting the fixed dimension to be entered by default either before or after posting so that the posted accounting entry matches the line on the voucher.
## Resolution
The following rules are followed for defaulting financial dimension values onto the lines of a voucher within the financial journals, such as the general journal or vendor invoice journal. 

### Journal header

1. Journal header dimensions default from Journal name default dimensions.
Journal line Account
2. First, journal line Account dimensions default from Journal header default dimensions.
3. If any financial dimensions are blank, their values will default from Customer, Vendor, Bank, Fixed assets, Project, or Ledger default dimensions.

   - If the Account type is Ledger, a fixed dimension on a Ledger account is treated like a default dimension during transaction entry.
   - If the Account type is Customer, Vendor, Bank, Fixed assets, or Project, the main account isn't known yet so a fixed dimension will never default for the Account.

### Journal line Offset Account

4. First, journal line Offset Account dimensions default from journal line Account dimensions.
5. If any financial dimensions are blank, they will next default from the Journal header.
6. If any financial dimensions are blank, they will next default from the **Ledger default dimensions** page. You can access this page from the main page for customers, vendors banks and fixed assets as follows: 
 
   **Customer > Ledger default dimensions**
   **Vendor > Ledger default dimensions**
   **Fixed Assets > Ledger default dimensions**
   **Project > Ledger default dimensions**

  - If the Offset account type is Ledger, a fixed dimension on a Ledger account is treated like a default dimension during transaction entry. If a dimension values already defaulted from the Account, the main account’s default or fixed dimension value will not override the default. 
  - If the Offset account type = Customer/Vendor/Bank/Fixed Assets/Project, the main account isn't known yet so a fixed dimension will never default for the Account.
Posting

7. During posting, the main account for each line of the accounting entry (for both the Account and Offset account) is evaluated for whether there is a fixed dimension value. If a fixed dimension is defined, any existing or blank values will be replaced with that fixed dimension value. 

   - The fixed dimension value is NOT displayed on the journal lines after posting. Instead, it’s shown on the accounting entry when viewing the voucher after posting.

8.	No other dimension values default during posting. This includes additional ledger accounts that may be added during posting such as penny rounding, intercompany due to/due from, and so on. The default dimension entries for additional ledger accounts are taken from the Account and Offset accounts. 
For the purpose of making default entries, the journal default logic doesn’t know if a blank dimension value was left blank intentionally, or if it just didn’t default.  If a dimension value is intentionally left blank, a value may still default using the defaulting order described above. If you need a dimension with a blank value, you might need to create a dimension with a value of zero to use in place of a blank dimension. 

Please review the following scenarios for examples of the financial dimension defaulting order. 

#### Scenario 1

Navigate to General ledger > Journal setup > Journal names.  In the journal name, select journal GenJrn and define the following values for the Default financial dimensions:
BUSINESSUNIT: 001
DEPARTMENT: 024

[![General ledger parameters page.](./media/financial-dimension-defaulting-jrnl-names-01.png)](./media/financial-dimension-defaulting-jrnl-names-01.png)

Go to the **General ledger > Journal entries > General journal**. Create a new general journal using journal name GenJrn. The dimensions default from the Journal name (LedgerJournalName table) to the journal header (LedgerJournalTable table) which is shown on the **Financial dimensions** tab. 

[![Financial dimensions tab on the General ledger parameters page.](./media/financial-dimension-defaulting-genrl-jrnl-02.png)](./media/financial-dimension-defaulting-genrl-jrnl-02.png)

Go to the Lines. Using the **Account type** Ledger, enter 170150 in the Account field and tab out of the field. The dimensions default from the Journal header, resulting in the account value 170150-001-024.

[![Journal lines on a general journal.](./mediafinancial-dimension-defaulting-jrnl-vchr-03.png)](./media/financial-dimension-defaulting-jrnl-vchr-03.png)

Change the Account value to 170150-001-023. Enter either a debit or credit amount, define the Offset account type as Ledger, then enter 600150 in the Offset account field. The dimension values default from the account, resulting in the offset account 600150-001-023.

#### Scenario 2

Use the same Financial dimensions on the Journal name as defined in Scenario 1.  Next navigate to the **All customers** page (**Accounts receivable > Customers > All customers**) to define default financial dimension values for customer US-001. Select the customer to open the customer details and go to the **Financial dimensions** tab. Keep the default value for BUSINESSUNIT as 001 and add the COSTCENTER as 007. 

Create a new General journal using journal name GenJrn. On the Financial dimensions tab, change the default BUSINESSUNIT from 001 to 002.

Go to the Lines. Using the Account type Customer, enter the Account as US-001.  To view the financial dimensions for non-Ledger account types, open Financial dimensions > Account. The default entries for financial dimension values are entered as follows:

   BUSINESSUNIT: 002 – Defaulted from the journal header. BUSINESSUNIT 001 is not defaulted from Customer US-001 because a value already defaulted.
   COSTCENTER: 007 – Defaulted from the Customer US-001 setup
   DEPARTMENT: 024 – Defaulted from the Journal header
   Back on the line, enter the Offset account type as Ledger with Offset account 600150. The financial dimension values are shown on the line and defaulted as follows:
   BUSINESSUNIT: 002 – Defaulted from Account’s financial dimensions (which originally defaulted from the journal header)
   DEPARTMENT: 024 – Defaulted from Account’s financial dimensions (which originally defaulted from the journal header)
   COSTCENTER: 007 – Defaulted from Account’s financial dimensions (which originally defaulted from the customer)

#### Scenario 3

While in the same journal as scenario 2, add a new line. Define the Account type as Ledger and enter Account 170150--.  Do this by clearing the default dimension values in the Account field. Set the Offset account type to Customer and enter the Offset account US-001.

   BUSINESSUNIT: 002 – The default entry is from the journal header because the Account dimension value is blank. BUSINESSUNIT 001 isn’t used as the default entry from Customer US-001 because a default value was already taken from the Journal header. If the BUSINESSUNIT was left blank intentionally, you must also remove the financial dimension on the Offset account. 
   COSTCENTER: 007 – The default entry is taken from the Customer US-001 because the Account and Journal header dimension value is blank. If the COSTCENTER was left blank intentionally, you must also remove the financial dimension on the Offset account.
   DEPARTMENT: 024 – The default entry is taken from the journal header because the Account dimension value is blank. If the DEPARTMENT was left blank intentionally, you must also remove the financial dimension on the Offset account.

#### Scenario 4

Use the same default financial dimension values on the Journal name and Customer as defined in Scenarios 1 and 2. Next, define a fixed dimension value for the BUSINESSUNIT on the main account 170150 by navigating to the **Main accounts** page (**General ledger > Chart of accounts > Accounts > Main accounts**). Select main account 170150, and click **Add** on the Legal entity overrides tab. Select USMF and click the **Add** button. Next highlight that record and click the **Default dimensions** button. Change the BUSINESSUNIT to a **Fixed value** and enter 003. 

Create a new General journal using journal name GenJrn. On the Financial dimensions tab, remove all the default dimension values. Go to the lines. Using the Account type Ledger, enter 170150 in the Account field and tab out of the field. The dimension values default from the Main account setup for account 170150, resulting in the account 170150-003- .

Change the account value to 170150-004-. The journal functionality does not prevent a fixed dimension value from being changed.  Enter either a Debit or Credit amount and set the Offset account type to Ledger.  Enter an Offset account of 170250 and post the document.
Click the **Voucher** button within the journal and you will see the BUSINESSUNIT value is reverted back to 003, the fixed dimension value, during posting. 

When you return to the voucher on the journal, the BUSINESSUNIT does NOT reflect the fixed dimension value. It always remains with the value shown in the UI before posting.  The posting process doesn’t change anything entered on the voucher; it only changes the accounting entry during posting. 

## Developer notes

If you are a developer and want to look at code for the defaulting process, review the following methods:
- LedgerJournalEngine.accountModified() – this method is the main entry point for the primary account dimension defaulting standard to all journals (and overridden by some journal types).
- LedgerJournalEngine.offsetAccountModified() – Offset account dimension defaulting
