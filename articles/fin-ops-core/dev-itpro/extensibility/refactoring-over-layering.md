---
title: Relax model restrictions to refactor overlayering into extensions
description: Learn about relaxing model restrictions to enable the refactoring of over-layering into extensions, including a detailed process.
author: CGarty
ms.author: CGarty
ms.topic: how-to
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-04-01
ms.dyn365.ops.version: Platform update 14
---

# Relax model restrictions to refactor overlayering into extensions

[!include [banner](../includes/banner.md)]

Starting with version 8.0, development tools for finance and operations apps don't allow customization of Microsoft code by using overlayering. Instead, use extension capabilities to modify and add behavior. The "no overlayering" restriction is a key part of the product evolution toward providing customers with a cloud service that is simple to update and always running the most recent version possible to allow all customers to receive the benefits of the latest features and fixes.

After you upgrade code from Dynamics AX 2012 or from Dynamics 365 for Finance and Operations version 7, any customizations that still use overlayering cause errors when you compile your code. To refactor the code, you can temporarily relax the overlayering restriction in the model descriptor file of the model that you're overlayering. This temporary relaxation only works on development and demo environments and can't be deployed on runtime environments like Standard Acceptance Test (or higher) sandbox or production environments. When you relax the descriptor restriction, you can gradually refactor the code to use extensions, compile, run, and then test.

## Detailed process

Complete the following steps to relax model restrictions. You can complete this procedure on a cloud environment or a local virtual machine (VM).

1. Deploy the development environment for the finance and operations app.
1. Run the Lifecycle Services (LCS) code upgrade service to upgrade the solution.
1. Temporarily allow overlayering in Microsoft models as needed to enable compilation.

    a. Locate the desired model within the `C:\AOSService\PackagesLocalDirectory` folder.

    b. Go to the descriptor folder. For example, `\Currency\Descriptor`.

    c. Open the XML file. For example, `Currency.xml`.

    d. Add a **Customization** metadata element inside the **AxModelInfo** metadata element to indicate **AllowAndWarn** so that the start of the file now looks like this.

    ```xml
    <AxModelInfo xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
    <AppliedUpdates xmlns:d2p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
    <Customization>AllowAndWarn</Customization>
    ```

1. Refactor overlayering to extensions and test. Use extension capabilities to eliminate overlayering. If needed, make extensibility requests.
1. Revert the temporary changes to Microsoft models. You can't deploy a model that uses overlayering, so ensure that you update the descriptor file.

## Prototyping extensibility requests

As your solution gradually migrates toward extensions, you might encounter situations where you need an extensibility request to unblock the solution. To fully understand what you need to unblock a solution and smooth the migration process toward extensions, prototype extension capabilities in a separate model.

1. Identify the need for an extension capability to refactor some over-layering.
1. Add a prototype of extension capabilities into an extension prototype model.

   - For enumeration extensibility, put a copy of the enumeration into the extension prototype model and mark it as extensible.

   - For extract method extensibility, prototype the extracted method and the overlayered original in the extension prototype model.

1. Use the prototype extension capability.
1. If the prototype extension capability is sufficient, create a matching request.
1. When the extension capability is implemented in the platform or application, remove the prototype extension capability and any associated over-layering from the extension prototype model.
1. After the solution has all over-layering refactored to extensions and the extension prototype model is empty, the solution refactoring is complete.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
