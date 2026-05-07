---
title: MX-00020 Set up the chart of accounts for a legal entity in Mexico
description: Learn how to set up specific parameters in the chart of accounts to allow the generation of electronic ledger accounting reports for a Mexican legal entity.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-06-30
ms.search.form: MainAccount, LedgerConsolidateAccountGroup, MainAccountConsolidateAccount
ms.dyn365.ops.version: Version 7.0.0
---

# MX-00020 Set up the chart of accounts for a legal entity in Mexico

[!include [banner](../../includes/banner.md)]

Set up specific parameters in the chart of accounts to generate electronic ledger accounting reports for a Mexican legal entity. This task uses the MXMF demo data company.

## Set up parameters for electronic ledger accounting report

1. Go to **General ledger** > **Chart of accounts** > **Accounts** > **Main accounts**.
1. Select **New**.
1. In the **Main account** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **DB/CR default** field, select an option.
    * Use this field to specify the typical transaction (debit or credit). The XML file uses this field to report the government type of main account in the node `<Natur>`. If this field is blank, the main account type determines the government type of account.  
1. In the **Parent account** field, select the dropdown button to open the lookup.
    * Example: 110  Use this value to set up the parent main account of the previous level.     Leave this field blank when the main account represents the first level of company in the chart of accounts.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Save**.

## Set up government group mapping

1. Go to **General ledger** > **Chart of accounts** > **Accounts** > **Consolidation account groups**.
1. Select **New**.
1. In the **Consolidation account group** field, enter a value.
1. In the **Name** field, enter a value.
1. Select **Save**.
1. Close the page.
1. Go to **General ledger** > **Chart of accounts** > **Accounts** > **Additional consolidation accounts**.
1. Select **New**.
1. In the **Main account** field, select the dropdown button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Consolidation account group** field, select the dropdown button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Consolidation account** field, enter a value.
    * Enter the SAT account group. The list of government account groups is available on the government website.
1. In the **Consolidation account name** field, enter a value.
    * Enter the name of the SAT account group.
1. In the **SAT level** field, enter a number.
    * This number represents the level of the SAT account group. You can find this information in the list of SAT account groups.  
1. Select **Save**.
    * Repeat this action for each main account you create in your company. If you need to create many main accounts, use the Data management tool to import the main accounts from a Microsoft Excel file.  
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
