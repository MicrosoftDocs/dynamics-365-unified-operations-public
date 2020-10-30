---
# required metadata

title: Export subsidiary data to a file
description: This topic lists the steps for preparing data from external systems to be imported to Dynamics 365 Finance.
author: jinniew
manager: AnnBe
ms.date: 10/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2018-5-31
ms.dyn365.ops.version: 8.0.1

---

# Export subsidiary data to a file

[!include banner] 

The **Consolidate [Export to]** page is used to prepare the export of subsidiary data to files that can be imported into the consolidated legal entity. For more information about the import and export processes, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md).

1. Create a new legal entity in the consolidatin process. For information about creating legal entities, see [Create a legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md).

For more information see [Prepare a legal entity for use in the consolidation process](prepare-company-for-consolidation.md) and [Set up a subsidiary legal entity for consolidation](set-up-subsidiary-company-for-consolidation.md). These are AX 2012 topics, which aren't maintained anymore. I tried to find alternate topics in Dynamics 365.

2. Open the **Export company balances** page (**Consolidations > Export company balances**). On the **Criteria** tab, specify the details of the consolidation as suggested in the following table.
          
|     Field                                  	|     Entry                                                                                          	|
|--------------------------------------------	|----------------------------------------------------------------------------------------------------	|
|     Main account                           	|     Specify the accounts to be consolidated. Leave this field  blank to include all accounts.    	|
|     Use consolidation account              	|     If you have specified consolidation accounts, move this toggle to Yes.                       	|
|     Select consolidation account from      	|     Select either Main Account or Consolidation account Group.                                   	|
|     Consolidation account group            	|     Select a consolidation account group for the consolidate account that you selected.          	|
|     Consolidation period                   	|     Specify Consolidation To and From Date.                                                      	|
|     Include actual amounts                 	|     Set to **Yes** to include actual amounts.                                                    	|
|     Include budget amounts                 	|     Set to Yes to include budget amounts in consolidations.                                      	|
|     Budget models                          	|     Specify which budget model to include.                                                       	|

 3. On the **Financial Dimensions** tab, specify the details of the consolidation as suggested follows. 

- Specify the financial dimension information that is transferred from the transactions in the subsidiary accounts to the transactions in the consolidated legal entity.
- Select from the list of Financial dimension.
- Identify the correct specification for each Financial Dimension to be consolidated. The selections include Dimension, Group Dimension, Company Accounts and Account).
- Specify a Segment Order that you want to consolidate in.

> [!Note]
> Group dimension - Allows you to define the dimension value used by the group of companies that's being consolidated.

4. On the Legal Entities tab, specify which legal entity you will be exporting.

- Click **New**.
- Enter Legal Entity in the **Source Legal Entity** field. (If the same criteria apply to several subsidiaries that are in the same database, you can transfer data from those subsidiaries to separate export files in a single operation.)
   1.	Create a line for each subsidiary legal entity whose accounts will be exported to files. These files will be imported into the consolidated legal entity later.
   2.	For each subsidiary, enter the subsidiary name and the name of the export file that will be created during the export job.
- Select Profit and Loss or Balance Sheet in **Account type of conversion differences** field.
- Enter a file name for the export file that will be created.

5. Click **OK** to run the export.

When the export is finished, a message will display the number of records that were saved in each file. You can then import the file into the consolidated legal entity.



