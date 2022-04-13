

# Set up return locations for retail stores

This topic explains how to set up return locations that are based on retail info codes and sales and marketing reason codes. Cashiers often identify the reason for a return when a customer returns a purchase. You can specify that returned products are assigned to different return locations in inventory based on the cashier’s response to info codes and reason codes that are displayed at the Point of Sale (POS) register.
For example, when a customer returns a defective product, the cashier processes the return transaction, Retail POS displays the info code for returns, the cashier selects the subcode for defective returns, and the returned product is automatically assigned to a specific return location.
A return location can be a warehouse, a location within a warehouse, or even a particular pallet, depending on what inventory locations your organization has set up. You can map each return location to one or more info codes in Retail and reason codes in Sales and marketing.
 
## Prerequisites
Before you can set up return locations, you must set up the following:
	• Retail info codes – Prompts at the POS register that are set up in the Retail module. For more information, see  https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/setting-up-info-codes.
	• Sales and marketing reason codes – Prompts at the POS register that are set up in the Sales and marketing module. For more information, see  https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-return-reason-codes.
	• Inventory locations – The places where inventory is kept. For more information, see  https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/about-locations.
To set up return locations, follow these steps:
	1. Click Warehouse management > Setup > Warehouse setup > Warehouses.
	2. Select a warehouse, and then on the Retail FastTab, in the Default return location field, select an inventory location.
This is the inventory location for returns whose info codes or reason codes are not mapped to return locations.
	3. In the Default return pallet field, select a pallet.
This is the pallet for returns whose info codes or reason codes are not mapped to return locations.
	4. Click **Retail & Commerce** > **Inventory management** > **Return locations**.
	5. In the Return locations form, click New to create a new return location policy.
	6. Enter a unique name and a description for the return location.
- ![Note]
- The name is entered automatically if a number sequence has been set up for return locations.
	7. On the **General** FastTab, select the **Print labels** check box to print labels for all the products that are assigned to return locations.
	8. On the **General** FastTab, select the **Block inventory** check box to take the returned products in the default return location out of inventory and prevent them from being sold. 
	9. To map specific retail info codes and subcodes to return locations, click Add on the Map retail info codes FastTab, and then enter the following information:
		○ In the Reason code field, select an info code for returns.
		○ In the Subcode field, select a subcode for the reason for the return.
		○ The Description field displays a description of the selected info code.
		○ In the Store field, select the store where the info code is used.
		○ Use the Warehouse, Location, and Pallet ID fields to specify a return location. For example, to specify a particular location in a store, select a store in the Store field and a location in the Location field.
		○ Select the Block inventory check box to take returned products out of inventory and prevent them from being sold. This is represented by number 1 in red color in the <<"Return location" image>. 
	10. To map specific sales and marketing reason codes to return locations, click Add on the Map sales and marketing reason codes FastTab, and then enter the following information:
		○ In the Info code field, select a reason code for returns.
		○ The Description field displays the description of the selected reason code.
		○ In the Store field, select the store where the reason code is used.
		○ Use the Warehouse, Location, and Pallet ID fields to specify a return location. For example, to specify a particular pallet in a location in a warehouse, select a warehouse in the Warehouse field, a location in the Location field, and a pallet in the Pallet ID field.
		○ Select the Block inventory check box to take returned products out of inventory and prevent them from being sold.
[!Note]
	- If for an item, a return location policy is used, but the return reason selected by the cashier does not match any of the codes mentioned in the Retail info codes or Sales and marketing reason codes FastTabs, then the item is sent to the default return location defined on the Warehouse form. Refer the "Default_Return_Location" image below. Additionally, the **Block inventory** checkbox on the **General** FastTab will determine if the returned item should be inventory blocked or not.  This is represented by number 2 in blue color in the <<return location image shown earlier in this document>.  
	11. Since there can be multiple Return locations policies defined for the same store, so the determination of which return location policy will be used depends on the Return location selected for the category on Commerce product hierarchy. Navigate to the "Retail and Commerce -> Commerce product hierarchy and choose a **Return location** under the **Manage inventory category properties" FastTab. Refer the Commerce product hierarchy image below


![image](https://user-images.githubusercontent.com/28161726/163286906-9beea77c-6fd5-48ba-b201-874920151daa.png)
