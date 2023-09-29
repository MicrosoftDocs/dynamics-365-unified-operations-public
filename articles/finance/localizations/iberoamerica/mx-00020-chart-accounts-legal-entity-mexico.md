---
title: MX-00020 Set up the chart of accounts for a legal entity in Mexico
description: Set up specific parameters in the chart of accounts to allow the generation of electronic ledger accounting reports for a Mexican legal entity.
author: AdamTrukawka
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Mexico
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: MainAccount, LedgerConsolidateAccountGroup, MainAccountConsolidateAccount
---
# MX-00020 Set up the chart of accounts for a legal entity in Mexico

[!include [banner](../../includes/banner.md)]

Set up specific parameters in the chart of accounts to allow the generation of electronic ledger accounting reports for a Mexican legal entity. This task was created using the MXMF demo data company.


## Set up parameters for electronic ledger accounting report
1. Go to General ledger > Chart of accounts > Accounts > Main accounts.
2. Click New.
3. In the Main account field, type a value.
4. In the Name field, type a value.
5. In the DB/CR default field, select an option.
    * Use this field to specify the typical transaction (debit/credit). This field is used in the XML file to report the government type of main account in the node `<Natur>`.  Main account type will be used to determine the government type of account when this field is blank.  
6. In the Parent account field, click the drop-down button to open the lookup.
    * Example: 110  Use this file to set up the parent main account of the previous level.     Leave this field blank when the main account represents the first level of company in the chart of accounts.    
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. Click Save.

## Set up government group mapping
1. Go to General ledger > Chart of accounts > Accounts > Consolidation account groups.
2. Click New.
3. In the Consolidation account group field, type a value.
4. In the Name field, type a value.
5. Click Save.
6. Close the page.
7. Go to General ledger > Chart of accounts > Accounts > Additional consolidation accounts.
8. Click New.
9. In the Main account field, click the drop-down button to open the lookup.
10. In the list, find and select the desired record.
11. In the list, click the link in the selected row.
12. In the Consolidation account group field, click the drop-down button to open the lookup.
13. In the list, find and select the desired record.
14. In the list, click the link in the selected row.
15. In the Consolidation account field, type a value.
    * Enter the SAT account group. The list of government account groups is available on the government website.    
16. In the Consolidation account name field, type a value.
    * You can enter the name of the SAT account group.    
17. In the SAT level field, enter a number.
    * This is the level of SAT account group. The information is available in the list of SAT account groups.  
18. Click Save.
    * You need to repeat this action for each main account created in your company. If you have a lot of main accounts to create, you can use the Data management tool to import the main accounts from a Microsoft Excel file.  
19. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
