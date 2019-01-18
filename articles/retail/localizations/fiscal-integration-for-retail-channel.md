---
# required metadata

title: Fiscal integration setup guide
description: This topic provides instructions for setting up the fiscal integration for Retail POS. 
author: josaw
manager: annbe
ms.date: 11/01/2018
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
# Fiscal integration setup guide

[!include [banner](../includes/banner.md)]

This topic is a setup guide explaining the required settings of the Fiscal integration functionality that is available in Microsoft Dynamics 365 for Retail. For more information about the fiscal integration, see [Fiscal integration functionality](fiscal-integration-functionality.md#fiscal-integration-functionality).

Users can perform the following tasks. 
- Configure fiscal connectors, which are fiscal devices or services used for fiscal registration purposes like saving, digital signatures, and secured submission of fiscal data.
- Configure the document provider, which defines an output method and an algorithm of fiscal document generation.
- Configure the fiscal registration process, which is defines a sequence of steps and a group of connectors used on each step.
- Assign fiscal registration processes to POS functionality profiles.
- Assign connector technical profiles, either to hardware profiles (for the local fiscal connectors) or to POS functionality profiles (for other fiscal connector types).

## How to set up a fiscal registration process
Before using the fiscal integration functionality, the following settings should be done:

1. Update retail parameters.

  - Set the parameter **Enable fiscal integration** to **Yes** on tab General of the **Retail parameters** page.

  - Define the number sequence on the **Retail parameters** page for the fiscal functional profile number.
  
  - Define the number sequences on the **Retail shared parameters** page for the following references:
  
    - Fiscal technical profile number
    - Fiscal connector group number
    - Registration process number

    >[!NOTE]
     > Number sequences are optional. All fiscal integration entities might have numbers filled in either from a number sequence or manually.

2. Upload configurations of two components included in the fiscal integration sample: a fiscal connector and a fiscal document provider.
  - Load an XML configuration on the **Fiscal connectors** page (**Retail > Channel setup > Fiscal integration > Fiscal connectors**) for each device or service that you plan to use for fiscal integration purposes. 
  
     By clicking button **View**, you may view all functional and technical profiles related to the current fiscal connetor.

  -  Load an XML configuration on the **Fiscal document providers** page (**Retail > Channel setup > Fiscal integration > Fiscal document providers**) for each device or service that you plan to use.
 
     By clicking button **View**, you may view all functional profiles related to the current fiscal document provider.


     >[!NOTE]
      > Data mapping is considered as a part of the fiscal document provider. To set up different data mappings for the same connector (like state-specific regulations), you should create different fiscal document providers.

3. Create connector functional profiles and connector technical profiles.

  - Create a **Connector functional profile** in **Retail > Channel setup > Fiscal integration > Connector functional profiles** for each combination of a fiscal connector and a fiscal document provider related to this fiscal connector.
    - Select a connector name.
    - Select a document provider.

     Data mapping parameters could be changed in a connector functional profile. Click button **Update** if you want to restore the default parameters defined in a fiscal document provider configuration.

       #### Examples 

    |  | Format | Example | 
    |--------|--------|--------|
    | VAT rates settings | value : VATrate | 1 : 2000, 2 : 1800 |
    | VAT codes mapping | VATcode : value | vat20 : 1, vat18 : 2 |
    | Tender types mapping | TenderTyp : value | Cash : 1, Card : 2 |
  
    >[!NOTE]
       > Connector functional profiles are company-specifis. So, if you plan to use the same combination of a fiscal connector and a fiscal document provider in several companies, every company should have its own connector functional profile.

  - Create a **Connector technical profile** in **Retail > Channel setup > Fiscal integration > Connector technical profiles** for each fiscal connector.
    - Select a connector name.
    - Select a connector type: 
        - **Local** - select this type for devices connected to a hardware station.
        - **Internal** - select this type for fiscal services and applications connected via CRT.
        - **External** - select this type for external fiscal services like a web-portal provided by a tax authority.

       >[!NOTE]
      > Currently connector types Internal and External are hidden in UI, since already released fiscal integration samples work with fiscal devices connected to a hardware station.

	  Parameters on tabs **Device** and **Settings** could be changed in a connector technical profile. Click button **Update** if you want to restore the default parameters defined in a fiscal document provider configuration. While loading a new version of an XML configuration, user gets an infolog-message notifying if the current fiscal connector or fiscal document provider is already in use. This procedure do now override manual changes made in connector functional profiles and connector technical profiles earlier. In order to apply default set of parameters from a new configuration, click **Update** on the **Connector functional profiles** page and **Connector technical profiles** page.

4.  Create **Fiscal connector groups**.

    Open the **Retail > Channel setup > Fiscal integration > Fiscal connector group** page. A connector group is a subset of functional profiles linked with fiscal connectors that perform identical functions and are used at the same stage within a fiscal registration process.

   - Add functional profiles to the connector group. Click **Add** on the **Functional profiles** page and select a profile number. Within a connector group, each fiscal connector can only have one functional profile.

   - If you want to suspend usage of the functional profile, set **Disable** to **Yes**. This change affects the current connector group only. You can continue using the same functional profile in other connector groups.

5. Create a **Fiscal registration process**.

   Open the **Retail > Channel setup > Fiscal integration > Fiscal registration processes** page and create a new record for each unique process of the fiscal integration. A registration process is defined by the sequence of the registration steps and the connector group used on each step. 
  
  - Add registration steps to the process:
	  - Click **Add**.
	  - Select a connector type. 
    - Select an appropriate connector group in the field **Group number**

  6. Assign entities of the fiscal registration process to POS profiles. 
  
     The connector type defines where the system will search a connector technical profile in run-time: on a hardware profile for connector type **Local**, or on POS functionality profile for other fiscal connector types.

  -  Assign fiscal registration process to POS functionality profiles on the **Retail > Channel setup > POS setup > POS profiles > Functionality profiles** page.
     - Click **Edit** and select a **Process number** on the **Fiscal registration process** tab.

  - Assign connector technical profiles with the connector type **Internal** or **External** on the **Retail > Channel setup > POS setup > POS profiles > Functionality profiles** page.   
    - Click **Edit** and add a line on the **Fiscal peripherals** tab, select a connector technical profile in the field **Profile number**.

  - Assign connector technical profiles with the connector type **Local** to hardware profiles on the **Retail > Channel setup > POS setup > POS profiles > Hardware profiles** page.
    - Click **Edit** and add a line on the **Fiscal peripherals** tab, select a connector technical profile in the field **Profile number**.

     >[!NOTE]
     > You can add several technical profiles to the same hardware profile or POS functionality profile. However, this is not supported if a hardware profile or POS functionality profile has more than one intersection with any connector group. 

  7. Validate the fiscal registration process.
  
     Open page **Fiscal registration processes** (**Retail > Channel setup > Fiscal integration > Fiscal registration processes**) and click button **Validate** to check the fiscal registration process. It’s recommended to run such a validation in the following cases:
      - For a new registration process after all the settings are completed, including assigning to POS functionality profiles and hardware profiles.
      - After making some changes to an existing registration process that may lead to selection of a different fiscal connector in run-time (for example, changing a connector group in the fiscal registration process, or enabling a connector functional profile in a connector group, or adding a new connector functional profile to a connector group).
      - After making changes in the connector technical profiles assignment to hardware profiles or POS functionality profiles.
      
   8. Open the **Distribution scheduler** page and run the job **1070** to transfer data to the Channel database.

## Setting up a fiscal text for discounts
 
 In some cases it's required to print a special text in a fiscal receipt if a discount was applied. You can set up a fiscal text for discounts on the **Fiscal connector groups** page (**Retail > Channel setup > Fiscal integration > Fiscal connector group**).  

  - For manual discounts applied on POS a fiscal text should be defined for the Info code or Info code group specified as the **Product discount** info code in the POS functionality profile. You can find more details regarding info codes in the topic [Info codes and info code groups](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/info-codes-retail).
    - Click button **Text for fiscal receipt** on the **Fiscal connector groups** page.
    - On tab **Info codes** click button **Add** and select an Info code or Info code group.
    - Select the **Info code number**.
    - Select the **Subcode number** if it's required for the selected info code.
    - Specify a fiscal text that should be printed in a fiscal receipt in the field **Text for fiscal receipt**.
    - Set the parameter **Print user input on fiscal receipt** to **Yes** if order to override the text in a fiscal receipt with inforamtion entered by user on POS manually. this options applies to the info codes with Input type **Text** only.
    
    >[!NOTE]
     > You can specify a fiscal text for several info codes to support such scenarios as using of info code groups, linked info codes and triggered info codes. In result a fiscal receipt will contain a fiscal text from all info codes linked with a transaction line where the discount was applied. 

    - For channel-specific discounts a fiscal text should be defined for the Discount ID. You can find more details regarding discounts in these topics: [Retail discounts](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/retail-discounts-overview), [Define channel-specific discounts](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/define-channel-specific-discounts).
      - Click button **Text for fiscal receipt** on the **Fiscal connector groups** page.
      - On tab **Discounts** click button **Add** and select a Discount ID.
      - Specify a fiscal text that should be printed in a fiscal receipt in the field **Text for fiscal receipt**.

    >[!NOTE]
     > If several discounts were applied to the same transaction line, a fiscal receipt would contain a fiscal text from all discounts linked with that transaction line. 

## Error handling settings

Fiscal register proccesses have some additional settings to define possible options when the fiscal registration has failed. For more information about the error handling feature in scope of the fiscal integration functionality, see [Error handling](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/fpi-sample-pol/articles/retail/localizations/fiscal-integration-functionality.md#error-handling).

1. On the page **Fiscal registration processes** (**Retail > Channel setup > Fiscal integration > Fiscal registration processes**) you can activate the following parameters for each registration process step:

  - **Allow skip** - this parameter enables the **Skip** option in error handling dialog.
  - **Allow mark as registered** - this parameter enables the **Mark as registered** option in error handling dialog.
  - **Optional** - this parameter means that the fiscal registration is optional. Error handling feauture is not used in this case.

2. Options **Skip** and **Mark as registered** in the error handling dialog require the permission **Allow skip or mark as registered**. If parameters **Allow skip** or **Allow mark as registered** are activated, then this permission must be enabled to some of users at least. 

  - Open the **Permission groups** page (**Retail > Employees > Permission groups**) page, and enable the permission **Allow skip or mark as registered**.

3. Options **Skip** and **Mark as registered** in the error handling dialog allow users to enter an additional information on POS when the fiscal registration has failed. The info codes **Skip** and **Mark as registered** should be specified on a fiscal connector group to make is possible entering additional details on POS and saving this information as an Info code transaction linked with a fiscal transaction. You can find more details regarding info codes in the topic [Info codes and info code groups](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/info-codes-retail).

    >[!NOTE]
     > It's not reccomended to set up info codes **Skip** and **Mark as registered** as info codes with the trigger function having value *Product*.

  - Open the **Fiscal connector groups** page.
  - on the tab **Info codes** select info codes or info code groups in fields **Skip** and **Mark as registered**.

    >[!NOTE]
     > One fiscal document and several non-fiscal documents could be generated within one step of the fiscal registration process. A fiscal document provider extension identifies every type of event or transaction as related to fiscal or non-fiscal documents. The error handling feature applies to the fiscal documents only.
     
## Set up running fiscal X/Z reports from POS

In order to enable running running fiscal X/Z reports from POS, new buttons should be added to a POS layout.
  - Open the **Button grids** page in Retail headquarters.
  - Follow the instructions from [Add a custom operation button to the POS layout in Retail headquarters](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/add-pos-operations#add-a-custom-operation-button-to-the-pos-layout-in-retail-headquarters) to install the designer and update a POS layout.
    - Select the layout that you are going to update. 
    - Add a new button and set the button property **Print fiscal X**.
    - Add another button and set the button property **Print fiscal Z**.
    - Run the job **1090** on the **Distribution schedule** page to transfer changes to the Channel database.
