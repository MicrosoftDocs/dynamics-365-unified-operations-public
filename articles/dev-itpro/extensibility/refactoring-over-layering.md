---
# required metadata

title: Relax model restrictions to enable the refactoring of over-layering into extensions
description: This topic provides information about relaxing model restrictions to enable the refactoring of over-layering into extensions which is needed in 8.0+ because models are sealed 
author: CGarty
manager: AnnBe
ms.date: 05/01/2018
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: CGarty
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: Platform update 4

---

# Relax model restrictions to enable the refactoring of over-layering into extensions

[!INCLUDE [banner](../includes/banner.md)]

## Introduction ##
Dynamics 365 for Finance and Operations release 8.0, or higher, will not allow customization of Microsoft’s code using over-layering. Instead extension capabilities should be used to modify and add behavior. The "no over-layering" restriction is a key part of the evolution of the product towards providing customers with a cloud ERP service that is simple to update and always running the most recent version possible to allow all customers to receive the benefits of the latest features and fixes.

After upgrading code to 8.0 or later any customizations that still use over-layering with cause errors when compiling the application. In order to refactor the code, the over-layering restriction can be temporarily relaxed in the model descriptor file of the model that is being over-layered. This temporary relaxation only works on development and demo environments and cannot be deployed on runtime environments like Standard Acceptance Test (or higher) sandbox or production environments. Relaxing the descriptor restriction will enable the code to be gradually refactored to extensions, compiled, run, and tested. 

## Detailed process ##

1. Deploy an 8.0+ development environment - either a cloud environment or local VM.
2. Run the LCS code upgrade service to upgrade the solution.
3. Temporarily allow over-layering in Microsoft models as needed to enable compilation.
    
    a. Locate the desired model within the C:\AOSService\PackagesLocalDirectory folder
    
    b. Navigate to the descriptor folder e.g. \Currency\Descriptor
    
    c. Open the XML file e.g. Currency.xml
    
    d. Add a "Customization" metadata element inside the "AxModelInfo" metadata element to indicate AllowAndWarn so that the start of the file now looks like this:
        
```xml
<AxModelInfo xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
<AppliedUpdates xmlns:d2p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
<Customization>AllowAndWarn</Customization>
```
    
4. Refactor over-layering to extensions and test - Make use of extension capabilities to eliminate over-layering. If needed, make extensibility requests.
5. Revert the temporary changes to Microsoft models - Deployment of a model that uses over-layering will not be possible, so ensure that the descriptor file is updated.
 
## Prototyping extensibility requests ##
As a solution is gradually migrated toward extensions, there will be places where an extensibility request is required to unblock the solution. To help understand exactly what is needed to unblock a solution and smooth the migration process toward extensions, extension capabilities can be prototyped in a separate model.

1. Identify the need for an extension capability to refactor some over-layering.
2. Add a prototype of extension capabilities into an extension prototype model.

		a. For enumeration extensibility, put a copy of the enumeration into the extension prototype model and mark it as extensible.
    
		b. For extract method extensibility, prototype the extracted method and the overlayered original in the extension prototype model.

3. Use the prototype extension capability.
4. If the prototype extension capability is sufficient, then create a matching request.
5. When the extension capability has been implemented in the platform or application, then the prototype extension capability and any associated over-layering should be removed from the extension prototype model.
6. Once the solution has all over-layering refactored to extensions and the extension prototype model is empty, then the solution refactoring is complete.
