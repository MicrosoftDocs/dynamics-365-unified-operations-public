
# Store hours

The new store hours feature provides the ability to capture and maintain multiple sets of store operating hours for a retailer. Dynamics 365 for Retail currently had no out-of-box solution to let retailers showcase their store operating hours across different channels like store, call center, mobile, e-commerce, and so on.

Retailers can now create and manage their store hours in Retail AX Headquarters and have cashiers look up store hours across various locations to assist customers in their shopping experience. It also allows retailers to print them at the footer of the receipt to notify customers when the stores are accessible to retail customers. 


## How to use the store hours feature
This feature is only available from Dynamics 365 Version 8.1.2 and latter

This configuration page is in AX Headquarters, **Retail** -> **Channel Setup** -> **Store hours**.

When the holiday and store hours are known, the admin can set the store hours for the whole year or to an even longer schedule.

The First step is to create a **Store hours template** -> Click +**New**  (If you have an exisiting **Store hours template**, it will be listed on the left pane) 

![Store Hours Template](../dev-itpro/media/Storehours1.png "Store hours template")  

After a Template is created or selected, user needs to define the period of the date range. 
1. If the store hours are constant and do not change - then select 'End Date' = Never ends. 
2. If the store hours are for a specific month/week/day - set the 'Start Date' & 'End Date'
3. Users can create mutliple templates with overlapping 'start Date' & 'End Date' - different store hours for stores in different time-zones. 

The next step, is to associate the 'Store hours' template to mutliple stores, 
This calendar is now made available for the different store or store groups. The calendar is set for all the stores and should be visible in the POS for reference.

![Save Store Hours Template](../dev-itpro/media/Storehours2.png "Save Store hours template") 

A cashier completing a sale prints the receipt, where the store hours are visible for the customer. Upcoming holidays—when the store is closed—are also made visible on the receipt.

![Receipt Template](../dev-itpro/media/Storehours3.png "Receipt template") 

If a customer has a pickup order for a different store, the cashier can select the right dates where the pickup will be available in that store. The store lookup will provide a reference to the dates and store times. The cashier will choose a date and location and print a pickup receipt with the store hours. 

![Store Card Template](../dev-itpro/media/Storehours4.png "Store Card template") 

## Business value
All retail stores have store hours when they are open for retail customers. In many cases, store hours vary from weekdays to weekends, from various geographies, seasons, and times of the year. Customers need to be able to quickly glance and be aware of when the retail stores are open. 

Retailers can use the new store hours feature to create, maintain, and manage the store hours for different stores across geographies from a single point. Retailers can showcase the new store hours in POS terminals, letting the cashiers share store hours to customers and assist shoppers while looking for inventory in different stores. Customers also can see the new store hours printed on their receipts in case they wish to return to the store. 

Store hours functionality can be leveraged on e-commerce websites, mobile apps, kiosks, and so on. Future enhancements to this feature might be to enable the retailer to set an appropriate pickup date based on holiday hours and store closures.
