To enable India localization solution for GST in Dynamics 365 for finance and operation, below master data setup configurations are required:

- Define business vetical
- Update the state code and union territory
- Create a GSTIN master
- Define GSTIN numbers for the legal entity, warehouse, vendor, or customer masters
- HSN codes and Service accounting codes
- Create main accounts for the GST posting type
- Create a tax settlement period
- Attach the GSTIN to a tax registration group

This article describes how to define GSTIN numbers and reference number sequence for legal entity, warehouse, vendor, or customer masters.

## Define GSTIN numbers and number sequence for legal entity

1. Click **Organization administration > Organizations > Legal entities > Addresses > More Options > Advanced**
2. In the **Tax information** tab, click **Add**
3. In the **Name or description** field, enter a value
4. On the **GST** FastTab, in the **GSTIN/GDI/UID** field, select a value; in the **Reference number sequence group** field, select a value
5. Select the **Primary** check box
6. Click **Yes** to acknowledge the message
7. **Save** the record
8. Click **Close**
9. Repeat steps 2 through 7, for all the other required legal entity addresses

![Define GSTIN for legal entity](media/GST-Whitepaper/Define-GSTIN-for-legal-entity.png)



## Define GSTIN numbers and number sequence for warehouses

1. Click **Inventory management > Setup > Inventory breakdown > Warehouse > Addresses > Advanced**
2. On the **Tax information** tab, click **Add**
3. In the **Name or description** field, enter a value
4. On the **GST** FastTab, in the **GSTIN/GDI/UID** field, select a value
5. Select the **Primary** check box
6. Click **Yes** to acknowledge the message
7. **Save** the record
8. Click **Close**

![Define GSTIN for warehouse](media/GST-Whitepaper/Define-GSTIN-for-warehouse.png)



## Define GSTIN numbers for vendors

1. Click **Accounts payable > Vendors > All vendors > Addresses > More Option > Advanced**
2. In the **Tax information** tab, click **Add**
3. In the **Name or description** field, enter a value
4. On the **GST** FastTab, in the **GSTIN/GDI/UID** field, select a value
5. Select the **Primary** check box
6. Click **Yes** to acknowledge the message
7. **Save** the record
8. Click **Close**

![Define GSTIN for vendor](media/GST-Whitepaper/Define-GSTIN-for-vendor.png)

9. On the **Tax information** FastTab, select the **Composition scheme** check box if a composition scheme is used to purchase from the dealer

![Composite Dealer](media/GST-Whitepaper/Composite-Dealer.png)



## Define GSTIN numbers for customers

1. Click **Accounts receivable > Customers > All customers > Addresses > More Option > Advanced**
2. In the **Tax information** tab, click **Add**
3. In the **Name or description** field, enter a value.
4. On the **GST** FastTab, in the **GSTIN/GDI/UID** field, select a value.
5. Select the **Primary** check box.
6. Click **Yes** to acknowledge the message.
7. **Save** the record.
8. Click **Close**.
![Define GSTIN for customer](media/GST-Whitepaper/Define-GSTIN-for-customer.png)
9. On the **Tax information** FastTab, select the **Consumer** check box to identify the customer as a consumer
10. For customer sales through an e-commerce operator, enter a value in the **Merchant ID** field, and select a value in the **Default E-Commerce operator** field
11. In the **Customer type** field, select **Govt company or other agencies** for sales with government companies or other agencies
![E-commerce operator](media/GST-Whitepaper/E-commerce-operator.png)

