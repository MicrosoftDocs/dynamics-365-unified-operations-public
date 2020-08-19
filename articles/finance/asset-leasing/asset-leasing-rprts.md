---
# required metadata

title: Asset leasing reports
description: This topic describes the Asset movement report, which serves as a rollforward report for the right-of-use asset balances for each lease.
author: moaamer
manager: Ann Beebe
ms.date: 08/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-18
ms.dyn365.ops.version: 10.0.14
---

# Asset leasing reports

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists and briefly describes the reports that are available in Asset leasing. You can display most reports by completing similar steps. For the reports that require a different selection path, the steps to generate the report are include with that report's description. 

- To view most Asset leasing reports, open the **Asset movements** report page (**Asset Leasing > Inquiries & reports** and then select a report to view). 
- A parameters page will open where you can set filters on the lease transactions. Enter filter criteria and click **OK**.
  The generated report will show information that falls within the filters that you specified.

## Asset movements 
The Asset movement report, which serves as a rollforward report for the right-of-use asset balances for each lease. This report lets you view the asset transactions of a lease during a specified period. The report includes the following fields. 

|     Name                           |     Description                                                                |
|------------------------------------|--------------------------------------------------------------------|
|     Commencement Date              |     The commencement date of the lease’s earliest version.   |   
|     Lease Term                     |     The lease term of the lease’s earliest version.                               |
|     Short Term Lease               |     If lease is classified as a short-term lease will show as   “Yes”               |
|     Low Value Lease                |     If lease is classified as a low-value lease will show as   “Yes”                   |
|     Initial Right of Use Asset     |     The original value of the right of use asset from the   initial recognition journal entry      |
|     Beginning Balance              |     The net book value of the right of use asset as of the   From Date                             |
|     Period Depreciation Expense    |     The amount of depreciation expense taken between the To   and From Dates                       |
|     Accumulated Depreciation       |     The amount of accumulated depreciation as of the From Date                                     |
|     Impairment                    	|     The amount the asset was impaired between date parameters                                     |
|     Modifications                  |     The amount of adjustments to the right of use asset   between date parameters                  |
|     Net Book Value                 |     The ending net book value of the right of use asset, net   of accumulated depreciation as of the To Date    |

## Differences report
The Differences report, shows the differences between information loaded into the Lease import framework and the information that's currently in the system. This lets you compare what was adjusted, updated, or added through the Lease import framework functionality.

The values in the report will vary based on the lease presented. The report will only show those fields that are differ from what is currently in the system and what is in the staging tables. The Old value is what is either currently in the system or that was previously in the system, depending on whether the import process has run. The New value are the values in the staging table and will replace the Old value.

## Five-years undiscounted payment forecast
The Five years undiscounted payment forecast report shows the projected undiscounted lease payments to be paid over the next five years from the date specified on the report parameters. The report includes the following fields. 

|     Name                 	|     Description                                                                                  	|
|--------------------------	|--------------------------------------------------------------------------------------------------	|
|     Lease Description    	|     The lease description from the lease header                                                  	|
|     Lease ID             	|     The unique lease ID                                                                          	|
|     Book                 	|     The lease book associated to the book ID                                                     	|
|     Classification       	|     The classification of the lease                                                              	|
|     Posting Layer        	|     The layer to which this lease is posting                                                     	|
|     Currency             	|     The currency of the lease                                                                    	|
|     Current              	|     The sum of all lease payments payable within the next 12   months from the Reporting Date    	|
|     13-24 Months         	|     The sum of all lease payments payable between 13 and 24   months from the Reporting Date     	|
|     25-36 Months         	|     The sum of all lease payments payable between 25 and 36   months from the Reporting Date     	|
|     37-48 Months         	|     The sum of all lease payments payable between 37 and 48   months from the Reporting Date     	|
|     49-60 Months         	|     The sum of all lease payments payable between 49 and 60   months from the Reporting Date     	|
|     Thereafter           	|     The sum of all lease payments payable on or after 61   months from the Reporting Date        	|

## GAAP cash flows report
The GAAP disclosures Report satisfies the US GAAP disclosure requirement specified in 842-20-50-4(g)(1). To view this report, click **Asset Leasing > Inquiries & reports > Disclosures > GAAP – cash flows**. 

|     Report Field                               	|     Description                                                                                                                                             	|
|------------------------------------------------	|-------------------------------------------------------------------------	|
|     From Date                                  	|     The date for which the report starts                                                                                                                    	|
|     To Date                                    	|     The date for which the report ends                                                                                                                      	|
|     Legal Entity                               	|     The legal entity tied to the leases                                                                                                                     	|
|     Lease Type                                 	|     The classification of the lease as either finance or   operating                                                                                        	|
|     Lease ID                                   	|     The unique lease ID                                                                                                                                     	|
|     Lease Description                          	|     The lease description from the lease header                                                                                                             	|
|     Lease Book                                 	|     The lease book for which the line is referring to                                                                                                       	|
|     Posting Layer                              	|     Each book that is attached to a fixed asset is set up for   a particular posting layer that has an overall depreciation objective.                      	|
|     Lease Group                                	|     The group which the lease is tied to                                                                                                                    	|
|     Currency                                   	|     The abbreviation for the transactional currency used. All   reports will convert the transactional currency to the reporting currency.                  	|
|     Finance Leases – Operating Cash Flows      	|     The sum of the total posted variable payments and the   total interest payments posted from the amortization schedule between the   date parameters.    	|
|     Finance Leases – Finance Cash Flows        	|     The sum of the total principal payments from the amortization   schedule between the date parameters.                                                   	|
|     Operating Leases – Operating Cash Flows    	|     The sum of all posted lease payments and posted variable   payments between the date parameters.                                                        	|


## Weighted-average discount rate report
The Weighted-Average Discount Rate Report satisfies the US GAAP disclosure requirement specified in ASC 842-20-50-4(g)(4) for a weighted-average discount rate. The report includes the following fields. 

|     Report Field                   	|     Description                                                                                                                                                                           	|
|------------------------------------	|----------------------------------------------------------------------------------------------------------------------------	|
|     As Of Date                     	|     This report will include all leases that have commenced   before or on the ‘As Of’ date parameter. This report should be run ‘As Of’   the last day of the period to be disclosed.    	|
|     Legal Entity                   	|     The legal entity that is tied to the lease                                                                                                                                            	|
|     Lease ID                       	|     The unique lease ID                                                                                                                                                                   	|
|     Lease Description              	|     The lease description from the lease header                                                                                                                                           	|
|     Book                           	|     The specific book type of the displayed lease                                                                                                                                         	|
|     Posting Layer                  	|     Each book that is attached to a fixed asset is set up for   a particular posting layer that has an overall depreciation objective.                                                    	|
|     Lease Group                    	|     The group to which the lease belongs                                                                                                                                                  	|
|     Discount Rate                  	|     The rate used to discount lease payments                                                                                                                                              	|
|     Currency                       	|     The abbreviation for the transactional currency used. All   reports will convert the transactional currency to the reporting currency.                                                	|
|     Lease Payments Remaining       	|     The total amount of unpaid lease payments from the payment   schedule remaining from the ‘As Of’ date                                                                                 	|
|     Weighted Payments Remaining    	|     The lease payments remaining multiplied by the discount   rate used.                                                                                                                  	|



