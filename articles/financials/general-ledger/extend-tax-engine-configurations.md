---
# required metadata

title: Tax engine
description: This topic provides information about extending tax engine configurations.
author: yijialuan
manager: AnnBe
ms.date: 12/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: riluan
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Extending tax engine configurations

[!include[banner](../includes/banner.md)]


The Tax engine (Also referred to as GTE) lets you configure tax rules that determine tax applicability, calculation, posting, and settlement, based on legal and business requirements.

In this topic, you will learn the Tax engine configuration extension process using the following example scenarios that apply to India.

-	Extend the Tax engine configuration for UTGST
-	Use a Reference Model to apply a tax rate of BCD for import order of goods from different countries/regions

The following tax terms are mentioned in this topic:

|Tax term | Full name|
|-----|-----------|
|GST | Goods and Services Tax|
|UTGST | Union Territory Goods and Services Tax|
|CGST | Central Goods and Services Tax|
|IGST | Integrated Goods and Services Tax |
|BCD| Basic Customs Duty|

## Activate the tax configuration
Before you can complete the example scenarios, you must activate the tax configuration using the following steps. 

1.	Navigate to **Organization administration** > **Workspaces** > **Electronic reporting**.
2.	In the **Configuration providers** section, click **Repositories** on the **Microsoft** provider.

![Load configuration](media/gte-extension-repositories.png)

3. Click **Add**. 
4. Select the **LCS** option. 
5. Click **Create repository** to create an LCS configuration repository.
6. Enter a name and description for the repository and then click **OK**.
7. Select the new LCS configuration repository in the list, and then click **Open**.
8. In tree, select the latest tax document (for example, select **Tax (India GST)**).
9. In the **Versions** section, click **Import**.

![Load configuration](media/gte-extension-import-configurations.png)

10. Click **Yes**.

![Load configuration](media/gte-extension-import-configurations2.png)

11. Close the page.

12. Click **Solutions**.

![Solutions link](media/gte-extensions-solution.png)

13. Create a new solution and enter the required information.

![Solution information](media/gte-extensions-solution2.png)

14. Click **Set active** to activate the new solution.

![Active solution](media/gte-extension-active-solution.png)

## Scenario 1: Extend the Tax engine configuration for UTGST

For union territories that don’t have a legislature, the GST Council introduced UTGST, which is on a par with SGST. UTGST applies to the following union territories of India:

-	Chandigarh
-	Lakshadweep
-	Daman and Diu
-	Dadra and Nagar Haveli
-	Andaman and Nicobar Islands

However, SGST can also be applied in union territories such as New Delhi and Puducherry, which have their own legislatures and can be considered “states” per the GST process.

For UTGST, the following combinations of taxes can be applied for any transaction:

-	Supply of goods and services within a state (intrastate): CGST + SGST
-	Supply of goods and services within union territories (intra-UT): CGST + UTGST
-	Supply of goods and services across states or union territories (interstate/inter-UT): IGST

The order of utilization for the Input Tax Credit of UTGST is the same as it is for the Input Tax Credit of SGST. Therefore, Input Tax Credit of SGST or UTGST is first set off against SGST or UTGST, respectively. The Output Tax liabilities and any balance can be set off against IGST Output Tax liabilities.

To support the scenario, the following must be done:
1.	Extend the taxable document so that it includes the **IntraStateInUnionTerritory** flag.
2.	Do data mapping for the extended taxable document to get the value from transaction to GTE
3.	Change the applicability of State GST (SGST).
4.	Add and configure UTGST.
5.	Import the extended configuration and deploy it to a specific company. 


### Task 1: Create extension configurations

#### Task 1.1: Create a new taxable document that is derived from Taxable Document (India)

1. On the **Localization configurations** workspace (**Organization administration** > **Workspaces** > **Electronic reporting**), click **Tax configurations**.
2. In the tree, find the **Taxable Document (India)** configuration, and then click **Create configuration**.
3. Select the **Derive from Taxable document model** option, and then enter a name and description for the derived taxable document. For this example, enter the name **Taxable Document (India Contoso)**.
4. Click **Create configuration**.

#### Task 1.2: Create a new tax document that is derived from Tax (India GST)

1. In the tree, select the **Tax (India GST)** configuration, and then click **Create configuration**.
2. Select the **Derive from Tax configuration** option, and then enter a name and description for the derived tax document. For this example, enter the name **Tax (India GST Contoso)**.
3. Click **Create configuration**.

### Task 2: Add the IntraStateInUnionTerritory flag to Taxable Document (India Contoso)

 1. In the tree, find the **Taxable Document (India Contoso)** configuration that you created in [Scenario 1: Task 1.1](#task-11-create-a-new-taxable-document-that-is-derived-from-taxable-document-india), and then click **Designer**.
 2. In the tree, go to **Taxable document** > **Header** > **Lines**, and then click **New** to create a new node.
 3. Enter a name for the node, and select the item type:
	-	**Name:** IntraStateInUnionTerritory
	-	**Item type:** Enum

	![Create a new node](media/gte-create-node-tax-document.png)

 4. Click **Add**.
 5. On the **Node** FastTab, click **Switch item reference**.
 6. Select **NoYes** in the tree, and then click **OK**.
 7. Save the configuration, and close the designer.
 8. With **Taxable Document (India Contoso)** still selected in the tree, click **Change status** > **Complete** in the **Versions** list.

	![Update the configuration status](media/gte-change-configuration-status.png)

 9. Enter a description such as **UTGST**, and then click **OK**.
 10. If there are any errors, open the designer, click **Validate**, and fix the errors.
 11. After the status is updated to **Complete**, the configuration is ready for deployment.
 
### Task 3: Complete data mapping for the extended taxable document
There are data mappings for each taxable document (purchase order, sales order, etc.) and reference mode in the taxable document. The purpose of data mapping is to get the value from taxable transactions and pass it into GTE for tax applicability, tax calculation, etc. 
For convenience, there is a special data source called **Taxable document source** which encapsulates most common tax relevant fields like Assessable Value, HSN, SAC, etc. So, there are two methods for retrieving and mapping the value of the additional field to your extended taxable document.

- 	Method 1: Enable the additional field for the existing Taxable document source.
-	Method 2: Use Electronic reporting (ER) data mapping
 
#### Method 1: Data mapping by Taxable document source
Before you use this method, be sure to read about [Tax engine integration](tax-engine-integration.md) so you understand the underlying concepts. The Tax engine must determine whether a state is a union territory. Therefore, in this method, you will modify the data provider so that it provides this information to the Tax engine.

1. Find the system name of the Union Territory of State master.
	1. Go to **Organization administration** > **Global address book** > **Addresses** > **Address setup**. 
	2. Right-click the **Union territory** column, and then click **Form information** > **Form Name: LogisticsAddressSetup**. For this example, notice that the system name for the column is **LogisticsAddressState.UnionTerritory_IN**.

![GTE extension of union territory](media/gte-extension-union-territory-form-info.png)

2. Add a tax engine model field for intrastate transactions in a union territory. 
	1. In the AOT, open **Classes** > **TaxableDocRowDataProviderExtensionLine**, add a ```const str``` for intrastate transactions in a union territory.
	
```
public class TaxableDocRowDataProviderExtensionLine extends TaxableDocumentRowDataProviderExtension
{
    public static const str IsIntraStateInUnionTerritory = 'IntraStateInUnionTerritory';
```

3. Implement logic to determine if a transaction is an intrastate transaction in a union territory. For example, add a new method for the **TaxableDocRowDataProviderExtensionLine** class, and implement the determination logic in the method.
	
```
private NoYes IsIntraStateWithUnionTerritory(TaxableDocumentLineObject _lineObj)
{
    boolean                     isIntraStateWithUnionTerritory = NoYes::No;
    LogisticsPostalAddress      partyAddress;
    LogisticsPostalAddress      taxAddress;
    LogisticsAddressState       partyState;
    SalesPurchJournalLine       documentLineMap;
    TaxModelTaxable_IN          taxModelTaxable;
    documentLineMap = SalesPurchJournalLine::findRecId(_lineObj.getTransactionLineTableId(), _lineObj.getTransactionLineRecordId());
    taxModelTaxable = TaxModelDocLineFactory_IN::newTaxModelDocLine(documentLineMap);
    partyAddress = taxModelTaxable.getPartyLogisticsPostalAddress();
    taxAddress = taxModelTaxable.getTaxLogisticsPostalAddressTable();
    if (partyAddress && taxAddress
        && partyAddress.CountryRegionId == taxAddress.CountryRegionId
        && partyAddress.State != ''
        && taxAddress.State != ''
        && partyAddress.State == taxAddress.State)
    {
        partyState = LogisticsAddressState::find(partyAddress.CountryRegionId, partyAddress.State);
        isIntraStateWithUnionTerritory = partyState.UnionTerritory_IN;
    }
    return  isIntraStateWithUnionTerritory;
}
```
4. Pass the flag to GTE in TaxableDocRowDataProviderExtensionLine.fillInExtensionFields()

```
_lineObj.setFieldValue(IsIntraStateInUnionTerritory, this.IsIntraStateWithUnionTerritory(_lineObj));
```

5. Add the new field in TaxableDocumentRowDataProviderLine. initValidFields ()

```
validFields.add(TaxableDocRowDataProviderExtensionLine::IsIntraStateInUnionTerritory, Types::Enum, enumNum(NoYes));
```

6. Complete the data binding in the Designer.
	1. Navigate to the **Taxable Document (India Contoso)** configuration, and then click **Designer**.

	![Tax configuration designer](media/gte-extension-tax-configuration-designer.png)
	
	2. Click **Map model to datasource**
	3. You will find there are lots of data mapping per each taxable document and reference model, like purchase order, sales order, etc. You need to do your data mapping per your business requirement. For example:
		1. Select a sales order document line.
		2. Click **Designer**.

		![Data mapping](media/gte-extension-data-mapping.png)

	4. After completing steps 1-5, you should be able to find the field **IntraStateInUnionTerritory** in the data source under **Sales order** > **Header** > **Lines**. You can bind this field to the **IntraStateInUnionTerritory:Enumeration value** in the Taxable Document.

	![Data binding](media/gte-extension-data-binding.png)

	5. Save the configuration, and close the designer.
	6. In the **Configurations** workspace, click **Change status** > **Complete**.

	![Chang configuration status](media/gte-change-configuration-status.png)

	7. Enter a description such as **UTGST**, and then click **OK**.
	8. If there are any errors, open the designer, click **Validate**, and fix the errors.

#### Method 2: Data mapping using the ER model mapping designer
Before you use this method, be sure you are familiar with ER and the table relation, class, method, etc. for purchase orders. 
1. Open the model mapping design of purchase order, add table records **PurchLine** as a root data source
![Purchline extension](media/gte-extension-purchline.png)
2. Add Data model\Enumeration **YesNo Global** and Dynamics 365 for Operations\Enumeration **NoYes**
![Add enumerations](media/gte-extension-add-enumerations.png)
3. Add a calculated field **$PurchLine** in **purchase order** to build the connection between existing taxable document **purchase order** and the table records **PurchLine**, click **Edit formula**.
![Edit formula](media/gte-extension-edit-formula.png)
4. Input formula which describe the relation between **PurchLine** and **purchase order**
![Add formula](media/gte-extension-add-formula.png)
5. Click **Save**, and close the page
6. Add calculated field **\$IsIntraStateInUnionTerritory** in **$PurchLine**, the formula is 
```
AND('purchase order'.'$PurchLine'.'initTaxModelDocLine_IN()'.getPartyLogisticsPostalAddress.'>Relations'.State.StateId = 'purchase order'.'$PurchLine'.'initTaxModelDocLine_IN()'.getTaxLogisticsPostalAddress.'>Relations'.State.StateId, 'purchase order'.'$PurchLine'.'initTaxModelDocLine_IN()'.getPartyLogisticsPostalAddress.'>Relations'.State.UnionTerritory_IN = NoYesAx.Yes, 'purchase order'.'$PurchLine'.'initTaxModelDocLine_IN()'.getTaxLogisticsPostalAddress.'>Relations'.State.UnionTerritory_IN = NoYesAx.Yes)
```
7. In the **Model mapping designer** complete the mapping:
	1. In the **DATA SOURCES** tree, select **$IntraStateInUnionTerritory**.
	2. In the **DATA MODEL**, select **IntraStateInUnionTerritory**.
	3. Click **Edit**.
![Edit data mapping](media/gte-extension-data-binding2.png)
	4. Input the following formula to convert the Boolean value to the enumeration value which is used by the extended taxable document field IntraStateInUnionTerritory.
	```
	CASE('purchase order'.'$PurchLine'.'$IsIntraStateInUnionTerritory', true, NoYesModel.Yes, false, NoYesModel.No)
	```
	5. Click Save and close the page.
8. Save the configuration, and close the designer.
9. In the **Configurations** workspace, click **Change status** > **Complete**.

	![Chang configuration status](media/gte-change-configuration-status.png)

10. Enter a description such as **UTGST**, and then click **OK**.
11. If there are any errors, open the designer, click **Validate**, and fix the errors.

### Task 4: Change the data model of Tax (India GST Contoso)

1. Go to the **Tax (India GST Contoso)** configuration that you created in [Scenario 1: Task 1.2](#task-12-create-a-new-tax-document-that-is-derived-from-tax-india-gst), and then click **Designer**.
2. Click **Tax document**, and then select **Taxable Document (India Contoso)** as the data model and **1** as the data model version.

	![Tax document](media/gte-tax-document-designer.png)

3. Click **Save** to save the configuration.

### Task 5: Change the applicability of SGST

1. Go to the **Tax (India GST Contoso)** configuration, select the version that has a status of **Draft**, and then click **Designer**.
2. Go to **Tax document** > **Header** > **Lines** > **GST** > **SGST**, and then click the **Lookup** tab.
3. Click **Columns**.
4. Select **IntraStateInUnionTerritory** as the lookup column, and then click the right arrow button.
5. For the **IntraStateInUnionTerritory** column, select **No**.
6. Click **Save** to save the configuration.

### Task 6: Configure the UTGST tax component

#### Task 6.1: Add the UTGST tax component

1. Navigate to **Tax document** > **Header** > **Lines** > **GST**, click **Add**, and then select **Tax component**.
2. Enter a name and description for the UTGST tax component, and then click **OK**.

#### Task 6.2: Configure tax measures for the UTGST tax component

1. Expand the tax document tree, and click the UTGST tax component to create a measure for.
2. Click **Add**, and then select **Tax measure**.
3. All the logic (properties, lookups, formulas, postings, accounting, and so on) except applicability of UTGST is the same as it is for SGST. Therefore, add all the tax measures that SGST uses by selecting the existing measures in the list.

	![Listed measures](media/gte-utgst-list.png)

#### Task 6.3 Configure rate/percentage lookups

1. Expand the **UTGST** tax component node.
2. Select the measure of the **Rate/Percentage** type to create a rate/percentage lookup.
3. Click **Columns** to see a list of the attributes that are relevant to the tax rate/percentage value.
4. Select the same attributes that SGST uses.

	> [!Note]
	> Don’t click **Add**. Values that you enter here have no effect on the actual rate table. That table should be completed at **Tax** > **Tax configuration** > **Tax setup**.

5. Save the tax document.

#### Task 6.4: Configure properties

1. Navigate to **Tax document** > **Header** > **Lines** > **GST** > **UTGST**, and then click the **Properties** tab.
2. Click **Edit** (the pencil symbol) next to **Condition**.
3. Enter the same condition that SGST uses.

	![SGST condition](media/gte-sgst-condition.png)

4. Save the tax document.

#### Task 6.5: Configure tax applicability lookups

1. Navigate to **Tax document** > **Header** > **Lines** > **GST** > **UTGST**, and then click the **Lookup** tab.
2. Click **Columns**.
3. Select **Import Order** and **IntraStateInUnionTerritory** as lookup columns.
4. Select **Configuration** as the source type, and select **No** for the **Import Order** column and **Yes** for the **IntraStateInUnionTerritory** column.	
5. Save the tax document.

#### Task 6.6 Configure formulas

Formulas can be configured at either the group node level (line, tax component, or tax type) or the measure node level. However, we recommend that you always configure tax calculation formulas at the group node level. Tax amount distribution formulas can be configured at either the group node level or the measure node level.

1. Navigate to **Tax document** > **Header** > **Lines** > **GST** > **UTGST**, and then click the **Formula** tab.
2. Click **Add Tax formula**.
3. On the **Details** FastTab, select **Formula** as the category, and then click **Edit** to enter the formula and condition.
4. Repeat steps 2 through 3 until the UTGST tax component has all the same formulas as SGST.
5. Save the tax document.

### Task 6.7 Configure a posting profile

Only nodes of the **Tax Component** type support a posting profile definition.

1. Navigate to **Tax document** > **Header** > **Lines** > **GST** > **UTGST**, and then click the **Postings** tab.
2. Click **Add Posting Profile** to create a new posting profile definition.
3. On the **Details** FastTab, enter the accounting treatment for the various tax measures that you defined in the previous task, and provide the names of the Debit and Credit accounting subledgers.
4. Click **Edit** to enter a condition.
5. Optional: Enter a description for the posting profile.
6. Repeat steps 2 through 5 until the UTGST tax component has all the same posting profiles as SGST.
7. Save the tax document.

#### Task 6.8 Configure accounting lookups

Only nodes of the **Tax Type** and **Tax Component** types support an accounting lookup definition.

1. Navigate to **Tax document** > **Header** > **Lines** > **GST** > **UTGST**, and then click the **Accounting** tab.
2. Click **Columns** to see a list of the attributes that can be used to determine the main accounts that will be used for accounting taxes.
3. Select the same attributes that SGST uses.

	> [!NOTE]
	> Don’t click **Add**. Values that you enter have no effect on the actual tax main accounts decision table. That table should be completed at **Tax** > **Tax configuration** > **Tax setup**.

4. Save the tax document.

#### Task 6.9 Configure credit pools

Only nodes of the **Tax Component** type support a credit pool definition.

1. Expand the **UTGST** tax component node, and then click the **Credit Pool** tab.
2. Click **Columns** to see a list of the attributes that are relevant to the tax settlement of this component. Typically, the selected column is the appropriate tax registration number, like **GST Registration Number**.
3. Select the same attributes that SGST uses.

	> [!NOTE]
	> Don’t click **Add**. Values that you enter here have no effect on the actual rate table. That table should be completed at **Tax** > **Tax configuration** > **Tax setup**.

4. Save the tax document.

### Task 7: Modify the formulas of lines so that they reflect UTGST

1. Navigate to **Tax document** > **Header** > **Lines**, and then click the **Formulas** tab.
2. Change any formulas that contain the **Base Amount**, **Line tax amount**, and **Tax amount included in price** measures, so that the formulas reflect UTGST.

	For example, change the **Tax amount inclusive** formula as shown here.
	![Tax amount inclusive formula](media/gte-tax-amount-inclusive.png)
	
3. Save the tax document.
4. Close the designer.

### Task 8: Complete the tax document configuration

1. Save the configuration, and close the designer.
2. In the **Configurations** workspace, click **Change status**, and then select **Complete**.
3. Enter a description such as **UTGST**, and then click **OK**.
4. If there are any errors, open the designer, click **Validate**, and fix the errors.
5. After the status is updated to **Complete**, the configuration is ready for deployment.

### Task 9: Import the configuration and deploy it to a specific company
1.	Go to **Tax** > **Setup** > **Tax configuration** > **Tax setup**.
2.	Create a new record and define Tax setup.

![New tax setup](media/gte-extension-new-tax-setup.png)

3.	Click **Configurations**.

![Configuration](media/gte-extension-new-configuration.png)

4.	Click on **Tax configuration** tab, switch to **Available configurations** and click **New** to create a tax configuration.
	> [!NOTE]
	> The configuration that is added to tax gets listed on the **Available configuration** tab
	
![New configuration](media/gte-extension-new-configuration2.png)

5.	Select the required configuration, Ex: **Tax (India GST)** and Click **Save**.

![Select configuration](media/gte-extension-select-configuration.png)

6.	In the elipses menu, click **Synchronize**.

![Synchronize configuration](media/gte-extension-synchronize-configuration.png)

7. In the elipses menu, click **Activate**.

![Activate configuration](media/gte-extension-activate-configuration.png)

![Active configuration](media/gte-extension-active-configuration.png)

8.	Click **Close**.
9.	Click the **Companies** FastTab.
10.	Click **New**(1) and then select **INMF** in the **Companies** field (2).

![Select company](media/gte-extension-deploy-to-company.png)

11.	Click **Save**.
12.	Click **Activate** to activate the configuration for the company.

![Activate configuration for the company](media/gte-extension-activate-configuration-to-company.png)

![Active configuration for the company](media/gte-extension-activate-configuration-to-company2.png)

13.	Click **Setup** to set up data for the new version.

![Set up data for new version](media/gte-extension-tax-setup.png)

## Scenario 2: Using a Reference Model

Per the Microsoft-provided configuration, the tax rate for the BCD is determined by Preferential Party/Import Order/Import Custom Tariff Code/Export Order/Export Custom Tariff Code. We will use this scenario to explain how to use a reference model to support the following scenario:

- Apply a different tax rate for the BCD on the import order of goods from difference countries/regions.

### Task 1: Create extension configuration

Complete the steps in [Scenario 1: Task 1](#task-1-create-extension-configurations).

### Task 2: Add Reference model for Country/Region of Origin

1. Find and select the **Taxable Document (India Contoso)** configuration, and then click **Designer**.
2. Click the elipses button, then click **Reference model** to change the view to Reference model, so you can view all the available reference models.
3. Click **New** to add a new reference model.
    -	**Name:** Country of Origin
    -	**Node type:** Model root
4. Click **Add**.
5. Highlight **Country of Origin**, click **New** to add new reference model.
    -   **Name:** Countries of Origin
    -   **Node type:** Child of an active node
    -   **Item type:** Record list
6. Click **Add**.
7. Highlight **Countries of Origin**, click **New** to add new reference model.
    -   **Name:** Country of Origin
    -   **Node type:** Child of an active node
    -   **Item type:** String
8. Click **Add**.
9. Highlight **Country of Origin**, click **Natural key**.
10. Choose **Country of Origin\\Countries of Origin\\Country of Origin** as the **Natural key**.
11. If there are any errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

### Task 3: Complete data mapping for the reference model
1. In the designer of **Taxable Document (India Contoso)**, and then click **Map model to datasource**.
2. Add a new model mapping for the reference model Country of Origin
![Add model mapping](media/gte-extension-map-reference-model.png)
3. Open the designer of the model mapping
![Model mapping designer](media/gte-extension-designer-mapping-reference-model.png)
4. Add table records **LogisticsAddressCountryRegion** as a root **DATA SOURCES**
![Add table records](media/gte-extension-add-table-records.png)
5.Bind the table
![Bind table](media/gte-extension-bind-table.png)
6.Bind the field
![Bind field](media/gte-extension-bind-field.png)
7.Click **Save** and close the page

### Task 4: Link the reference model to field in taxable document

1. Click the elipses button, then click **Taxable document** to change the view to Taxable document.
2. Navigate to **Taxable document** > **Header** > **Lines** > **GST** > **Country/Region of Origin**.
3. On the **Node** FastTab, click **Select reference model**. 
4. Choose **Country of Origin** for the reference model.
5. Click **OK**.
6. Save the configuration and close the designer.
7. In the **Configurations** workspace, click **Change status**, and then select **Complete**.
8. Enter a description such as **Add reference model for Country of Origin**, and then click **OK**.
9. If there are any errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

### Task 5: Change the lookup of the BCD tax rate

1.  Go to the **Tax (India GST Contoso)** configuration, and then click **Designer**.
2.  Change the data model of **Tax (India GST Contoso)** to the updated version of the extended taxable document. To do this, complete the steps in [Scenario 1: Task 3](#task-3-do-data-mapping-for-the-extended-taxable-document).
3.  Go to **Tax document** > **Header** > **Lines** > **Custom Duty** > **BCD** > **Rate**, and then click the **Lookup** tab.
4.  Click **Columns**.
5.  Select **Country/Region of Origin** as the lookup column, and then click the right arrow button.
6.  Click **Save**.

### Task 6: Complete the tax document configuration
Complete the steps in [Scenario 1: Task 8](task-8-complete-the-tax-document-configuration).

### Task 7: Import the configuration and deploy it to a specific Company
Complete the steps in [Scenario 1: Task 9](#task-9-import-the-configuration-and-deploy-it-to-a-specific-company).
