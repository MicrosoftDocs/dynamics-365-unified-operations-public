---
# required metadata

title: Asset leasing reports
description: This topic lists and briefly describes the reports that are available in Asset leasing.
author: moaamer
ms.date: 04/05/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysOperationTemplateForm 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-27
ms.dyn365.ops.version: 10.0.14
---

# Asset leasing reports

[!include [banner](../includes/banner.md)]

This topic lists and briefly describes the reports that are available in Asset leasing. Most reports display by completing these steps or steps that are very similar, as noted). 

- To view most Asset leasing reports, go to **Asset Leasing > Inquiries and reports > Lease reports** and then select a report to view. For the reports that require a different selection path, the steps to open the report are included with that report's description. 
- When you select a report to print, a parameters page will open that lets you filter the information that's included on the report. Enter filter criteria, and then select **OK** to generate the report. The generated report will show information that falls within the filters that you specified.

## Asset movement
The Asset movement report serves as a rollforward report for the right-of-use asset balances for each lease. This report lets you view the asset transactions of a lease during a specified period. The report includes the following fields. 

|     Report fields                  |     Description                                                                |
|------------------------------------|--------------------------------------------------------------------------------|
|     Commencement date              |     The commencement date of the lease’s earliest version.                     |   
|     Lease term                     |     The current version of the lease term.                            |
|     Short term Lease               |     If the lease is classified as a short-term lease will show as **Yes**.         |
|     Low value Lease                |     If the lease is classified as a low-value lease will show as **Yes**.          |
|     Initial right of use asset     |     The original value of the right-of-use asset from the initial recognition journal entry.      |
|     Beginning balance              |     The net book value of the right of use asset as of the **From date**.                         |
|     Period depreciation expense    |     The amount of depreciation expense taken within the date range defined for the report.        |
|     Accumulated depreciation       |     The amount of accumulated depreciation as of the **From date**.                               |
|     Impairment                     |     The amount the asset was impaired within the date range defined for the report.               |
|     Modifications                  |     The amount of adjustments to the right of use asset between date parameters.                            |
|     Net book value                 |     The ending net book value of the right of use asset, which is the net of accumulated depreciation as of the **To date**.    |

## Differences report
The Differences report shows the differences between information loaded into the Lease import framework and the information that's currently in the system. This lets you compare what was adjusted, updated, or added through the Lease import framework.  

The values in the report will vary based on the selected lease. The report will only show those fields that differ from what is currently in the system and what is in the staging tables. The old value is what is either currently in the system or what was previously in the system, depending on whether the import process has run. The new value shows the value that's in the staging table that will replace the old value.

## Five-years undiscounted payment forecast
The Five-years undiscounted payment forecast report shows the projected undiscounted lease payments to be paid over the next five years from the date specified on the report parameters. The report includes the following fields. 

|     Report fields        	|     Description                                                                                   	|
|--------------------------	|---------------------------------------------------------------------------------------------------	|
|     Lease Description    	|     The lease description from the lease header.                                                  	|
|     Lease ID             	|     The unique lease ID.                                                                          	|
|     Book                 	|     The lease book associated to the book ID.                                                     	|
|     Classification       	|     The classification of the lease.                                                              	|
|     Posting Layer        	|     The layer to which this lease is posting.                                                     	|
|     Currency             	|     The currency of the lease.                                                                    	|
|     Current              	|     The sum of all lease payments payable within the next 12 months from the reporting date.      	|
|     13-24 Months         	|     The sum of all lease payments payable between 13 and 24 months from the reporting date.       	|
|     25-36 Months         	|     The sum of all lease payments payable between 25 and 36 months from the reporting date.       	|
|     37-48 Months         	|     The sum of all lease payments payable between 37 and 48 months from the reporting date.       	|
|     49-60 Months         	|     The sum of all lease payments payable between 49 and 60 months from the reporting date.       	|
|     Thereafter           	|     The sum of all lease payments payable on or after 61 months from the reporting date.          	|

## GAAP cash flows report
The GAAP disclosures report satisfies the US GAAP disclosure requirement specified in 842-20-50-4(g)(1). To view this report, go to **Asset Leasing > Inquiries and reports > Disclosures > GAAP – cash flows**. 

|     Report fields                              	|     Description                                                                                                                                             	|
|------------------------------------------------	|-----------------------------------------------------------------------------	|
|     From date <br> To date                     	|     Defines a range of dates that's used to restrict the information included in the report.    	|
|     Legal Entity                               	|     The legal entity tied to the leases.                                    	|
|     Lease Type                                 	|     The classification of the lease as either finance or operating.         	|
|     Lease ID                                   	|     The unique lease ID.                                                   	|
|     Lease Description                          	|     The lease description from the lease header.                           	|
|     Lease Book                                 	|     The lease book for which the line is referring to.                     	|
|     Posting Layer                              	|     Each book that is attached to a fixed asset is set up for a particular posting layer that has an overall depreciation objective.                      	|
|     Lease Group                                	|     The group which the lease is tied to.                                   	|
|     Currency                                   	|     The abbreviation for the transactional currency used. All reports will convert the transactional currency to the reporting currency.                  	|
|     Finance Leases – Operating Cash Flows      	|     The sum of the total posted variable payments and the total interest payments posted from the amortization schedule between the   date parameters.    	|
|     Finance Leases – Finance Cash Flows        	|     The sum of the total principal payments from the amortization schedule between the date parameters.    	|
|     Operating Leases – Operating Cash Flows    	|     The sum of all posted lease payments and posted variable payments between the date parameters.         	|

## Lease balances forecast
The Lease balances forecast lists information directly from the liability amortization schedule and asset depreciation schedule. The report shows forecasted amounts of the projected lease liability, and right-of-use assets over a period of time, including all projected expenses for those leases. The report includes the following fields.

|     Report fields                	|     Description                                                                                                                                                                            	|
|---------------------------------	|--------------------------------------------------------------------------------------------------------------------	|
|     Beginning balance           	|     The beginning balance in the lease’s amortization schedule for the period containing the start date of the report.         	|
|     Initial recognition         	|     If the commencement date of the lease falls within the date range defined for the report, this column will display the liability account value of the initial recognition journal entry.    	|
|     Payments                    	|     The sum of the lease’s payments that fall within the date range defined for the report.                            	|
|     Interest                    	|     The sum of the lease’s interest expenses that fall within the date range defined for the report.                    |
|     Ending balance              	|     The liability balance of the lease as of the **To date**.                                                         	|
|     Short-term liability        	|     The short-term liability amount in the lease’s amortization schedule as of the **To date**.                        	|
|     Long term liability         	|     The long-term liability amount in the lease’s amortization schedule as of the **To date**.                         	|
|     Beginning Net Book Value    	|     The “Beginning Net Book Value” in the lease’s asset depreciation schedule for the period containing the start date of the report    	|
|     Initial recognition         	|     If the commencement date of the lease falls between the report’s date parameters, this column will display the asset account value of   the initial recognition journal entry.        	|
|     Depreciation expense        	|     The sum of the lease’s depreciation expenses that fall within the date range defined for the report.                  |
|     Ending balance              	|     The asset balance as of the lease as of the **To date**.                                                             	|
|     Equity adjustment           	|     The beginning balance minus the beginning net book value.                                                             |

## Lease commencements report
The Lease commencements report shows all leases that have commenced within a specified date range including the initial liability and right-of-use asset balances. The report includes the following fields. 

|     Report fields                	|     Description                                                                                   	|
|---------------------------------	|---------------------------------------------------------------------------------------------------	|
|     Commencement Date           	|     The date of the initial recognition journal entry that was posted for that lease version.     	|
|     Initial liability amount    	|     The liability amount from the initial recognition journal entry.                              	|
|     Initial asset amount        	|     The asset amount from the initial recognition journal entry.                                  	|

## Lease modification report
The Lease modification report shows all leases that have been modified within a specified date range. The report also shows the user who adjusted the lease, and the total amount of liability adjusted. The report includes the following fields. 

|     Report fields               	|     Description         	|
|---------------------------------	|-------------------------	|
|     Adjusted by                 	|     The username of the person who modified the lease.                             	|
|     Adjustment fate             	|     The date on which the adjustment journal entry was posted.                     	|
|     Adjustments                 	|     The amount for any adjustment journal entry posted to the lease’s liability account between the date parameters. Credits will appear   positive, while debits will be negative.    	|
|     Gain (loss) amount          	|     The amount for any adjustment journal entry posted to the lease’s gain/loss account between the date parameters. Credits will appear   positive, while debits will be negative.    	|
|     Retained earnings           	|     The amount for any adjustment journal entry posted to the lease’s retained earnings account between the date parameters.     	|
|     Ending liability balance    	|     The resulting liability balance as of the adjustment date of the lease.       	|

## Lease movement report
The Lease movement report serves as a rollforward report for the lease liability balances for each lease. This report allows the user to view the liability transactions of a lease during a specified period.

|     Report fields          	|     Description                                             	|
|----------------------------	|--------------------------------------------------------------	|
|     Commencement date      	|     The commencement date of the lease’s earliest version.   	|
|     Lease term             	|     The lease term of the lease’s earliest version.           |
|     Payments remaining     	|     The number of payments that have not yet been posted for the lease.                    	|
|     Beginning balance      	|     The sum of all transactions affecting the lease’s liability that occurred before the report’s start date.            	|
|     Initial recognition    	|     The amount of any initial recognition transaction for the lease that was posted within the date range defined for the report.   	|
|     Payments               	|     The sum of the lease’s payment transactions that have been posted within the date range defined for the report. The values in this column will appear as negative amounts as the payments are decreasing the lease’s liability balance.  |
|     Interest               	|     The sum of the interest accruals that have been posted against the lease within the date range defined for the report.          	|
|     Adjustments            	|     The sum of the lease’s posted adjustment transactions within the date range defined for the report.                             	|
|     Ending balance         	|     The balance of all the lease’s liability transactions that have been posted as of the **To date** of the report.                 	|

## Lease transactions report
The Lease transactions inquiry shows all the journal entries that have been generated by Asset leasing. Each journal entry is linked with the book ID it was originated from. This lets you easily associate the journal entry with corresponding lease. The Lease transactions inquiry functions in a manner that's similar to the **Voucher transactions** page in General ledger.

## Weighted-average discount rate report
The Weighted-average discount rate report satisfies the US GAAP disclosure requirement specified in ASC 842-20-50-4(g)(4) for a weighted-average discount rate. To view this report, go to **Asset Leasing > Inquiries and reports > Disclosures > Weighted-average discount rate**. The report includes the following fields. 

|     Report fields                  	|     Description                                                       	|
|------------------------------------	|------------------------------------------------------------------------	|
|     As of date                     	|     This report will include all leases that have commenced on or before the **As of** date parameter. This report should be run as of   the last day of the period to be disclosed.    	|
|     Legal entity                   	|     The legal entity that is tied to the lease.                       	|
|     Lease ID                       	|     The unique lease ID.                                               	|
|     Lease description              	|     The lease description from the lease header.                      	|
|     Book                           	|     The specific book type of the displayed lease.                                                                                                                                         	|
|     Posting layer                  	|     Each book that is attached to a fixed asset is set up for a particular posting layer that has an overall depreciation objective.   	|
|     Lease group                    	|     The group to which the lease belongs.                              	|
|     Discount rate                  	|     The rate used to discount lease payments.                          	|
|     Currency                       	|     The abbreviation for the transactional currency used. All reports will convert the transactional currency to the reporting currency. 	|
|     Lease payments remaining       	|     The total amount of unpaid lease payments from the payment schedule remaining from the **As of** date.         	|
|     Weighted payments remaining    	|     The lease payments remaining multiplied by the discount rate used.   |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
