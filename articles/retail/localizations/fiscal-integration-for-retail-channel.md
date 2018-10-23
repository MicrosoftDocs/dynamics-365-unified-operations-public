---
# required metadata

title: Fiscal integration for Retail channel
description: This topic provides an overview of the fiscal integration for Retail POS. 
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
ms.search.region: 
ms.search.industry: Retail
ms.author: v-kikozl
ms.search.validFrom: 2018-11-1
ms.dyn365.ops.version: 8.1.1

---
# Fiscal integration for Retail channel

This article is an overview of the Fiscal integration functionality that is available in Microsoft Dynamics 365 for Retail, and applies to Dynamics 365 for Retail.
The fiscal integration functionality is a framework designed to support local fiscal laws aimed to prevent fraud in Retail industry. Typical scenarios that could be covered by using the fiscal integration:
- Print an appropriate fiscal receipt and give it to the customer.
- Secured submission of the information related to sales and returns performed on POS to an external service provided by the authority.
- Data protection with a digital signature authorized by the authority.

The article provides guidelines for setting up the Fiscal integration functionality which allows users to perform the following tasks. 

- Configure fiscal connectors – fiscal devices or services used for fiscal registration purposes like saving, digital signature, and secured submission of the fiscal data.
- Configure document provider defining an output method and an algorithm of fiscal documents generation.
- Configure Fiscal registration process – a sequence of steps of the fiscal registration process and a group of connectors used on each step.
- Assign fiscal registration processes to POS functionality profiles.
- Assign connector technical profiles either to Hardware profiles (this approach is used for the local fiscal connectors) or to POS functionality profiles (for other fiscal connector types).

The common fiscal integration execution flow is described below.

1. Initialization of the fiscal registration process.
  
   After performing some actions where the fiscal registration is required, e.g. after a retail transaction has been concluded, the system finds a fiscal registration process associated with current POS functionality profile.

1. Search for a fiscal connector.
   
   For each fiscal registration step included into the found fiscal registration process, the system matches the list of fiscal connectors that have a functional profile included in the connector group specified for this step with the list of connectors that have a technical profile associated with current hardware profile (for connector type that equals **Local** only) or with the current POS functionality profile (for other connector types).
   
1. Perform the fiscal integration.

   The system executes all necessary actions defined by an assembly linked with the found connector in accordance with the settings of the functional profile and technical profile found on the previous step for this connector.

Before using the fiscal integration functionality, the following settings should be maintained:

- Define the number sequence in **Retail parameters** for the reference:
  
  - Fiscal functional profile number.
  
- Define the number sequences in **Retail shared parameters** for the following references:
  
  - Fiscal technical profile number
  - Fiscal connector group number
  - Registration process number.

- Create a **Fiscal connector** in **Retail > Channel setup > Fiscal integration > Fiscal connectors** for each device or service that you plan to use for the fiscal integration purposes.
    - Load XML-configuration. 

-  Create a **Fiscal document provider** in **Retail > Channel setup > Fiscal integration > Fiscal document providers** for all fiscal connectors. Data mapping is considered as a part of the fiscal document provider. To set up different data mappings for the same connector (e.g. depending on the State-specific regulations), you should create different Fiscal document providers.
      - Load XML-configuration.

- Create a **Connector functional profile** in **Retail > Channel setup > Fiscal integration > Connector functional profiles** for each Fiscal document provider.
  - Select a Connector name.
  - Select a Document provider.
  - Specify VAT rates settings on the tab **Service setup**.
  - Specify VAT codes mapping and Tender type mapping on the tab **Data mapping**.

Examples:

  |  | Format | Example | 
  |--------|--------|--------|
  | VAT rates settings | value : VATrate | 1 : 2000, 2 : 1800 |
  | VAT codes mapping | VATcode : value | vat20 : 1, vat18 : 2 |
  | Tender types mapping | TenderTyp : value | Cash : 1, Card : 2 |

- Create **Fiscal connector groups** in **Retail > Channel setup > Fiscal integration > Fiscal connector group**. Connector group is a subset of functional profiles linked with fiscal connectors that perform identical functions and are used at the same stage within a fiscal registration process.

   - Add functional profiles to the connector group – click **Add** in **Functional profiles** and select a profile number.
   - If you want to suspend usage of the functional profile, set the flag **Disable** to **Yes**. 
   
     This change affects the current connector group only. You may continue using the same functional profile in other connector groups.

     >[!NOTE]
     > Within a connector group, each fiscal connector may have one functional profile only.

- Create a **Connector technical profile** in **Retail > Channel setup > Fiscal integration > Connector technical profiles** for each Fiscal connector.
  - Select a Connector name.
  - Select Connector type: 
        - **Local**: set this type for physical devices or applications installed on a local machine.
        - **Internal**: set this type for fiscal devices and services connected to Retail Server.
        - **External**: for external fiscal services like a web-portal provided by a tax authority.
  - Specify settings on the **Connection** tab.

      
 >[!NOTE]
 > The system can load an updated version of a configuration loaded earlier both for functoional and technical profiles. If an appropriate connector or document provider is already in use, you will be notified. By default, the system keeps changes made manually in functional and technical profiles. In order to override them with the default set of parameters from a configuration, you should click **Update** on the  **Connector functional profiles** and **Connector technical profiles** pages.
 
- Create a **Fiscal registration process** in **Retail > Channel setup > Fiscal integration > Fiscal registration processes** for each unique process of the fiscal integration. A registration process is defined by sequence of the registration steps and a connector group used on each step. 
  
  - Add registration steps to the process:
	  - Click **Add**.
	  - Select a connector type.
	  >[!NOTE]
          > This field defines where the system will search a technical profile of the connector: in hardware profiles for connector type **Local**, or in POS functionality profiles for other fiscal connector types.
	  
   - Select a Connector group to be used on this step.
     >[!NOTE]
     >  By clicking **Validate**, you can check an integrity of the registration process structure. It’s recommended to make such validations in the following cases:
         - For a new registration process after all the settings are completed, including binding to POS functionality profiles and Hardware profiles.
         - After making updates in an existing registration process.

-  Bind Fiscal registration processes to POS functionality profiles in **Retail > Channel setup > POS setup > POS profiles > Functionality profiles**.
   - Click **Edit** and select a **Process number** on the **Fiscal registration process** tab.
- Bind the connector technical profiles to the hardware profiles in **Retail > Channel setup > POS setup > POS profiles > Hardware profiles.
   - Click **Edit**, then click **New** on the **Fiscal technical profile** tab.
   - Select a connector technical profile in the **Profile number** field.
   
     >[!NOTE]
     > You can add several technical profiles to a hardware profile, but cases where a hardware profile has more than one intersection with any connector group is not supported. It’s recommended that you validate a registration process after updating all the hardware profiles to avoid incorrect settings.
