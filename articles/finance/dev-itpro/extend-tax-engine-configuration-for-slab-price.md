# Extend tax engine configurations for slab price
[!include [banner](../includes/banner.md)]

Follow this guide to set up the Tax engine configuration extension for slab price, with steps tailored for India. Ensure that you've completed the [Prerequisites step](extend-tax-engine-configurations.md#prerequisites) before beginning.

## Activate the tax configuration
### Create extension configurations
1. Create a new taxable document that is derived from Taxable Document (India).
   - Open the **Localization configurations** workspace.
   - Click **Tax configurations**.
   - Navigate to the **Taxable Document (India)** configuration, and then click **Create configuration**.
   - Select the **Derive from Taxable document model** option, and then enter a name and description for the derived 
taxable document.
2. Create a new tax document that is derived from Tax (India GST).
   - Navigate to the **Tax (India GST)** configuration, and then click **Create configuration**.
   - Select the **Derive from Tax configuration** option, and then enter a name and description for the derived tax 
document.

### Add the Net price to Taxable Document India (India Contoso)
1. Navigate to the **Taxable Document (India Contoso)** configuration, and then click **Designer**.
2. Navigate to **Tax document > Header > Lines**, and then click **New** to create a new node.
3. Enter a name for the node, and select the item type:
   - **Name:** Net Price
   - **Item type:** Real
4. In the **Configurations** workspace, click **Change status**, and then select **Complete**.
5. Enter a description such as **Slab price**, and then click **OK**.
6. If there are any errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

### Change the data model of Tax (India GST Contoso)
1. Navigate to the **Tax (India GST Contoso)** configuration, and then click **Designer**.
2. Click **Tax document**, and then select **Taxable Document (India Contoso)** as the data model and **1** as the data 
model version.
3. Click **Save** to save the configuration.

### Modify rate/percentage lookups
1. Expand the **CGST** tax component node.
2. Select the measure of the **Rate**.
3. Click **Columns** to add **Net Price** as condition of rate table.
4. Select the same attributes that SGST uses.

> [!NOTE]
> Don't click **Add**. Values that you enter here have no effect on the actual rate table. That table should be 
completed at **Tax > Tax configuration > Tax setup**.

5. Save the tax document.

### Complete the tax document configuration
1. Save the configuration, and close the designer.
2. In the **Configurations** workspace, click **Change status**, and then select **Complete**.
3. Enter a description such as **Slab price**, and then click **OK**.
4.  If there are any errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

### Download the tax document configuration
1. In the **Versions** grid, select the **Tax (India GST Contoso)** configuration.
2. Click **Change status**, and then select **Share**.
3. Click **Yes**.
4. Repeat steps 1 through step 3 for the **Taxable Document (India Contoso)** configuration.

> [!NOTE]
> The configuration will be saved in the C:\India GST Configurations folder that you created earlier. Currently, 
all configurations are in that folder. You must then copy the folder to the Microsoft Dynamics AX environment 
where the configuration must be applied.

## Import the configuration and deploy it to a specific company
1. Save all the configuration files in one folder that Microsoft Dynamics AX Application Object Server (AOS) can access
2. Go to **General ledger > Setup > Sales tax > India > Load configurations**.
3. Set the directory to the folder where you saved the configuration files.
4. Click **OK**.
5. Click **Close**.
6. Go to **General ledger > Setup > Sales tax > India > Tax setup**.
7. Select the current working tax setup.
8. Click **Configurations**.
9. Click the **Tax configuration** tab, and then, under **Available configurations**, click **New** to create a tax 
configuration.

> [!NOTE]
> Any tax configurations that you add are listed in the **Available configurations** grid.

10. Select the required configuration (for example, **Tax (India GST Contoso)** and version (for example, **1**)), and then click **Synchronize**.
11. Click **Activate**.
12. Click **Setup** to set up data for the new version.
13. Setup tax rate as per business requirement as below


## Modify the data provider in Microsoft Dynamics AX
### Check the system name of the Net Price
1. Add a tax engine model field for Net Price.
   - In the AOT, open Classes > TaxableDocRowDataProviderExtensionLine. In classDeclaration, add a new macro for Net Price. `#define.NetPrice('Net Price')`

### Implement logic to determine Net Price
1. Add a new method for the TaxableDocRowDataProviderExtensionLine class, and implement the determination logic in the method.

### Pass the Net Price to GTE
1. Pass the Net Price to GTE in `TaxableDocRowDataProviderExtensionLine.fillInExtensionFields()`.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]