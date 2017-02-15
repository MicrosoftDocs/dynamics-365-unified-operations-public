---
# required metadata

title: General journal processing
description: This articles describes capabilities in Microsoft Dynamics AX that can help make general journal processing easier, and that can also help guarantee that correct data is captured and internal control isn't compromised.  
author: twheeloc
manager: AnnBe
ms.date: 2015-12-03 20 - 42 - 19
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalSetup, LedgerJournalTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: fd00aa13-12fc-4caa-a29d-10b0a68189d8
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# General journal processing

This articles describes capabilities in Microsoft Dynamics AX that can help make general journal processing easier, and that can also help guarantee that correct data is captured and internal control isn't compromised.  

Journal names
-------------

One of the most important areas to set up is journal names. It's a good idea to define specific journal names for each purpose, such as intercompany, accrual adjustment, and error correction. You can tailor each journal name to help make data entry for each purpose easy and secure. On the **Journal names** page, you can set up the following elements:

-   **Workflow approval** – To increase internal control, define journal workflows that establish materiality limits for review and approval steps, based on criteria such as total debit amount. You set up workflows for the general journals on the** General ledger workflows** page.
-   **Default values** – Select default values for offset accounts, currency, and financial dimensions.
-   **Journal control** – You can set up restrictions on the company and account type, and also the segment values. **Examples**
    -   A journal name can be used only for adjustments. In this case, you can specify that only the **Ledger** account type is valid across all companies. [![Journal control account types](./media/journal-control-account-types1.png)](./media/journal-control-account-types1.png)
    -   A journal name can be used only for a specific segment or for a range for main accounts. [![Journal control segment](./media/journal-control-segment1.png)](./media/journal-control-segment1.png)

The **Automatic reversal** option is available in general journals. For example, you have an accrual adjustment where the actual document hasn't yet been processed, as shown in the following illustration. [![General journal reversing](./media/general-journal-reversing1.png)](./media/general-journal-reversing1.png) The Microsoft Excel add-in for journal entry provides an additional level of automation and makes data entry easier. The **Open lines in Excel** action is available on the **General journal** and **Journal voucher** pages. On the **Periodic journals** page, you can set up recurring journals to automate journal processing. You can use voucher templates at any time. On the **General journals** page, the **Save** and **Select voucher template** actions are found on the **Journal voucher** page, under **Functions** for the voucher lines.

## Related setup
The following setup isn't specific to general journals, but will help guarantee that data entry is correct data and easy.

### Main account

The main account setup provides many options for general journal processing:

-   **DC/CR requirement** – Use this option if a main account is limited to debit or credit transactions. The setup is verified when a journal is validated or posted.
-   **Default offset account**
-   **Suspended** – Suspend a main account for data entry across all companies or for a specific company/legal entities.
-   **Do not allow manual entry** – Prevent users from manually entering a value for the account in journals.
-   **Default/Validate currency**
-   **Legal entity override** – This setup is specific to the defined company/legal entity:
    -   **Default/Validate sales tax**
    -   **Default dimension** – **Not fixed** or **Fixed value**. **Fixed value** will help guarantee that all postings for this main account always use any dimension value that is set up as **Fixed**.
-   **Posting validation**
    -   **User validation** – This option controls which users are allowed to post to a main account.
    -   **Posting type validation** – This option controls which posting types are allowed for a main account.

### Accounting structures and advanced rules structures

Accounting structures and advanced rules structures are extremely important for guaranteeing that the data that is required for financial reporting and performance tracking is captured during general journal processing and any documentation. Accounting structures and advanced rules structures let you tailor the data entry experience. You can allow data entry only for financial dimensions that are relevant in each situation, and can also enforce the requirement that mandatory and correct data always be captured.

See also
--------

[Planning: Chart of accounts](plan-chart-of-accounts.md)

