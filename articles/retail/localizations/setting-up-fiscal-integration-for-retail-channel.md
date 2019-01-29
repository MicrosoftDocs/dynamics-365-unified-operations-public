---
# required metadata

title: Set up fiscal integration for Retail channel
description: This topic provides guidelines on setting up the fiscal integration functionality for Retail channel. 
author: josaw
manager: annbe
ms.date: 2/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: v-kikozl
ms.search.validFrom: 2018-11-1
ms.dyn365.ops.version: 8.1.1

---
# Set up fiscal integration for Retail channel

[!include [banner](../includes/banner.md)]

This topic provides guidelines on setting up the fiscal integration functionality for Retail channel. For more information about the fiscal integration, see [Overview of fiscal integration for Retail channel](fiscal-integration-for-retail-channel).

Setting up fiscal integration includes the following tasks.

- Configure fiscal connectors that represent fiscal devices or services used for fiscal registration purposes, such as fiscal printers.
- Configure document providers that generate fiscal documents to be registered in fiscal devices or services by fiscal connectors.
- Configure the fiscal registration process that defines a sequence of fiscal registration steps and fiscal connectors and fiscal document providers used on each step.
- Assign the fiscal registration process to POS functionality profiles.
- Assign connector technical profiles to hardware profiles.

## How to set up a fiscal registration process

Before using the fiscal integration functionality, the following settings should be configured.

1. Update retail parameters.

 	- On the **Retail shared parameters** page: 
		- Set the parameter **Enable fiscal integration** to **Yes** on **General** tab.
 		- Define the number sequences for the following references:
			- Fiscal technical profile number;
			- Fiscal connector group number;
			- Registration process number.
	- On the **Retail parameters** page, define the number sequence for the fiscal functional profile number.

	>[!NOTE]
	> Number sequences are optional. All fiscal integration entities may have numbers populated either from number sequences or manually.

2. Upload configurations of fiscal connectors and fiscal document providers.

	A fiscal document provider is responsible for the generation of fiscal documents representing retail transactions and events registered on POS in a format further used for the interaction with a fiscal device or service. For example, a fiscal document provider may generate a fiscal receipt representation in an XML format. A fiscal connector is responsible for the communication with a fiscal device or service. For example, a fiscal connector may send a fiscal receipt in an XML format created by a fiscal document provider to a fiscal printer. For more details about fiscal integration components, see [Fiscal registration process and fiscal integration sample for fiscal device](fiscal-integration-for-retail-channel#fiscal-registration-process-and-fiscal-integration-sample-for-fiscal-device).

	- On the **Fiscal connectors** page (**Retail > Channel setup > Fiscal integration > Fiscal connectors**), upload an XML configuration for each device or service that you plan to use for fiscal integration purposes. 
  
	By clicking **View**, you may view all functional and technical profiles related to the current fiscal connector.

	-  On the **Fiscal document providers** page (**Retail > Channel setup > Fiscal integration > Fiscal document providers**), upload an XML configuration for each device or service that you plan to use.
 
	By clicking **View**, you may view all functional profiles related to the current fiscal document provider.

	See [Fiscal integration samples in Retail SDK](fiscal-integration-for-retail-channel#fiscal-integration-samples-in-retail-sdk) for examples of configurations of fiscal connectors and fiscal document providers.

	>[!NOTE]
	> Data mapping is considered to be a part of a fiscal document provider. To set up different data mappings for the same connector (like state-specific regulations), you should create different fiscal document providers.

3. Create connector functional profiles and connector technical profiles.

	- Create a **Connector functional profile** in **Retail > Channel setup > Fiscal integration > Connector functional profiles** for each combination of a fiscal connector and a fiscal document provider related to this fiscal connector.
		- Select a connector name.
		- Select a document provider.

	Data mapping parameters can be changed in a connector functional profile. Click **Update** if you want to restore the default parameters defined in the fiscal document provider configuration.

	#### Examples 
        |  | Format | Example | 
        |--------|--------|--------|
        | VAT rates settings | value : VATrate | 1 : 2000, 2 : 1800 |
        | VAT codes mapping | VATcode : value | vat20 : 1, vat18 : 2 |
        | Tender types mapping | TenderType : value | Cash : 1, Card : 2 |
  
	>[!NOTE]
	> Connector functional profiles are company-specific. If you plan to use the same combination of a fiscal connector and a fiscal document provider in different companies, a connector functional profile should be created for each company.

	- Create a **Connector technical profile** in **Retail > Channel setup > Fiscal integration > Connector technical profiles** for each fiscal connector.
		- Select a connector name.
		- Select a connector type: 
			- **Local**: select this type for devices connected to a hardware station.

	>[!NOTE]
	> Only local connectors are supported currently.

	Parameters on the **Device** and **Settings** tabs can be changed in a connector technical profile. Click **Update** if you want to restore the default parameters defined in the fiscal connector configuration. While loading a new version of an XML configuration, a message will be displayed notifying the user that the current fiscal connector or fiscal document provider is already in use. This procedure does not override manual changes made in connector functional profiles and connector technical profiles earlier. To apply default set of parameters from a new configuration, click **Update** on the **Connector functional profiles** page or the **Connector technical profiles** page.

4.  Create **Fiscal connector groups**.

	A fiscal connector group combines functional profiles of fiscal connectors that perform identical functions and are used at the same step of a fiscal registration process. For example, if several fiscal printer models can be used in a retail store, fiscal connectors for these fiscal printers may be combined in a fiscal connector group.
	
	- Open the **Retail > Channel setup > Fiscal integration > Fiscal connector group** page and create a new fiscal connector group.
	- Add functional profiles to the connector group. Click **Add** on the **Functional profiles** page and select a profile number. Within a connector group, each fiscal connector can only have one functional profile.
	- If you want to suspend usage of the functional profile, set **Disable** to **Yes**. This change affects the current connector group only. You can continue using the same functional profile in other connector groups.

5. Create a **Fiscal registration process**.

	A fiscal registration process is defined by the sequence of registration steps and the connector group used on each step. 
	
	- Open the **Retail > Channel setup > Fiscal integration > Fiscal registration processes** page and create a new record for each unique process of fiscal registration.
	- Add registration steps to the process:
		- Click **Add**.
		- Select a connector type. 
		- Select an appropriate connector group in the field **Group number**.

6. Assign entities of the fiscal registration process to POS profiles. 
 
	6.1.  Assign the fiscal registration process to a POS functionality profile on the **Retail > Channel setup > POS setup > POS profiles > Functionality profiles** page. 
  
	Click **Edit** and select a **Process number** on the **Fiscal registration process** tab.      

	6.2. Assign connector technical profiles to a hardware profile on the **Retail > Channel setup > POS setup > POS profiles > Hardware profiles** page.
    
	Click **Edit**, add a line on the **Fiscal peripherals** tab, and select a connector technical profile in the field **Profile number**.

	>[!NOTE]
	> You can add several technical profiles to the same hardware profile. However, a hardware profile or POS functionality profile should have only one intersection with any fiscal connector group. 

	The fiscal registration flow is defined by the fiscal registration process as well as by some parameters of fiscal integration components: the Commerce runtime extension for the fiscal document provider and the Hardware station extension for the fiscal connector.

	- The subscription of events and transactions to fiscal registration is predefined in the fiscal document provider.
	- The fiscal document provider is also responsible for the identification of the fiscal connector to be used for fiscal registration. It matches the connector functional profiles that are included in the connector group specified on the current step of the fiscal registration process with the connector technical profile assigned to the hardware profile of the hardware station which POS is paired to.
	- The fiscal document provider uses the **Data mapping** settings from the fiscal document provider configuration for the transformation of transaction/event data such as taxes and payments while generating a fiscal document.
	- The fiscal connector can either send a fiscal document generated by the fiscal document provider to the fiscal device as-is or parse it and transform into a sequence of commands of the device API, depending on how the communication is handled.  

7. Validate the fiscal registration process.
  
	Open the page **Fiscal registration processes** (**Retail > Channel setup > Fiscal integration > Fiscal registration processes**) and click **Validate** to validate the fiscal registration process. It’s recommended to run such a validation in the following cases.
	
	- For a new registration process after all the settings are completed, including assigning to POS functionality profiles and hardware profiles.
	- After making some changes to an existing fiscal registration process that may result in selecting a different fiscal connector in run-time (for example, changing the connector group for a fiscal registration process step; enabling a connector functional profile in a connector group; or adding a new connector functional profile to a connector group).
	- After making changes in the assignment of connector technical profiles to hardware profiles.
      
8. Open the **Distribution scheduler** page and run the job **1070** to transfer data to the Channel database.

## Setting up fiscal texts for discounts
 
In some cases, it is required to print a special text in a fiscal receipt if a discount is applied. You can set up fiscal texts for discounts on the **Fiscal connector groups** page (**Retail > Channel setup > Fiscal integration > Fiscal connector group**):

- For manual discounts applied on POS, a fiscal text should be set for the info code or info code group specified as the **Product discount** info code in the POS functionality profile.
	- Click **Text for fiscal receipt** on the **Fiscal connector groups** page.
	- On the **Info codes** tab, click **Add** and select an info code or info code group.
	- Select the **Info code number**.
	- Select the **Subcode number** if it is required for the selected info code.
	- Specify a fiscal text that should be printed in a fiscal receipt in the field **Text for fiscal receipt**.
	- Set the parameter **Print user input on fiscal receipt** to **Yes** to override the text in a fiscal receipt with the information entered by user on POS manually. This option applies to info codes with Input type **Text** only.
    
	>[!NOTE]
	> You can specify a fiscal text for several info codes to support such scenarios as using of info code groups, linked info codes, and triggered info codes. As a result, the fiscal receipt will contain the fiscal texts from all info codes linked to the transaction line where the discount was applied. 

- For channel-specific discounts, a fiscal text should be defined for the **Discount ID**.
	- Click **Text for fiscal receipt** on the **Fiscal connector groups** page.
	- On the tab **Discounts** click **Add** and select a **Discount ID**.
	- Specify a fiscal text that should be printed in a fiscal receipt in the field **Text for fiscal receipt**.

	>[!NOTE]
	> If several discounts are applied to the same transaction line, the fiscal receipt will contain fiscal texts from all discounts linked to the transaction line. 

## Error handling settings

Error handling options that are available in fiscal integration are set in the fiscal registration process. For more information about error handling in fiscal integration, see [Error handling](fiscal-integration-for-retail-channel#error-handling).

1. On the **Fiscal registration processes** page (**Retail > Channel setup > Fiscal integration > Fiscal registration processes**), you can activate the following parameters for each fiscal registration process step.

	- **Allow skip**: this parameter enables the **Skip** option in the error handling dialog.
	- **Allow mark as registered**: this parameter enables the **Mark as registered** option in the error handling dialog.

2. Options **Skip** and **Mark as registered** in the error handling dialog require the permission **Allow skip or mark as registered**. 

	- Open the **Permission groups** page (**Retail > Employees > Permission groups**) and enable the permission **Allow skip or mark as registered**.

3. Options **Skip** and **Mark as registered** allow operators to enter additional information when fiscal registration fails. The info codes **Skip** and **Mark as registered** should be specified on a fiscal connector group to enable this. The information entered is saved as an info code transaction linked to the fiscal transaction. See [Info codes and info code groups](../info-codes-retail) for more details about info codes.

	>[!NOTE]
	> The trigger function with the value *Product* is not supported for the info codes that are used as **Skip** and **Mark as registered** in fiscal connector groups.

	- Open the **Fiscal connector groups** page.
	- On the **Info codes** tab, select info codes or info code groups in the fields **Skip** and **Mark as registered**.

	>[!NOTE]
	> One fiscal document and one non-fiscal document can be generated on any step of a fiscal registration process. A fiscal document provider extension identifies every type of transaction or event as related to fiscal or non-fiscal documents. The error handling feature applies to fiscal documents only. 
	> - *Fiscal document*: a mandatory document that should be registered successfully (e.g., a fiscal receipt).
	> - *Non-fiscal document*: a supplementary document for the transaction or event (e.g., a gift card slip).

     
## Setting up fiscal X/Z reports from POS

To enable running fiscal X/Z reports from POS, new buttons should be added to a POS layout.
- Open the **Button grids** page.
- Follow the instructions from [Add a custom operation button to the POS layout in Retail headquarters](../dev-itpro/add-pos-operations#add-a-custom-operation-button-to-the-pos-layout-in-retail-headquarters) to install the designer and update a POS layout.
	- Select the layout that you are going to update. 
	- Add a new button and set the button property **Print fiscal X**.
	- Add a new button and set the button property **Print fiscal Z**.
	- Run the job **1090** on the **Distribution schedule** page to transfer changes to the Channel database.
