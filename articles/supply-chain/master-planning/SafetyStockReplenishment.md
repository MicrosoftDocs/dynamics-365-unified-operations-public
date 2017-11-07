# Setting up safety stock levels for items

Safety stock is set up part of item coverage (**Released products – Plan – Coverage – Item coverage**).

In the **Minimum** field, enter the safety stock level, that you want to maintain for the item. The value is expressed in inventory units. If you leave the field blank, the default value is zero. This field is available when you select **Period**, **Requirement**, or **Min./Max.** in the **Coverage code** list. The limit applies to the available inventory, meaning that reservations and markings may trigger safety stock replenishment.

You must define all other coverage planned dimensions before you can define this field. This rule prevents an invalid record from being used during master scheduling. This situation can occur if, for example, a dimension group is extended with an additional coverage planned dimension for which the minimum and maximum inventory quantities are not yet defined.

For items with demand patterns that follow a certain periodicity, you need to maintain different safety stock limits, following the item’s demand periodicity. To do that, you need to define **Minimum keys** (**Master planning – Setup – Coverage – Minimum/maximum keys**) and fill in the **Minimum key** field on the **Item coverage** form. You can view the information about the safety stock levels defined via minimum keys on the **Min./Max.** tab of the **Item coverage** form.

If coverage code is **Min./Max.**, you can also specify the **Maximum** inventory quantity that you want to maintain for the item. The value is also expressed in inventory units. If the projected available inventory falls below the minimum quantity, master planning generates a planned order to fulfill all open requirements and also bring the available inventory up to the specified maximum quantity.

### Min./Max. coverage code example
The minimum quantity is 10, and the maximum quantity is 15. Current on-hand inventory is 4. This gives a minimum quantity requirement of 6. However, because the maximum quantity is 15, master planning generates a planned order for 11.

Just like for **Minimum**, you must define all other coverage planned dimensions before you can define the **Maximum** field.

For items with demand patterns that follow a certain periodicity, you may need to maintain different maximum levels, following the item's demand periodicity. To do that, you need to define **Maximum keys** (**Master planning – Setup – Coverage – Minimum/maximum keys**) and fill in the **Maximum key** field on the **Item coverage** form. You can view the information about the safety stock levels defined via minimum keys on the **Min./Max.** tab of the **Item coverage** form. You need to make sure that, for a certain period, the minimum and the maximum values are kept in sync.



# Safety stock fulfillment 

The **Fulfill minimum** parameter allows you to select the date or the period during which the inventory level must meet the quantity that you specified in the **Minimum** field. This field is available when you select **Period**, **Requirement**, or **Min./Max.** in the **Coverage code** list.

The following options are available:
- **Today's date**: The specified minimum quantity is met on the date that master planning is run.
- **Today's date + procurement time**: The specified minimum quantity is met on the date that master planning is run, plus the
purchase or production lead time. This time includes any safety margins. If the item carries a trade agreement, and the **Find trade agreements** check box is selected in the **Master planning parameters** form, the delivery lead time from the trade agreement is not considered. Lead times are taken from the item's coverage settings or from the item.
- **First issue**: The specified minimum quantity is met on the date the available inventory goes below minimum.

The difference between these three fulfill minimum modes is related to the available inventory on the date master planning is run. If on the date master planning is run the available inventory is already under the safety stock limit, **Today's date** and **Today's date + procurement time** will trigger the replenishment imediately. **First issue** will wait until there is another issue transaction (sales order, BOM line requirement, etc) for the item and it will trigger the replenishment on the date of this transaction.

- **Coverage time fence**: The specified minimum quantity is met during the period that is specified in the **Coverage time fence** field.
