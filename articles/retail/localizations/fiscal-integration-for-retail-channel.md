---
# required metadata

title: Fiscal integration for Retail channel
description: This topic provides an overview of the fiscal integration for Retail POS. 
author: KirillKozlov
manager: epopov
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
ms.search.region: 
ms.search.industry: Retail
ms.author: v-kikozl
ms.search.validFrom: 2018-11-1
ms.dyn365.ops.version: 8.1.1

---
# Fiscal integration for Retail channel

This article is an overview of the Fiscal integration functionality that is available in Microsoft Dynamics 365 for Retail, and applies to Dynamics 365 for Retail.
The fiscal integration functionality is a framework designed to support local fiscal laws aimed to prevent fraud in Retail industry. Typical scenarios that could be covered by using the fiscal integration:
- Print an appropriate fiscal receipt and give it to the customer
- Secured submission of the information related to sales and returns  performed on POS to an external service provided by the authority 
- Data protection with a digital signature authorized by the authority

The article provides guidelines for setting up the Fiscal integration functionality which allows to perform the following tasks: 

- Configure fiscal connectors – fiscal devices or services used for fiscal registration purposes like saving, digital signature and secured submission of the fiscal data,
- Configure document provider defining an output method and an algorithm of fiscal documents generation,
- Configure Fiscal registration process – a sequence of steps of the fiscal registration process and a group of connectors used on each step.

Common fiscal integration execution flow is described below:

1. Initialization of the fiscal registration process 
  
   After performing some actions where the fiscal registration is required, e.g. after a retail transaction has been concluded, system finds a Fiscal registration process associated with current POS functionality profile.
2. Searching a fiscal connector
   
   For each fiscal registration step included into the found Fiscal registration process system matches the list of fiscal connectors that have a functional profile included in the connector group specified for this step with the list of connectors that have a technical profile associated with current Hardware profile (for connector type equal "Local" only) or with current POS functionality profile (for other connector types).
3. Performing the fiscal integration

   System executes all necessary actions defined by an assembly linked with the found connector in accordance with the settings of functional profile and technical profile found on the previous step for this connector.

Before using the Fiscal integration functionality, the following settings should be maintained:

- Define number sequences in Retail parameters for the following references:
  
  - Fiscal functional profile number
  - Fiscal technical profile number
  - Fiscal connector group number
  - Registration process number

- Create a **Fiscal connector** in **_Retail > Channel setup > Fiscal integration > Fiscal connectors_** for each device or service that you plan to use for the fiscal integration purposes.
  
  - Load XML-configuration. 

-  Create a **Fiscal document provider** in **_Retail > Channel setup > Fiscal integration > Fiscal document providers_** for all fiscal connectors. Data mapping is considered as a part of the Fiscal document provider. So, to set up different data mappings for the same connector (e.g. depending on the State-specific regulations), you should create different Fiscal document providers.
   - Select a Connector name
   - Load XML-configuration

- Create a **Connector functional profile** in **_Retail > Channel setup > Fiscal integration > Connector functional profiles_** for each Fiscal document provider.
  - Select a Connector name,
  - Select a Document provider,
  - Specify VAT rates settings on the tab Service setup,
  - Specify VAT codes mapping and Tender type mapping on the tab _Data mapping_.

- Create **Fiscal connector groups** in **_Retail > Channel setup > Fiscal integration > Fiscal connector group_**. Connector group is a range of connector functional profiles that can substitute each other depending on what device or service is currently available. 

   - Select a Connector name
   - Add functional profiles to the connector group – click button Add in group Functional profiles and select a Profile number
   - If you want to suspend usage of the functional profile, set flag **Disable** to **_Yes_**. 
   
     This change affects a current connector group only, you may continue using the same functional profile in other connector groups.

     Note: Each connector may be presented in a connector group by one functional profile only.

- Create a **Connector technical profile**  in **_Retail > Channel setup > Fiscal integration > Connector technical profiles_** for each Fiscal connector.
  - Select a Connector name,
  - Select Connector type: 
	
    Local – set this type for physical devices or applications installed on a local machine.
  - Specify settings on the tab _Connection_.
 
- Create a **Fiscal registration process** in **_Retail > Channel setup > Fiscal integration > Fiscal registration processes_** for each unique process of the fiscal integration. A registration process is defined by sequence of the registration steps and a connector group used on each step. 
  
  - Add registration steps to the process:
	  - Click button **_Add_**,
	  - Select a connector type,
	
        Note: This field defines where the system will search a technical profile of the connector: in Hardware profiles for connector type "Local", or in POS functionality profiles for other fiscal connector types.
    - Select a Connector group that is going to be used on this step.

       Note: Bu clicking the button **_Validate_**, you can check an integrity of the registration process structure. It’s recommended to make such validation:

       - for new registration process after all settings are completed, including binding to POS functionality profiles and Hardware profiles
       - after making updates in existing registration process

-  Bind Fiscal registration processes to POS functionality profiles in **_Retail \ Channel setup \ POS setup \ POS profiles \ Functionality profiles_**:
   - Click button Edit and select a Process number on the tab Fiscal registration process.
- Bind Connector technical profiles to Hardware profiles (Retail \ Channel setup \ POS setup \ POS profiles \ Hardware profiles):
   - Click button Edit, then click button New on the tab Fiscal technical profile.
   - Select a Connector technical profile in the field Profile number.
   
     Note: You can add several technical profiles to a Hardware profile, but the situation when a Hardware profile has more than one intersection with any connector group is not supported. It’s recommended to validate a registration process after updating all hardware profiles to avoid incorrect settings.
