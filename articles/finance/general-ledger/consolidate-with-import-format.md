---
# required metadata

title: Consolidate with Import - Format
description: 
author: jinniew
manager: AnnBe
ms.date: 10/09/2020
ms.topic: article
ms.prod: This topic lists the import format that's used when you're consolidating financial data from multiple legal entities.
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

# Consolidate with Import - Format 

[!include banner] 

This topic lists the import format that's used when you're consolidating financial data from multiple legal entities. The information must be saved as a text (.txt) file. 

Below is the import format that you would use when using Consolidate with Import. You would save the file as a .txt file.

## Import Formats

|     Record table    	|     Formats                                                                    	|     Notes                                                                                                                                                                                                                                                                                                                                                                                                     	|
|---------------------	|--------------------------------------------------------------------------------	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
|     1               	|     170150,   Goodwill, 4                                                      	|     Record table   <br>     Source main   account ID <br>     Main account   name <br>     Main account   type <br>                                                                                                                                                                                                                                                                                           	|
|     2               	|     110130,   2015/01/01, 1, USD, 0,0,80699.39,0,1                             	|     Main account   ID <br>     Transaction   date <br>     Fiscal period   type (0 Opening, 1 Operating, 2 Closing     Transaction   currency <br>     Debit or   Credit (0 for Debit, 1 for Credit) <br>     Posting layer   <br>     Transaction   amounts, Quantity <br>     Local recid   (ambiguous unique int64 value for the transaction) <br>                                                         	|
|     3               	|     USMF0000009,   2017/01/01, FY2017, 1, 2017,01,01, 602200, USD, 6053.6.0    	|     Entry number   (budget header transaction number) <br>     Budget header   default date <br>     Budget model   ID <br>     Transaction   type (blank, original budget, etc.) enum integer value <br>     Line date   <br>     Line main account   ID <br>     Line currency   code <br>     Line   transaction currency amount <br>     Line budget   type (expense, revenue) enum integer value <br>    	|
|     4               	|     DEMF                                                                       	|     RecordCompany   is the source legal entity or the originating transactions                                                                                                                                                                                                                                                                                                                                	|
|     5               	|     110130,   2015/01/01, 1, USD, 0,0,80699.39,0,1                             	|     RecordCompany   is the source legal entity or the originating transactions                                                                                                                                                                                                                                                                                                                                	|
|     6               	|     BusinessUnit,   1     Department, 2                                        	|     The financial   dimension attributes defined in the segment order. <br>You can use the   **Export** page to verify how the attributes are defined. <br>                                                                                                                                                                                                                                                   	|
|     7               	|     002,1,658                                                                  	|     Financial   dimension value <br>     Financial dimension,   as the index provided in RecordDimensions <br>     Ambiguous   unique record ID that’s associated with the unique <br> record ID from   RecordTrans or RecordTrans2. <br>                                                                                                                                                                     	|
|     8               	|     002,1,1                                                                    	|     Dimension   values associated with the transaction from RecordBudget <br>     Financial   dimension as the index provided in RecordDimensions <br>     Ambiguous   line record ID, which lines up with the order of the transactions lines in   the file. <br>                                                                                                                                            	|

![Import Format](./media/import_format.jpg "Import Format")
  
