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
ms.search.region: Global
ms.search.industry: Retail
ms.author: v-kikozl
ms.search.validFrom: 2018-11-1
ms.dyn365.ops.version: 8.1.1

---
# Fiscal integration for Retail channel

[!include [banner](../includes/banner.md)]

This topic is an overview of the fiscal integration functionality that is available in Microsoft Dynamics 365 for Retail. The fiscal integration functionality is a framework designed to support local fiscal laws that are aimed to prevent fraud in the Retail industry. Typical scenarios that could be covered by using fiscal integration include:

- Printing a fiscal receipt and giving it to the customer.
- Securing the submission of the information related to sales and returns performed on POS to an external service provided by the authority.
- Using data protection with a digital signature authorized by the authority.

This topic provides guidelines for setting up fiscal integration so users can perform the following tasks. 

- Configure fiscal connectors, which are fiscal devices or services used for fiscal registration purposes like saving, digital signatures, and secured submission of fiscal data.
- Configure the document provider, which defines an output method and an algorithm of fiscal document generation.
- Configure the fiscal registration process, which is defines a sequence of steps and a group of connectors used on each step.
- Assign fiscal registration processes to POS functionality profiles.
- Assign connector technical profiles, either to hardware profiles (for the local fiscal connectors) or to POS functionality profiles (for other fiscal connector types).

## Fiscal integration execution flow
The following scenario shows the common fiscal integration execution flow.

1. Initialization of the fiscal registration process.
  
   After performing some actions where fiscal registration is required, such as after a retail transaction has been concluded, the fiscal registration process is associated with the current POS functionality profile.

1. Search for a fiscal connector.
   
   For each fiscal registration step included in the fiscal registration process, the system matches the list of fiscal connectors. These connectors have a functional profile included in the specified connector group, with a list of connectors that have a technical profile associated with the current hardware profile (for a connector type that equals **Local** only) or with the current POS functionality profile (for other connector types).
   
1. Perform the fiscal integration.

   The system executes all necessary actions defined by an assembly linked with the found connector. This is done in accordance with the settings of the functional profile and technical profile that were found on the previous step for this connector.

## Setup needed before using fiscal integration
Before using the fiscal integration functionality, you should define the following settings:

- Define the number sequence on the **Retail parameters** page for the fiscal functional profile number.
  
- Define the number sequences on the **Retail shared parameters** page for the following references:
  
  - Fiscal technical profile number
  - Fiscal connector group number
  - Registration process number

- Create a **Fiscal connector** in **Retail > Channel setup > Fiscal integration > Fiscal connectors** for each device or service that you plan to use for fiscal integration purposes.

-  Create a **Fiscal document provider** in **Retail > Channel setup > Fiscal integration > Fiscal document providers** for all fiscal connectors. Data mapping is considered a part of the fiscal document provider. To set up different data mappings for the same connector (like state-specific regulations), you should create different fiscal document providers.

- Create a **Connector functional profile** in **Retail > Channel setup > Fiscal integration > Connector functional profiles** for each fiscal document provider.
  - Select a connector name.
  - Select a document provider.
  - Specify VAT rates settings on the **Service setup** tab.
  - Specify VAT codes mapping and tender type mapping on the **Data mapping** tab.

  #### Examples 

  |  | Format | Example | 
  |--------|--------|--------|
  | VAT rates settings | value : VATrate | 1 : 2000, 2 : 1800 |
  | VAT codes mapping | VATcode : value | vat20 : 1, vat18 : 2 |
  | Tender types mapping | TenderTyp : value | Cash : 1, Card : 2 |

- Create **Fiscal connector groups** in **Retail > Channel setup > Fiscal integration > Fiscal connector group**. A connector group is a subset of functional profiles linked with fiscal connectors that perform identical functions and are used at the same stage within a fiscal registration process.

   - Add functional profiles to the connector group. Click **Add** on the **Functional profiles** page and select a profile number.
   - If you want to suspend usage of the functional profile, set **Disable** to **Yes**. 
   
     This change affects the current connector group only. You can continue using the same functional profile in other connector groups.

     >[!NOTE]
     > Within a connector group, each fiscal connector can only have one functional profile.

- Create a **Connector technical profile** in **Retail > Channel setup > Fiscal integration > Connector technical profiles** for each fiscal connector.
  - Select a connector name.
  - Select a connector type: 
      - **Local** - Set this type for physical devices or applications installed on a local machine.
      - **Internal** - Set this type for fiscal devices and services connected to Retail Server.
      - **External** - For external fiscal services like a web-portal provided by a tax authority.
	
  - Specify settings on the **Connection** tab.

      
 >[!NOTE]
 > An updated version of a configuration that was loaded earlier will be loaded for both functional and technical profiles. If an appropriate connector or document provider is already in use, you will be notified. By default, all changes that have been made manually in functional and technical profiles will be stored. In order to override these profiles with the default set of parameters from a configuration, click **Update** on the **Connector functional profiles** page and **Connector technical profiles** page.
 
- Create a **Fiscal registration process** in **Retail > Channel setup > Fiscal integration > Fiscal registration processes** for each unique process of the fiscal integration. A registration process is defined by the sequence of the registration steps and the connector group used on each step. 
  
  - Add registration steps to the process:
	  - Click **Add**.
	  - Select a connector type.
	  
	  >[!NOTE]
	  > This field defines where the system will search in a technical profile for the connector, either in hardware profiles for connector type **Local**, or in POS functionality profiles for other fiscal connector types.
	  
   - Select a connector group.
   
     >[!NOTE]
     > Click **Validate** to check the integrity of the registration process structure. It’s recommended that validations be made in the following cases:
       >- For a new registration process after all the settings are completed, including binding to POS functionality profiles and hardware profiles.
       >- After making updates to an existing registration process.

-  Bind fiscal registration processes to POS functionality profiles in **Retail > Channel setup > POS setup > POS profiles > Functionality profiles**.
   - Click **Edit** and select a **Process number** on the **Fiscal registration process** tab.
- Bind the connector technical profiles to the hardware profiles in **Retail > Channel setup > POS setup > POS profiles > Hardware profiles**.
   - Click **Edit**, then click **New** on the **Fiscal technical profile** tab.
   - Select a connector technical profile in the **Profile number** field.
   
     >[!NOTE]
     > You can add several technical profiles to a hardware profile. However, this is not supported if a hardware profile has more than one intersection with any connector group. To avoid incorrect settings, it’s recommended that you validate the registration process after updating all the hardware profiles.
