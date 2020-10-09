---
# required metadata

title: Import subsidiary data from files
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

# Import subsidiary data from files

[!include banner] 

This topic lists the steps for preparing data from external systems to be imported to Dynamics 365 Finance. The **Consolidate with Import** page is used to prepare for the transfer of subsidiary data from external systems.

1. Start by preparing a new legal entity in the consolidatin process and Set up a subsidiary legal entity for consolidation. For information about creating legal entities, see [Create a legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md).

*For more information see [Prepare a legal entity for use in the consolidation process](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/prepare-a-legal-entity-for-use-in-the-consolidation-process) and [Set up a subsidiary legal entity for consolidation](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-a-subsidiary-legal-entity-for-consolidation).* 

2. Prepare your import file. For more information, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md).

3. Perform the steps to **Export Subsidiary data to file** as outlined above. You can use this step to consolidate data from another instance of Dynnamics 365 Finance, or from Business Central.
		b. For data from external systems, data will need to be formatted to this format

4. Open the **Consolidate with import** page (**Consolidations > Consolidate with Import)**. On the **Criteria** tab, specify the details of the report, and/or the import, as follows. 

|      Field                                   	|      Entries for    reporting                                                                                                                      	|      Entries for    inporting                                                                                                                      	|
|----------------------------------------------	|----------------------------------------------------------------------------------------------------------------------------------------------------	|----------------------------------------------------------------------------------------------------------------------------------------------------	|
|     Description                              	|                                                                                                                                                    	|     Create a description to identify this   import.                                                                                                	|
|     Main account                             	|     Identify FROM and TO accounts to define a   range. Not entering a range will cause all accounts to be included.                                	|     Identify FROM and TO accounts to define a   range. Not entering a range will cause all accounts to be included.                                	|
|     Consolidation period                     	|     Enter From and To* dates to define a range   to consolidate.                                                                                   	|     Enter From and To* dates to define a range   to consolidate.                                                                                   	|
|     Include actual amounts                   	|     Set to Yes to include actuals.                                                                                                                 	|     Set to Yes to include actuals.                                                                                                                 	|
|     Include budget amounts                   	|     Set to Yes to include budget amounts in   consolidations.                                                                                      	|     Set to Yes to include budget amounts in   consolidations.                                                                                      	|
|     Rebuild balances during consolidation    	|     Set to Yes. The rebuild process will   completely clear the balance and new records, and recreate the balance from   the beginning of time.    	|     Set to Yes. The rebuild process will   completely clear the balance and new records, and recreate the balance from   the beginning of time.    	|
|     Budget models                            	|                                                                                                                                                    	|     Enter the budget models to be consolidated   if you chose to import budget amounts.                                                            	|
|     Budget rate type                         	|                                                                                                                                                    	|     Enter a budget exchange rate type.                                                                                                             	|
5. On the Legal entities tab, create a line for each subsidiary legal entity whose data will be imported into the consolidated legal entity. Specify the following information for each subsidiary.

|     Field                                       	|     Entry                                     	|
|-------------------------------------------------------|-------------------------------------------------------|
|     Source legal   entity                       	|     Select the   legal entity you are importing.      |
|     Share                                       	|     If the   consolidated legal entity owns part of a subsidiary, specify the share of the   subsidiary accounts that is imported.                                                                	|
|     Account type   of conversion differences    	|     Specify   whether exchange differences that are the result of the consolidation process   are posted to a balance account or a profit and loss account in the   consolidated legal entity.    	|
|     File name                                   	|     Enter a name   for the import file.                                                                                                                                                           	|
			
6. If you have different accounting currencies, use the **Currency Translation** tab to configure the translation that will be performed during the consolidation. 

|     Field                           	|     Entry                                                   	|
|-------------------------------------	|---------------------------------------------------------------|
|     Source legal   entity           	|     Select the   legal entity you are importing.          	|
|     Source   accounting currency    	|     This default   currency is the currency associated with source legal entity you selected.                    	|
|     From and To   accounts          	|     Enter accounts   to define a range accounts to import from the source company.                                  	|
|     Exchange   rate type            	|     Select the rate   type. Rate types are defined in *Currency exchange rates*. See [POL Set up   ledger accounts for posting currency exchange differences](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/pol-set-up-ledger-accounts-for-posting-currency-exchange-differences).    	|
|     Apply   exchange rate from      	|     Enter a date   to apply the exchange rate that was set on that date or enter a value to use   as the exchange rate.                                                                                                                                                                                	|
|     Exchange   rate                 	|     The default entry   is based on the exchange rate type you selected. You can also define a rate   if you entered a user-defined exchange rate.                                                                                                                                                     	|

7. Set the **Run in background** field to **Yes** to let the import process run in the background.

8. Set the **Batch Processing** field to **Yes** to run the consolidation as a batch job at a specific time. To run the consolidate immediately, click **OK**. 
			
   The transactions and balances that were specified for consolidation in the subsidiaries are added to the appropriate accounts in the consolidated legal entity.



