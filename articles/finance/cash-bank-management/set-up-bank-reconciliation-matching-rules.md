---
# required metadata

title: Set up bank reconciliation matching rules
description: This article explains how to set up reconciliation matching rules and reconciliation matching rule sets to help with the bank reconciliation process. Reconciliation matching rules are a set of criteria that are used to filter bank statement lines and bank document lines during the reconciliation process.
author: angelad116
ms.date: 11/22/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankReconciliationMatchRule, BankReconciliationMatchRuleSet
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 12971
ms.assetid: b5073f83-31dc-404f-af42-3fd84a02a7c6
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up bank reconciliation matching rules

[!include [banner](../includes/banner.md)]

This article explains how to set up reconciliation matching rules and reconciliation matching rule sets to help with the bank reconciliation process. Reconciliation matching rules are a set of criteria that are used to filter bank statement lines and bank document lines during the reconciliation process.

You can set up reconciliation matching rules and reconciliation matching rule sets to help with the bank reconciliation process. A reconciliation matching rule is a set of criteria that are used to filter bank statement lines and Dynamics 365 Finance bank transaction lines during the reconciliation process. Use the **Reconciliation matching rules** page to set up the reconciliation matching rules. You can set up more than one matching rule and then create a reconciliation matching rule set on the **Reconciliation matching rule sets** page. 

> [!NOTE] 
> Bank reconciliation matching rules are used if you reconcile an electronic bank statement by using advance bank reconciliation. 

On the **Reconciliation matching rules** page, you can select which actions and selection criteria are used when the matching rule is run. In the **Actions** field group, select the action that will be performed when the matching rule is run during the reconciliation process.  

By default, matching rules will match to the first bank document that meets the matching rule criteria. If multiple bank document meet the rule criteria, the parameter to require manual matching can be turned on by going to **Cash and bank management > Setup > Cash and bank management parameters > Bank reconciliation > Require manual matching when advanced bank reconciliation matching rules find multiple documents that match on amount**.

You can turn on this feature "Advanced bank reconciliation improvement: enable group conditions in reconciliation matching rules" to enable three additional matching type: One to many, Many to one, Many to many. Grouping conditions will be available in the reconciliation matching rules setup when you choose either of three matching types. Bank statement records and bank transaction records will be grouped by the grouping conditions define in this step and then execute rest of the matching steps.

> [!NOTE] 
> The option that you select determines the fields that appear.

| Action | Description   | Selection criteria available when action is selected     |
|--------|---------------|----------------------------------------------------------|
| **Match with bank document**       | Create criteria to specify how the bank documents and bank statement lines are matched when the matching rule is run from the **Bank reconciliation worksheet** page. The transaction lines are selected according to the additional criteria that are set up on the FastTabs. | <ul><li>**Step 1: Define the matching rule** – Select criteria to specify which bank statements should be matched with Finance bank transactions.</li><li> **Step 2 (optional) : Select the statement lines to run matching rules against:**  Apply a filter on which statement line to run the rules against.</li></ul>                                       |
| **Clear reversal statement lines** | Create criteria to specify how reversal statement lines should be removed from the **Bank reconciliation worksheet** page when the matching rule is run. This option is used when a bank error causes two bank statement lines to be listed in the imported bank statement, and the lines must be reconciled. |<ul><li> **Step 1**: **Find reversal statement lines** – Add selection criteria to select reversal bank statement lines. For example, to select only checks, select the **Bank transaction code** in the **Field** field, select the plus sign (+) in the **Operator** field, and then enter **Checks** in the **Value** field. </li><li>**Step 2: Find original statement lines** – You can add selection criteria to match bank document lines to bank statement lines. </li><li>**Step 3: Find Finance bank transactions** – You can add selection criteria to match Finance bank transactions to bank statement lines.</li></ul>  |
| **Mark new transactions**          | Create criteria to specify how new transactions should be marked on the **Bank reconciliation worksheet** page when the matching rule is run.                                                                                                                                                                 | <ul><li>**Step 1: Find statement lines** – Add selection fields to specify which bank statement lines should be selected from the **Bank reconciliation worksheet** page.</li><li> **Step 2: Find finance and operations** – You can add selection criteria to search bank document lines. If no bank document is found, a statement line will be marked as a new transaction. </li></ul>         |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

