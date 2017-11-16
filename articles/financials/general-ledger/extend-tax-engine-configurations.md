---
# required metadata

title: Tax engine
description: This topic provides information about extending tax engine configurations.
author: RichardLuan
manager: AnnBe
ms.date: 10/02/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: riluan
#ms.search.validFrom:
#ms.dyn365.ops.version: 

---

# Extending tax engine configurations

[!include[banner](../includes/banner.md)]

The new Tax Engine (GTE) is an essential part of the configurable business application experience in Microsoft Dynamics 365 for Operations. GTE is highly customizable and lets business users, functional consultants, or power users configure tax rules that determine tax applicability, calculation, posting, and settlement, based on legal and business requirements.

In this document, you will learn how to extend the configuration of Goods and Services Tax (GST) to cover your future business extension scenarios. Following two scenarios are used to explain the detailed extension process.

Extend the GTE configuration for UTGST

Apply tax rate of BCD for import order of goods from different countries/regions (Usage of Reference Model)

## Prerequisites


-	Make sure that Microsoft Dynamics 365 for Operations version 1611 has been deployed, and that the GST hotfix is installed. 
-	Switch to the **INMF** company context.

## Copy the GST configuration


1. On the computer that is running Dynamics 365 for Operations, create a folder for the GST configuration, such as **C:\\India GST Configurations**. 

2. Save the GST configuration in the folder that you just created.

## Activate the tax configuration


1. Go to **Organization administration** \> **Electronic reporting**.

	![](media/24cc6ec2799c285acb79f9e5228a4a0b.png)

2. Click **Electronic reporting parameters**.

	![](media/4172aafcc859e3204d6487783345ea3e.png)

3. On the **Attachments** tab, set the **Configurations** field to **File**.

	![](media/a16f544dd975c14d108879de86bf52f6.png)

4. Close the page.

5. Click **Enable India GST**.

	![](media/7f483a5559bd0ce555d664762af39c64.png)

6. Set the **Enable GST** option to **Yes**, and then click **OK** in the message box.

	![](media/3d9bf1e01410a555e27e05d69184a72b.png)

7. In the **Work directory** field, specify the folder where you saved the India GST configuration.

	![](media/f99474d8d09dd8a36fd7f271ccf833d3.png)

8. Click **OK**.

9. Click **Import GST configurations** to import the configuration.

	![](media/bb051139a01fac1cbd4adb82871eb9f0.png)

10. Click **Import**.

	![](media/d8ab60826d1e723aac53aa530fee1a07.png)

11. Click **Yes**.

	![](media/bccddac3a52bf7bec2e2a8be4bab9032.png)

12. Click **Solutions**.

	![](media/d7df57cff0cf106ec6eb14fc12fdfcef.png)

13. Create a new solution, and enter the required information.

	![](media/85eba6431cbd76f76f09c6f092f1723e.png)

14. Click **Set active** to activate the new solution.

	![](media/f51054065e9de4bda82ba0c47e557f91.png)

## Scenario 1: Extend the GTE configuration for UTGST


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

-	Supply of goods and services across states or union territories (interstate/inter-UT): Integrated GST (IGST)

The order of utilization for Input Tax Credit of UTGST is the same as it is for Input Tax Credit of SGST. Therefore, Input Tax Credit of SGST or UTGST is first set off against SGST or UTGST, respectively. Output Tax liabilities and any balance can be set off against IGST Output Tax liabilities.

Following is the summary of the changes of the extension:

1.  Extend the taxable document so that it includes the     **IntraStateInUnionTerritory** flag.

2.  Change the applicability of State GST (SGST).

3.  Add and configure UTGST.

4.  Import the extended configuration, and deploy it to a specific company.

5.  Change the **TaxableDocRowDataProviderExtensionLine** class in the Application Object Tree (AOT) of Microsoft Dynamics AX 2012 so that it sends the **IntraStateInUnionTerritory** flag to GTE.

### Task 1: Create extension configurations


#### Task 1.1: Create a new taxable document that is derived from Taxable Document (India)

1. Open the **Localization configurations** workspace.

2. Click **Tax configurations**.

3. Navigate to the **Taxable Document (India)** configuration, and then click **Create configuration**.

	![](media/361306c4ceb367a3513a170a9db66e31.png)

4. Select the **Derive from Taxable document model** option, and then enter a name and description for the derived taxable document.

	![](media/458888b4088259f03a17aa20f4acf7a9.png)

#### Task 1.2: Create a new tax document that is derived from Tax (India GST)

Navigate to the **Tax (India GST)** configuration, and then click **Create configuration**.

![](media/59e381657dde6c6c406190ccc5fbcbea.png)

Select the **Derive from Tax configuration** option, and then enter a name and description for the derived tax document.

![](media/48d518dbba407be1b90e7db0ca13af36.png)

### Task 2: Add the IntraStateInUnionTerritory flag to Taxable Document (India Contoso)


Navigate to the **Taxable Document (India Contoso)** configuration, and then click **Designer**.

![](media/4f4b968b23228fcc6e60c8cdadd4f942.png)

Navigate to **Taxable document** \> **Header** \> **Lines**, and then click **New** to create a new node.

Enter a name for the node, and select the item type:

**Name:** IntraStateInUnionTerritory

**Item type:** Enum

![](media/4dbae44d81445d74cf3478a7b978c9f3.png)

Click **Add**.

Click **Switch item reference**.

![](media/990cd87a21bc3c3f6424a1d68b484f66.png)

Select **NoYes**, and then click **OK**.

Save the configuration, and close the designer.

In the **Configurations** workspace, click **Change status**, and then select **Complete**.

![](media/e6938db9fe6cd010cab8093177fa01f9.png)

Enter a description such as **UTGST**, and then click **OK**.

If there are any errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

### Task 3: Change the data model of Tax (India GST Contoso)


Navigate to the **Tax (India GST Contoso)** configuration, and then click **Designer**.

![](media/c3fcf88a39b927857071c8e7deaf78e2.png)

Click **Tax document**, and then select **Taxable Document (India Contoso)** as the data model and **1** as the data model version.

![](media/f48cdba98904d5eca6e9456caa29a5fd.png)

Click **Save** to save the configuration.

### Task 4: Change the applicability of SGST


Navigate to the **Tax (India GST Contoso)** configuration, select the version that has a status of **Draft**, and then click **Designer**.

![](media/169e717e970e6247a6f6c04577855162.png)

Navigate to **Tax document** \> **Header** \> **Lines** \> **GST** \> **SGST**, and then click the **Lookup** tab.

Click **Columns**.

Select **IntraStateInUnionTerritory** as the lookup column, and then click the right arrow button.

![](media/5c066d2fd6d41e91dd80c36bcff59de9.png)

For the **IntraStateInUnionTerritory** column, select **No**.

![](media/d76a95b661005ae734b8de4924ae7c94.png)

Click **Save** to save the configuration.

### Task 5: Configure the UTGST tax component


#### Task 5.1: Add the UTGST tax component

Navigate to **Tax document** \> **Header** \> **Lines** \> **GST**, click **Add**, and then select **Tax component**.

![](media/385ad35f9f554728e9f144fa1af53ef2.png)

Enter a name and description for the UTGST tax component, and then click **OK**.

#### Task 5.2: Configure tax measures for the UTGST tax component

Expand the tax document tree, and click the UTGST tax component to create a measure for.

Click **Add**, and then select **Tax measure**.

![](media/331577a480dccf48b8734e8cb82745d1.png)

All the logic (properties, lookups, formulas, postings, accounting, and so on) except applicability of UTGST is the same as it is for SGST. Therefore, add all the tax measures that SGST uses by selecting the existing measures in the list.

![](media/fbe4c4aae43db743817c6ac337690944.png)

#### Task 5.3 Configure rate/percentage lookups

Expand the **UTGST** tax component node.

Select the measure of the **Rate/Percentage** type to create a rate/percentage lookup.

Click **Columns** to see a list of the attributes that are relevant to the tax rate/percentage value.

Select the same attributes that SGST uses.

> [!Note]
> Don’t click **Add**. Values that you enter here have no effect on the actual rate table. That table should be completed at **Tax** \> **Tax configuration** \> **Tax setup**.

Save the tax document.

#### Task 5.4: Configure properties

Navigate to **Tax document** \> **Header** \> **Lines** \> **GST** \> **UTGST**, and then click the **Properties** tab.

Click **Edit** (the pencil symbol) next to **Condition**.

Enter the same condition that SGST uses.

![](media/da55b376d88489eec725d5c83d7e702e.png)

Save the tax document.

#### Task 5.5: Configure tax applicability lookups

Navigate to **Tax document** \> **Header** \> **Lines** \> **GST** \> **UTGST**, and then click the **Lookup** tab.

Click **Columns**.

Select **Import Order** and **IntraStateInUnionTerritory** as lookup columns.

Select **Configuration** as the source type, and select **No** for the **Import Order** column and **Yes** for the **IntraStateInUnionTerritory** column.

![](media/e6a2d52f43c9b19ee27451d209e26daa.png)

Save the tax document.

#### Task 5.6 Configure formulas

Formulas can be configured at either the group node level (line, tax component, or tax type) or the measure node level. However, we recommend that you always configure tax calculation formulas at the group node level. Tax amount distribution formulas can be configured at either the group node level or the measure node level.

Navigate to **Tax document** \> **Header** \> **Lines** \> **GST** \> **UTGST**, and then click the **Formula** tab.

Click **Add Tax formula**.

On the **Details** FastTab, select **Formula** as the category, and then click **Edit** (the pencil symbol) to enter the formula and condition.

Repeat steps 2 through 3 until the UTGST tax component has all the same formulas as SGST.

Save the tax document.

### Task 5.7 Configure a posting profile

Only nodes of the **Tax Component** type support a posting profile definition.

Navigate to **Tax document** \> **Header** \> **Lines** \> **GST** \> **UTGST**, and then click the **Postings** tab.

Click **Add Posting Profile** to create a new posting profile definition.

On the **Details** FastTab, enter the accounting treatment for the various tax measures that you defined in the previous task, and provide the names of the Debit and Credit accounting subledgers.

Click **Edit** (the pencil symbol) to enter a condition.

Optional: Enter a description for the posting profile.

Repeat steps 2 through 5 until the UTGST tax component has all the same posting profiles as SGST.

Save the tax document.

#### Task 5.8 Configure accounting lookups

Only nodes of the **Tax Type** and **Tax Component** types support an accounting lookup definition.

Navigate to **Tax document** \> **Header** \> **Lines** \> **GST** \> **UTGST**, and then click the **Accounting** tab.

Click **Columns** to see a list of the attributes that can be used to determine the main accounts that will be used for accounting taxes.

Select the same attributes that SGST uses.

> [!NOTE]
> Don’t click **Add**. Values that you enter have no effect on the actual tax main accounts decision table. That table should be completed at **Tax** \> **Tax configuration** \> **Tax setup**.

Save the tax document.

#### Task 5.9 Configure credit pools

Only nodes of the **Tax Component** type support a credit pool definition.

Expand the **UTGST** tax component node, and then click the **Credit Pool** tab.

Click **Columns** to see a list of the attributes that are relevant to the tax settlement of this component. Typically, the selected column is the appropriate tax registration number, like **GST Registration Number**.

Select the same attributes that SGST uses.

> [!NOTE]
> Don’t click **Add**. Values that you enter here have no effect on the actual rate table. That table should be completed at **Tax** \> **Tax configuration** \> **Tax setup**.

Save the tax document.

### Task 6: Modify the formulas of lines so that they reflect UTGST


Navigate to **Tax document** \> **Header** \> **Lines**, and then click the **Formulas** tab.

Change any formulas that contain the **Base Amount**, **Line tax amount**, and **Tax amount included in price** measures, so that the formulas reflect UTGST.

>   For example, change the **Tax amount Inclusive** formula as shown here.

![](media/a097874b0d1404abe674d50470e89e73.png)

Save the tax document.

Close the designer.

### Task 7: Complete the tax document configuration


Save the configuration, and close the designer.

In the **Configurations** workspace, click **Change status**, and then select **Complete**.

![](media/e6938db9fe6cd010cab8093177fa01f9.png)

Enter a description such as **UTGST**, and then click **OK**.

If there are any errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

### Task 8: Download the tax document configurations


In the **Versions** grid, select the **Tax (India GST Contoso)** configuration.

Click **Change status**, and then select **Share**.

![](media/f5ab08e0945f4bbe88896979ad394955.png)

Click **Yes**.

![](media/bb6db0ffabaacbae2afb1f76708377ea.png)

Repeat steps 1 through step 3 for the **Taxable Document (India Contoso)** configuration.

> [!NOTE]
> The configuration will be saved in the C:\\India GST Configurations folder that you created earlier. Currently, all configurations are in that folder. You must then copy the folder to the Microsoft Dynamics AX environment where the configuration must be applied.

### Task 9: Import the configuration and deploy it to a specific company


Save all the configuration files in one folder that Microsoft Dynamics AX Application Object Server (AOS) can access.

![](media/04f998ef1ccf94676526b6f593464ba3.png)

Go to **General ledger** \> **Setup** \> **Sales tax** \> **India** \> **Load configurations**.

Set the directory to the folder where you saved the configuration files.

![](media/854b24262d911d33fb603ad6fccb33d1.png)

Click **OK**.

![](media/d760b4f226057fa4b74207d6c388ce55.png)

Click **Close**.

Go to **General ledger** \> **Setup** \> **Sales tax** \> **India** \> **Tax setup**.

Select the current working tax setup.

Click **Configurations**.

![](media/a10fb9220447f7ba936547ad4e167c32.png)

Click the **Tax configuration** tab, and then, under **Available configurations**, click **New** to create a tax configuration.

> [!NOTE]
> Any tax configurations that you add are listed in the **Available configurations** grid.

![](media/6917f0980f7338174f88bff7b051497b.png)

Select the required configuration (for example, **Tax (India GST Contoso**) and version (for example, **1**), and then click **Synchronize**.

![](media/a96a042c4bf72301a6df753352ea460e.png)

Click **Activate**.

![](media/d5382114a914e221d892090022bc5ea1.png)

![](media/6905ba3ea1f2285f7e618a6cce675c36.png)

Click **Setup** to set up data for the new version.

![](media/b37f77a3cda491cdf0fc60b9a27313ee.png)

![](media/1b70500c6f1a29bf9c1ec740f7513e10.png)

### Task 10: Modify the data provider in Microsoft Dynamics AX

Before you start this scenario, be sure to read the **Tax Engine Integration** document where you can find all the details about how GTE is integrated with Microsoft Dynamics AX. GTE must determine whether a state is a union territory. Therefore, in this scenario, you will modify the data provider in Microsoft Dynamics AX 2012 R3 so that it provides this information to GTE.

#### Task 10.1: Check the system name of the Union Territory of State master

Go to **Organization administration** \> **Addresses** \> **Address setup**. Although a check box indicates whether a state is a union territory, the value isn’t provided to GTE. Right-click the **Union territory** column, and then click **Personalize**. You will see that the system name for the column is **LogisticsAddressState\_IN.UnionTerritory**.

![](media/f7c464ac22eadb35058072914e5ba91d.png)

#### Task 10.2: Add a tax engine model field for intrastate transactions in a union territory

In the AOT, open **Classes** \> **TaxableDocRowDataProviderExtensionLine**. In **classDeclaration**, add a new macro for intrastate transactions in a union
territory.

\#define.IsIntraStateInUnionTerritory('IntraStateInUnionTerritory')

### Task 10.3: Implement logic to determine whether a transaction is an intrastate transaction in a union territory

Add a new method for the **TaxableDocRowDataProviderExtensionLine** class, and implement the determination logic in the method.

/// \<summary\>  
/// To determine if it is the inter state transaction within union territory.  
/// \</summary\>  
/// \<returns\>  
/// True if it is not inter state transaction within union territory; otherwise,
false.  
/// \</returns\>  
private NoYes IsIntraStateWithUnionTerritory(TaxableDocumentLineObject
\_lineObj)  
{  
boolean isIntraStateWithUnionTerritory = NoYes::No;  
LogisticsPostalAddress partyAddress;  
LogisticsPostalAddress taxAddress;  
LogisticsAddressState\_IN partyState\_IN;  
SalesPurchJournalLine\_IN documentLineMap;  
TaxModelTaxable\_IN taxModelTaxable;  
documentLineMap =
SalesPurchJournalLine\_IN::findRecId(\_lineObj.getTransactionLineTableId(),
\_lineObj.getTransactionLineRecordId());  
taxModelTaxable =
TaxModelDocLineFactory\_IN::newTaxModelDocLine(documentLineMap);  
partyAddress = taxModelTaxable.getPartyLogisticsPostalAddress();  
taxAddress = taxModelTaxable.getTaxLogisticsPostalAddressTable();  
if (partyAddress && taxAddress  
&& partyAddress.CountryRegionId == taxAddress.CountryRegionId  
&& partyAddress.State != ''  
&& taxAddress.State != ''  
&& partyAddress.State == taxAddress.State)  
{  
partyState\_IN =
LogisticsAddressState\_IN::findByLogisticsAddressState(LogisticsAddressState::find(partyAddress.CountryRegionId,
partyAddress.State).RecId);  
isIntraStateWithUnionTerritory = partyState\_IN.UnionTerritory;  
}  
return isIntraStateWithUnionTerritory;  
}

In case you are working on Dynamics AX 2009, since its table structures are
different from Dynamics AX 2012 R3, you should follow the same approach above to
write your code. Here we provide the corresponding implementation of
IsIntraStateWithUnionTerritory in Dynamics AX 2009 for your convenience.

/// \<summary\>

/// To determine if it is the inter state transaction within union territory.

/// \</summary\>

/// \<returns\>

/// True if it is not inter state transaction within union territory; otherwise,
false.

/// \</returns\>

private NoYes IsIntraStateWithUnionTerritory(TaxableDocumentLineObject
\_lineObj)

{

    boolean                     isIntraStateWithUnionTerritory = NoYes::No;

    Address                     partyAddress;

    Address                     taxAddress;

    AddressState                partyState\_IN;

    SalesPurchJournalLine\_IN    documentLineMap;

    TaxModelTaxable\_IN          taxModelTaxable;

    documentLineMap =
SalesPurchJournalLine\_IN::findRecId(\_lineObj.getTransactionLineTableId(),
\_lineObj.getTransactionLineRecordId());

    taxModelTaxable =
TaxModelDocLineFactory\_IN::newTaxModelDocLine(documentLineMap);

    partyAddress = taxModelTaxable.getPartyAddress();

    taxAddress = taxModelTaxable.getCompanyAddress();

    if (partyAddress && taxAddress

        && partyAddress.CountryRegionId == taxAddress.CountryRegionId

        && partyAddress.State != ''

        && taxAddress.State != ''

        && partyAddress.State == taxAddress.State)

    {

        partyState\_IN = AddressState::find(partyAddress.CountryRegionId,
partyAddress.State);

        isIntraStateWithUnionTerritory = partyState\_IN.UnionTerritory\_IN;

    }

    return  isIntraStateWithUnionTerritory;

}

### Task 10.4: Pass the flag to GTE in TaxableDocRowDataProviderExtensionLine.fillInExtensionFields()

\_lineObj.setFieldValue(\#IsIntraStateInUnionTerritory,
TaxEngineEnumToEREnumUtil::noYes(this.IsIntraStateWithUnionTerritory(\_lineObj)));

Scenario 2: Usage of Reference Model
====================================

Per the Microsoft provided configuration, the tax rate of BCD is determined by
Preferential Party/Import Order/Import Custom Tariff Code/Export Order/Export
Custom Tariff Code. We will use this scenario to explain how to use reference
model to support the scenario below:

Apply the different tax rate of BCD for import order of goods from difference
countries/regions.

Task 1: Create extension configuration
--------------------------------------

Do Scenario 1-\>Task 1.

Task 2: Add Reference model for Country/Region of Origin
--------------------------------------------------------

1.  Navigate to the **Taxable Document (India Contoso)** configuration, and then
    click **Designer**.

![](media/4f4b968b23228fcc6e60c8cdadd4f942.png)

1.  Click the **three dots** button, then click **Reference model** to change
    the view to Reference model, so you can view all the available reference
    models.

    ![](media/123185bb08446e4b98283003e4115ebd.png)

2.  Click **New** to add a new reference model.

    **Name:** Country of Origin

    **Node type:** Model root

![](media/7d36ec1c370b69d7d7e9d40f7a4e34be.png)

1.  Click **Add**.

2.  Highlight **Country of Origin**, click **New** to add new reference model.

    -   **Name:** Countries of Origin

    -   **Node type:** Child of an active node

    -   **Item type:** Record list

![](media/f28397d3358acb669f1694a3823389fa.png)

1.  Click **Add**.

2.  Highlight **Countries of Origin**, click **New** to add new reference model.

    -   **Name:** Country of Origin

    -   **Node type:** Child of an active node

    -   **Item type:** String

        ![](media/c16b0a4c1987f51baef302d6d5fe47d8.png)

3.  Click **Add**.

4.  Highlight **Country of Origin**, click **Natural key**.

![](media/091afd9b2ee1ca4f4f2695f53dd4775c.png)

1.  Choose **Country of Origin\\Countries of Origin\\Country of Origin** as the
    **Natural key**.

    ![](media/535f2d380d45557c6ef2b5a34d9cd6b0.png)

2.  If there are any errors, open the designer, click **Validate**, and fix the
    errors.

After the status is updated to **Complete**, the configuration is ready for
deployment.

Task 3: Link the reference model to field in taxable document
-------------------------------------------------------------

1.  Click the **three dots** button, then click **Taxable document** to change
    the view to Taxable document.

    ![](media/e73e5e4d125e414a3922d3b8dddef00f.png)

2.  Navigate to **Taxable document** \> **Header** \> **Lines** \> **GST** \>
    **Country/Region of Origin**, and then click **Select reference model**,
    choose **Country of Origin**.

3.  Click **OK** button.

![](media/baac5f34304f728a09e5641222721cab.png)

1.  Save the configuration, and close the designer.

2.  In the **Configurations** workspace, click **Change status**, and then
    select **Complete**.

![](media/e6938db9fe6cd010cab8093177fa01f9.png)

1.  Enter a description such as **Add reference model for Country of Origin**,
    and then click **OK**.

2.  If there are any errors, open the designer, click **Validate**, and fix the
    errors.

After the status is updated to **Complete**, the configuration is ready for
deployment.

Task 4: Change the lookup of BCD tax rate
-----------------------------------------

1.  Navigate to the **Tax (India GST Contoso)** configuration, and then click
    **Designer**.

![](media/c3fcf88a39b927857071c8e7deaf78e2.png)

1.  Change the data model of **Tax (India GST Contoso)** to the updated version
    of the extended taxable document follow the steps described in **Scenario
    1-\>Task 3**.

2.  Navigate to **Tax document** \> **Header** \> **Lines** \> **Custom Duty**
    \> **BCD** \> **Rate**, and then click the **Lookup** tab.

3.  Click **Columns**.

4.  Select **Country/Region of Origin** as the lookup column, and then click the
    right arrow button.

![](media/c9f578f35ad27e70ef0c050f8b989fa8.png)

1.  Click **Save** to save the configuration.

Task 5: Complete the tax document configuration
-----------------------------------------------

Please follow the same steps described in **Scenario 1-\>Task 7**.

Task 6: Download the tax document configurations
------------------------------------------------

Please follow the same steps described in **Scenario 1-\>Task 8**.

Task 7: Import the configuration and deploy it to a specific Company
--------------------------------------------------------------------

Please follow the same steps described in **Scenario 1-\>Task 9**.

Task 8: Add tax runtime reference model mapping in AOT 
-------------------------------------------------------

1.  Go to **Organization administration** \> **Addresses** \> **Address setup**
    \> **Country/Region**. Right-click the **Country/Region** column, and then
    click **Personalize**. You will see that the system name for the column is
    **LogisticsAddressCountryRegion.CountryRegionId**.

![](media/c7abea53c4278bb0e5a96ca9462565e2.png)

1.  Add Reference model name and Reference field name to
    **TaxRuntimeReferenceModel**

In the AOT, open **Macros** \> **TaxRuntimeReferenceModel**. Add two new macros
for Reference model name and Reference field name.

// Reference model name

\#define.GSTRegistrationNumbers('GST Registration Numbers')

\#define.CustomTariffCodes('Custom Tariff Codes')

\#define.ImportCustomTariffCodes('Import Custom Tariff Codes')

\#define.ExportCustomTariffCodes('Export Custom Tariff Codes')

\#define.TDSTCSRegistrationNumbers('TDS TCS Registration Numbers')

\#define.CustomDutyRegistrationNumbers('Custom Duty Registration Numbers')

\#define.TaxableDocumentTypes('Taxable Document Types')

\#define.TaxRegistrationProfiles('Tax Registration Profiles')

\#define.HSNCodes('HSN Codes')

\#define.SACodes('SA Codes')

\#define.CountriesOfRegion('Countries of Origin')

// Reference field name

\#define.GSTRegistrationNumber('GSTIN/GDI/UID')

\#define.CustomTariffCode('Custom Tariff Code')

\#define.TANNumber('TAN Number')

\#define.IECNumber('IEC Number')

\#define.TaxableDocumentName('Taxable Document Name')

\#define.PAN('PAN')

\#define.HSNCode('HSN Code')

\#define.SACode('SAC')

\#define.CountryOfRegion('Country of Origin')

1.  Add a TaxRuntimeReferenceModelMapping class for Country of Origin.

/// \<summary\>

/// Data model mapping for Country of Region reference data model.

/// \</summary\>

\#TaxRuntimeReferenceModel

[TaxRuntimeReferenceModelMappingAttribute(\#CountriesOfRegion)]

**class** TaxRuntimeRefModelMappingCountryOfRegion **extends**
TaxRuntimeReferenceModelMapping

{

}

/// \<summary\>

/// Gets table field name per reference field name.

/// \</summary\>

/// \<param name="\_referenceFieldName"\>

/// The reference field name

/// \</param\>

/// \<returns\>

/// The table field name

/// \</returns\>

**public** FieldName getTableFieldName(**str** \_referenceFieldName)

{

**switch**(\_referenceFieldName)

{

**case** \#CountryOfRegion:

**return fieldStr**(LogisticsAddressCountryRegion, CountryRegionId);

**default**:

**return** '';

}

}

/// \<summary\>

/// Gets table name for HSN Code.

/// \</summary\>

/// \<returns\>

/// The table name.

/// \</returns\>

**public** TableName getTableName()

{

**return tableStr**(LogisticsAddressCountryRegion);

}

1.  Restart AOS.

    ![](media/138847562184c990cffc0e9de7dfe397.png)

2.  Refresh elements by clicking **AOT** \> **Tools** \> **Caches** \>**Refresh
    elements**.

    ![](media/f792b57e643f93597343cfb8f6e736d4.png)

