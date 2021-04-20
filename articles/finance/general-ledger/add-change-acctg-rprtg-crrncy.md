---
# required metadata

title: Year-end activities FAQ 
description: This topic has been compiled to assist with year-end closing activities.
author: kweekley
ms.date: 01/25/2021
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
ms.dyn365.ops.version: 10.0.14

---

How do I change the accounting or reporting currency or add a reporting currency to the Ledger setup? The following scenarios typically trigger this question: 
•	A legal entity was set up with the wrong accounting or reporting currency and you want to change the currency.
•	A legal entity was set up without a reporting currency (optional to define) and you want to add the reporting currency.
o	Some organizations request this to start using the Dual currency functionality.
•	A legal entity was set up with a reporting currency and you want to remove the reporting currency.
•	An organization is upgrading/migrating to Dynamics 365 Finance and want to change the accounting or reporting currency.
Answer
The most important detail to consider when answering this question is whether any transactions (actual or budget) have been posted into the legal entity for the Ledger setup. **It is not possible to change the accounting or reporting currency or add a reporting currency if a single transaction (actual or budget) has been posted within the legal entity.**  The following steps can be taken regardless of whether or not transactions have been posted. 
No transactions posted
•	In the legal entity that you’re updating currencies for, navigate to **General Ledger > Ledger Setup > Ledger**.
•	On the **Ledger** page, click the **Edit** button in the upper left corner of the page.
•	Beneath the **Currency** FastTab, select the accounting and reporting currencies to use for this legal entity
•	Click **Save**.
If the accounting and reporting currency fields are not enabled on your **Ledger** page, one or more transactions (actual or budget) have been posted into the legal entity and the currencies can’t be changed. If that is the case, complete the following steps.
Transactions posted
**The only option to modify or add the accounting and reporting currencies is to create a new legal entity with the correct currencies.  To make the creation of the legal entity easier, use Data management within Dynamics 365 Finance to copy setup and master records from the current legal entity to the new legal entity.** 
Changing the accounting or reporting currency is a pervasive change. This change doesn’t impact General ledger only, but also every subledger (AR, AP, Inventory, Project, etc), ISV solution, and extension made by a customer that stores amounts.   To find and translate each of these amounts to a different currency is subject to error.  Because of this, the engineering team won’t approve a script to modify or add the accounting and reporting currencies.  Also, a tool used to be available on Microsoft Dynamics AX 2012 to modify or add the accounting and reporting currency.  The tool was deprecated for both Microsoft Dynamics AX 2012 R3 and Dynamics 365 Finance. 
Below is a step-by-step outline for the process of copying the setup and master data from the current legal entity to the new legal entity.
•	Navigate to Workspaces > Data management within Dynamic 365 Finance.
•	Choose the "Templates" option in the Import/Export action pane.
•	In the window, make sure there are templates available. If no templates are available, select the **Load default templates** menu selection and wait for the templates to be generated.
•	Return to the Data management workspace.
•	Click the **Copy into legal entity** action.
•	Enter a group name and description.
•	In the **Source legal entity** field, select the company from which you wish to copy data from.
•	In Destination legal entities, use the **Create legal entities** option to create a new company in which you want to copy the source company data into. If you wish to copy data into an existing legal entity, click the **Select existing** option to do so.
•	Set **Copy number sequences** to true (this is a good idea when performing the copy).
•	In the bottom window, choose **Add template** option. 
•	Select templates you wish to use. Suggested templates for a new company include "025 - General Ledger", and "Financials". It’s important to research these templates to see if there are additional ones that may apply, as well.
•	Choose the **Copy into legal entity** menu selection to start a batch process that will create and copy the selected entities into the destination company.
•	Once the copy is complete, and before a single transaction is posted, go to the ledger and update the accounting and reporting currencies.
If a new legal entity was created to change the accounting or reporting currencies, verify that the beginning balances are translated from the previous legal entities’ currencies to the new accounting or reporting currencies.
For a video describing the steps above, click the following link:
https://community.dynamics.com/365/b/techtalks/posts/copy-into-legal-entity-october-24-2017

