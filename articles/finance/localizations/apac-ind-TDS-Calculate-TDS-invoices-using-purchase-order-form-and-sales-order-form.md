# Calculate TDS invoices using purchase order form and sales order form

Follow these steps to calculate TDS on invoices using **Purchase** **order** form, **Purchase** **journal** form, **Blanket** **order** form, and **Sales** **order** form:

1. Create a purchase order, purchase journal, purchase blanket order, or a sales order using the forms listed in the table. Enter the required details.

2. Click the **Setup** tab. Under the **Withholding** **tax** **group** field group, in the **Nature** **of** **assessee** field, view the nature of the assessee of the vendor or customer.

3. In the **TDS** **group** field, view or modify the default TDS group defined for the vendor or customer.

>   [!Note]
>
>   The **TCS** **group** field becomes  unavailable when you select a TDS group in the **TDS** **group** field.  TDS is calculated only if the **Calculate** **withholding** **tax** check box is selected for the vendor or customer in the Vendors  form or Customers form.  

4. Create item lines on the **Lines** tab and enter the required details.

5. Click the **Setup** tab (line-level). Under the **Withholding** **tax** **group** field group, the **TDS** **group** field, the TDS group defined at the header-level is displayed in and can be changed.

6. Click the **Tax** **information** tab. Under the **Company** **information** field group, in the **Name** field, the company name is displayed. Select a company name of alternate addresses that are set up for the company in this field. 

7. Under the **Withholding** **tax** field group, in the **Tax** **Account** **Number** (**TAN**) field, the TAN of the selected company name is displayed. 

8. Click the **Withholding** **tax** button to open the **Temporary** **withholding** **tax** **transactions** form. View the following fields on the upper pane of the **Temporary** **withholding** **tax** **transactions** form.

- **Withholding** **tax** **amount** **in** **total** field: The total TDS calculated for the transaction for the TDS group.

- **Value** field: The total percentage used to calculate TDS for the transaction. The total percentage is based on the formula that is defined for TDS tax codes attached to the TDS group.

- **Adjusted** **withholding** **tax** **amount** **in** **total** field: The total adjusted TDS amount for all tax codes in the TDS group.

- **TDS** check box: This check box is displayed as selected if a TDS group is attached to the transaction.

The fields on the **Overview** tab, **General** tab, and **Adjustment** tab in the **Temporary** **withholding** **tax** **transactions** form display the calculated TDS amount and adjusted TDS amount details for each TDS tax code attached to the TDS group.

9. Click the **Threshold** button to open the **Threshold** form. View the threshold limit defined for the TDS tax component attached to a specific TDS tax code in this form.

10. Click the **Formula** **designer** button to open the **Formula** **designer** form. View the formula that is defined for a specific TDS tax code in this form. 

11. Post the invoice. The TDS amount calculated on purchase invoices is posted to the payable account and the TDS amount calculated on sales invoices is posted to the receivable account that is defined for each TDS tax code in the TDS group. The payable accounts or receivable accounts for TDS tax codes are defined in the **Withholding** **tax** **codes** form.

12. Click inquiry button > invoice > posted withholding tax button to open the **Withholding** **tax** **transactions** form. In the **Value** field, view the total percentage used to calculate TDS for the transaction.

The fields on the **Overview** tab, **General** tab, and **Amount** tab in the **Withholding** **tax** **transactions** form display the information of TDS calculated for the transaction. View the TDS calculation information for each TDS tax code attached to the TDS group.
