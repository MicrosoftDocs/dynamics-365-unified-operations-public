---
title: Relax model restrictions to refactor overlayering into extensions
description: Learn about relaxing model restrictions to enable the refactoring of over-layering into extensions, including a detailed process.
author: CGarty
ms.author: CGarty
ms.topic: article
ms.date: 05/01/2018
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-04-01
ms.dyn365.ops.version: Platform update 14
---

# Relax model restrictions to refactor overlayering into extensions

[!include [banner](../includes/banner.md)]

Development tools for finance and operations apps, starting with version 8.0, do not allow Microsoft code to be customized by using over-layering. Instead, extension capabilities should be used to modify and add behavior. The "no over-layering" restriction is a key part of the evolution of the product toward providing customers with a cloud service that is simple to update and always running the most recent version possible to allow all customers to receive the benefits of the latest features and fixes.

After you upgrade code from Dynamics AX 2012 or from Dynamics 365 for Finance and Operations version 7, any customizations that still use over-layering will cause errors when you compile your code. To refactor the code, the over-layering restriction can be temporarily relaxed in the model descriptor file of the model that is being over-layered. This temporary relaxation only works on development and demo environments and cannot be deployed on runtime environments like Standard Acceptance Test (or higher) sandbox or production environments. Relaxing the descriptor restriction will enable the code to be gradually refactored to extensions, compiled, run, and then tested. 

## Detailed process
Complete the following steps to relax model restrictions. This procedure can be completed on a cloud environment or a local virtual machine (VM).

1. Deploy the development environment for the finance and operations app. 
2. Run the Lifecycle Services (LCS) code upgrade service to upgrade the solution.
3. Temporarily allow over-layering in Microsoft models as needed to enable compilation.
    
    a. Locate the desired model within the C:\AOSService\PackagesLocalDirectory folder.
    
    b. Navigate to the descriptor folder. For example, \Currency\Descriptor.
    
    c. Open the XML file. For example, Currency.xml.
    
    d. Add a **Customization** metadata element inside the **AxModelInfo** metadata element to indicate **AllowAndWarn** so that the start of the file now looks like this.
            
    ```xml
    <AxModelInfo xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
    <AppliedUpdates xmlns:d2p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
    <Customization>AllowAndWarn</Customization>
    ```
    
4. Refactor over-layering to extensions and test. Make use of extension capabilities to eliminate over-layering. If needed, make extensibility requests.
5. Revert the temporary changes to Microsoft models. The deployment of a model that uses over-layering will not be possible, so it's important to ensure that the descriptor file is updated.
 
## Prototyping extensibility requests
As a solution gradually migrates toward extensions, there will be places where an extensibility request is required to unblock the solution. To fully understand what is needed to unblock a solution and smooth the migration process toward extensions, extension capabilities can be prototyped in a separate model.

1. Identify the need for an extension capability to refactor some over-layering.
2. Add a prototype of extension capabilities into an extension prototype model.

   - For enumeration extensibility, put a copy of the enumeration into the extension prototype model and mark it as extensible.
    
   - For extract method extensibility, prototype the extracted method and the overlayered original in the extension prototype model.
    
3. Use the prototype extension capability.
4. If the prototype extension capability is sufficient, create a matching request.
5. When the extension capability has been implemented in the platform or application, the prototype extension capability and any associated over-layering should be removed from the extension prototype model.
6. After the solution has all over-layering refactored to extensions and the extension prototype model is empty, the solution refactoring is complete.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
