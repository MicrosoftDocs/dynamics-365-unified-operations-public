# Fixed asset Disposal scrap scenario

The fixed asset disposal scrap will eliminate asset’s transactions of acquisition, accumulated depreciation and other fixed assets transactions has effect on assets balance sheet accounts such as acquisition adjustment, depreciation adjustment, revaluation, write-up, and write-down. 

| Transaction                         |   | Dr | Cr |
|-------------------------------------|---|----|----|
| Dr. Accumulated depreciation        |   | xx |    |
| Cr. Fixed assets gain/loss          |   |    | xx |
|                                     |   |    |    |
| Dr. Fixed assets gain/loss          |   | xx |    |
| Cr. Fixed asset acquisition account |   |    | xx |
|                                     |   |    |    |
| Dr. Fixed assets gain/loss (NBV)    |   | xx |    |
| Cr. Fixed assets gain/loss (NBV)    |   |    | xx |

*Note: Need to work closely with CFO/Controller to identify the proper accounts for each transaction types, and verify the disposal scrap process and generated entry to ensure it gives the desired results.*    

The minimum requirement to dispose a fixed asset need to have ledger accounts associated to Acquisition value, Depreciation (this year), Depreciation (prior years), and Net book value. The fixed assets transactions types are listed in the fixed assets posting profile under disposal fast tab. To access fixed assets posting profile go to **Fixed assets| Setup| Fixed assets posting profile**  then move to **Disposal** fast tab and select **Scrap**. The following screen shot represents fixed assets posting profile:

<img src="media/Fixed_asset_Disposal_scrap_scenario_1.png">

Assuming we have a fixed asset acquired on Jan 1st 2018, required to scrap it in March 31st 2019. 

Acquisition price 	  		= 24,000.00 USD

Service life 		      		= 2 Years

Depreciation method is Straight line service line.

Depreciation amount			= 1000.00 USD per month

This fixed asset is acquired and depreciated for 15 months from Jan 2018 to March 2019. This means the asset Net book value is 9,000.00 USD.
Acquisition price 	= 24,000.00 USD

Depreciation 		    = (15,000.00) USD

Net book value	  	=    9,000.00 USD

<img src="media/Fixed_asset_Disposal_scrap_scenario_2.png">

To create a disposal journal, go to **Fixed assets| Journal entries| Fixed assets journal** then move to **Lines** then select **Disposal – scrap** and select fixed asset ID. To fully dispose the fixed asset do not enter amount in Debit/Credit fields.  

<img src="media/Fixed_asset_Disposal_scrap_scenario_3.png">

The fixed asset disposal scrap transaction will change the fixed asset book fields as the following; fixed asset Status to Scrapped and add Scrap date.  

<img src="media/Fixed_asset_Disposal_scrap_scenario_4.png">

Fixed asset balance

<img src="media/Fixed_asset_Disposal_scrap_scenario_5.png">
Posted voucher
<img src="media/Fixed_asset_Disposal_scrap_scenario_6.png">
