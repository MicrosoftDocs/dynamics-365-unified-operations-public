

# Withholding tax in purchase transactions

For vendors who are liable to withholding tax, you can assign the default **Withholding tax group** in the vendor master.

1. Go to **Navigation pane > Modules > Accounts payable > Vendors > All vendors**.

2. Click the respective Vendor account, click **Edit**.

3. In sub-form **Invoice and delivery**, switch on **Calculate withholding tax**.

   > [!NOTE] 
   > Withholding tax will not be calculated if **Calculate withholding tax** is not switched on for this vendor in the master data.

4. Select a withholding tax group in **Withholding tax group**.

5. Click **Save**.

For items/services which are liable to withholding tax, you can assign the default **Item withholding tax group** in **Released Products**.

1. Go to **Navigation pane > Modules > Product information management > Products > Released products**.

2. Click the respective Item number, click **Edit**.

3. In sub-form **Purchase**, switch on **Calculate withholding tax**.

   > [!NOTE] 
   > Withholding tax will not be calculated if **Calculate withholding tax** is not switched on for this Item in the sub-form **Purchase** of the Released product.

4. Select an Item withholding tax group in **Item withholding tax group**.

5. Click **Save**.

Withholding tax groups and Item withholding tax groups can be assigned in forms: 

- **Purchase order**
- **Vendor invoice**
- **Invoice journal**

The default Withholding tax group and Item withholding tax group will be carried into the lines when creating **Purchase orders** and/or **Pending Vendor invoices**. For **Vendor invoice journal**, you can switch on **Calculate withholding tax** and select **Item withholding tax group** in the **General** tab in the journal.

The temporary amount of withholding tax is available in the field **Adjusted withholding tax** of the sub-form **Totals** in form **Purchase order**.

![](media/withholding-tax-adjusted.png)

Withholding tax is calculated on **Vendor payment journal**. You can manual adjust the applicable withholding tax codes as well as the actual withholding tax amounts in the **Withholding tax** tab in the **Settle transactions** form.

![](media/withholding-tax-vendor-payment-tab.png)

The derived withholding tax amount will be deducted from the vendor payment and posted to the **Withholding tax account** in a related voucher.

![](media/withholding-tax-adjusted.png)
