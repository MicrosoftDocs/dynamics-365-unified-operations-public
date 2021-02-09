# TDS calculation on invoices using free text invoice form

Follow these steps to calculate TDS on invoices using the **Free** **text** **invoice** form.

 Go to **Accounts receivable > Invoices > All free text invoices**

[![Free text invoices](./media/apac-ind-TDS-57-1.png)](./media/apac-ind-TDS-57-1.png)

2. Click **New** to create a new free text invoice and enter the required details.

3. Click the **Invoice** tab. Under the **Withholding** **tax** **group** field group, in the **Nature** **of** **assessee** field, view the nature of the assessee of the customer.

4. In the **TDS** **group** field, view or modify the default TDS group defined for the customer. 

>   [!Note]
>
>   The **TCS** **group** field  becomes unavailable when you select a TDS group in the **TDS** **group**  field.  TDS is calculated only if the **Calculate** **withholding**  **tax** check box is selected for the customer in the **Customers**  form.   

4. Click the **Tax** **information** tab. Under the **Company** **information** field group, in the **Name** field, view the company name. Select a company name of alternate addresses that are set up for the company in this field.  

5. Under the **Withholding** **tax** field group, in the **Tax** **Account** **Number** (**TAN**) field, view the TAN of the selected company.

6. Create invoice lines on the **Invoice** **lines** tab and enter the required details. Under the **Withholding** **tax** **group** field group, in the **Tax** **Account** **Number** (**TAN**) field, view the TAN. In the **TDS** **group** field, view the TDS group.

7. Click the **Withholding** **tax** button to open the **Temporary** **withholding** **tax** **transactions** form. The following fields are displayed on the upper pane of the **Temporary** **withholding** **tax** **transactions** form.

- **Withholding** **tax** **amount** **in** **total** field: The total TDS calculated for the transaction for the TDS group.

- **Value** field: The total percentage used to calculate TDS for the transaction. The total percentage is based on the formula that is defined for TDS tax codes attached to the TDS group.

- **Adjusted** **withholding** **tax** **amount** **in** **total** field: The total adjusted TDS amount for all tax codes in the TDS group.

- **TDS** check box: This check box is displayed as selected if a TDS group is attached to the transaction.

> [!Note]
>
> The fields on the **Overview** tab, **General** tab, and **Adjustment** tab in the **Temporary** **withholding** **tax** **transactions** form display the calculated TDS amount and adjusted TDS amount details for each TDS tax code attached to the TDS group.

8. Click the **Threshold** button to open the **Threshold** form. View the threshold limit defined for the TDS tax component attached to a specific TDS tax code.

9. Click the **Formula** **designer** button to open the **Formula** **designer** form. View the formula defined for a specific TDS tax code.

10. Post the free text invoice. The TDS amount calculated on the free text invoice is posted to the receivable account that is defined for each TDS tax code in the TDS group. The receivable accounts for TDS tax codes are defined in the **Withholding** **tax** **codes** form.

11. Click **Posted withholding tax** button to open the **Withholding** **tax** **transactions** form. In the **Value** field, view the total percentage used to calculate TDS for the transaction.

The fields on the **Overview** tab, **General** tab, and **Amount** tab in the **Withholding** **tax** **transactions** **form** display the information of TDS calculated on the invoice lines. View the TDS calculation information for each TDS tax code attached to the TDS group.