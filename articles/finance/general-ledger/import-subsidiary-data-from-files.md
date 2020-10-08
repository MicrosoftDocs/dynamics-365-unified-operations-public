---
title: Import subsidiary data from files
TOCTitle: Import subsidiary data from files
ms:assetid: 20fa98c9-4c38-4352-b25b-3afde679d7bb
ms:mtpsurl: https://technet.microsoft.com/library/Aa496786(v=AX.60)
ms:contentKeyID: 37822140
author: jinniew
ms.date: 04/18/2014
mtps_version: v=AX.60
audience: Application User
ms.search.region: Global
---

# Import subsidiary data from files
The Consolidate with Import form allows you to prepare the transfer of subsidiary data from external systems.

1.	Start by preparing a new legal entity in the consolidatin process and Set up a subsidiary legal entity for consolidation. For more information see [Prepare a legal entity for use in the consolidation process](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/prepare-a-legal-entity-for-use-in-the-consolidation-process) and [Set up a subsidiary legal entity for consolidation](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-a-subsidiary-legal-entity-for-consolidation)

2. Preparing your import file. 
		a. Run steps to Export Subsidiary data to file as outlined above. You could use this step to consolidate from another D365 instance or from Business Central.
		b. For data from external systems, data will need to be formatted to this format

3. Click Consolidations > Consolidate with Import

    a. On the Criteria tab, specify the details of the data import.
		
    	§ Note: If the same criteria apply to several subsidiaries, you can transfer data from those subsidiaries to the consolidated legal entity by using a single operation.
		  § Description: Create a description to identify this Import.
			§ Main Account: Identify FROM and TO accounts. If left blank it will include ALL accounts.
			§ Consolidation Period: Enter FROM and TO Dates to consolidate.
			§ Include actual amounts: Toggle to Yes to include Actuals
			§ Include budget amounts: Toggle to Yes to include budget amounts in consolidations
			§ Rebuild balances during consolidations: Toggle to yes (Note: rebuild will completely clear the balance and new records and recreate the balance from the beginning of time)
			§ Budget Models: Identify Budget Models to consolidate (if you toggled to include budget amounts).
			§ Budget Rate type: Identify Budget exchange rate type
			
		b. On the Legal entities tab, create a line for each subsidiary legal entity whose data will be imported into the consolidated legal entity. Specify the following information for each subsidiary:
		
			§ Source Legal Entity: Select the legal entity you are importing
			§ Share: If the consolidated legal entity owns part of a subsidiary, specify the share of the subsidiary accounts that is imported.
			§ Account type of conversion differences: specify whether exchange differences that are the result of the consolidation process are posted to a balance account or a profit and loss account in the consolidated legal entity.
			§ File Name : Select Import file
			§ OK
			
		c. On the Currency Translation tab-  If you have different accounting currencies, this is where you set up the translation that is going to happen during the consolidation process. 
		
			§ Source Legal entity:  Select entity you are consolidating
			§ Source accounting currency: This will default from source legal entity you select.
			§ From Account: Select Beginning range. (Note: These are the accounts from the source company)
			§ To Account: Select ending range
			§ Exchange rate type: Select Rate type (this is defined in Currency exchange rates. See [(POL) Set up ledger accounts for posting currency exchange differences](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/pol-set-up-ledger-accounts-for-posting-currency-exchange-differences))
			§ Apply exchange rate from: Select the date you want the rate to apply from. You could also select a user defined rate here.
			§ Exchange rate: This will default based on the exchange rate type you selected. Or you will have the option to define a rate if you selected a user defined rate.
			
		d. Run in background
			§ Batch Processing: Toggle Yes or No to set up the consolidation to run as a batch job at a specific time, or click OK to run the consolidation immediately.
			
	4. The transactions and balances that were specified for consolidation in the subsidiaries are added to the appropriate accounts in the consolidated legal entity.



