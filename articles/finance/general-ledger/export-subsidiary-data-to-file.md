---
title: Export subsidiary data to a file
TOCTitle: Export subsidiary data to a file
ms:assetid: 20fa98c9-4c38-4352-b25b-3afde679d7bb
ms:mtpsurl: https://technet.microsoft.com/library/Aa496786(v=AX.60)
ms:contentKeyID: 37822140
author: jinniew
ms.date: 04/18/2014
mtps_version: v=AX.60
audience: Application User
ms.search.region: Global
---

# Export subsidiary data to a file
The **Consolidate [Export to]** page is used to prepare the export of subsidiary data to files that can be imported into the consolidated legal entity.

1.	Start by preparing a new legal entity in the consolidatin process and Set up a subsidiary legal entity for consolidation. For more information see [Prepare a legal entity for use in the consolidation process](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/prepare-a-legal-entity-for-use-in-the-consolidation-process) and [Set up a subsidiary legal entity for consolidation](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-a-subsidiary-legal-entity-for-consolidation)

2. Click Consolidations > Export company balances
   a. On the Criteria tab, specify the details of the consolidation.
          
      • Main Account - specify Accounts you want to consolidate. Leave blank if you want to include all accounts
      • Use consolidation account - If you have specified consolidation accounts, move this toggle to Yes
      • Select consolidation account from - Select either Main Account or Consolidation account Group
      • Consolidation account group: Select a consolidation account group as indicated in prior step.
      • Consolidation Period: Specify Consolidation To and From Date.
      • Include actual amounts: Toggle to Yes to include Actuals
      • Include budget amounts: Toggle to Yes to include budget amounts in consolidations
      • Budget Models: Specify which Budget Model to choose from.

    b.	On the Financial Dimensions tab, specify the details of the consolidation

          •	Specify the financial dimension information that is transferred from the transactions in the subsidiary accounts to the transactions in the consolidated legal    entity.
          •	Select from the list of Financial dimension
          •	Identify the correct Specification for each Financial Dimension to be consolidated (Select from Dimension, Group Dimension*, Company Accounts and Account)
          •	Specify a Segment Order that you want to consolidate in.
          •	*Note: Group Dimension - Allows you to define the dimension value used by the "group" of companies.

     c.	On the Legal Entities tab, specify which legal entity you will be exporting
          •	Click +New
          •	Source Legal Entity: Enter Legal Entity (Note: If the same criteria apply to several subsidiaries that are in the same database, you can transfer data from those subsidiaries to separate export files by using a single operation.)
              1.	create a line for each subsidiary legal entity whose accounts will be exported to files. These files will be imported into the consolidated legal entity later.
              2.	For each subsidiary, enter the subsidiary name and the name of the export file that will be created during the export job.
          •	Account type of conversion differences: Select from Profit and Loss or Balance Sheet
          •	File Name: Enter a file name to create the export file
          
          
3.	OK
4.	When the export is completed, a message displays the number of records that were saved in each file. You can then import the files into the consolidated legal entity.



