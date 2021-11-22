---
title: Consume custom headless Commerce APIs and entities in POS
description: This topic explains how to use Proxy to consume custom headless Commerce APIs and entities in Point of Sale (POS).
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18
---

# Consume custom headless Commerce APIs and entities in POS

[!include [banner](../../../includes/banner.md)]

This topic explains how to use Proxy to consume custom headless Commerce APIs and entities in Point of Sale (POS). It applies to version 10.0.18 and later of the Retail software development kit (SDK).

1. Make sure that your Commerce runtime (CRT) extension project references the **Microsoft.Dynamics.Commerce.Sdk.Runtime** NuGet package, and that your POS extension project references the **Microsoft.Dynamics.Commerce.Sdk.Pos** NuGet package.
2. Add a project reference from your POS extension project to the CRT project that defines your APIs.
3. Build your POS extension project to generate the TypeScript for your headless Commerce extensions. The build generates two TypeScript files in a **DataService** folder in your project root:

    + **DataServiceEntities.g.ts** – This file contains the TypeScript entities for all the referenced CRT extension projects.
    + **DataServiceRequests.g.ts** – This file contains the TypeScript data service requests for all the referenced CRT extension projects.

4. Import your data service entities and requests into your extension code, as shown in the following example.

    ```Javascript
    import * as Triggers from "PosApi/Extend/Triggers/ProductTriggers";
    import { ObjectExtensions } from "PosApi/TypeExtensions";
    import { ClientEntities } from "PosApi/Entities";
    import { StoreHours } from "../DataService/DataService.g"
    
    export default class PreProductSaleTrigger extends Triggers.PreProductSaleTrigger {
        /**
         * Executes the trigger functionality.
         * @param {Triggers.IPreProductSaleTriggerOptions} options The options provided to the trigger.
         */
        public execute(options: Triggers.IPreProductSaleTriggerOptions): Promise<ClientEntities.ICancelable> {
            if (ObjectExtensions.isNullOrUndefined(options)) {
                // This will never happen, but is included to demonstrate how to return a rejected promise when validation fails.
                let error: ClientEntities.ExtensionError
                    = new ClientEntities.ExtensionError("The options provided to the PreProductSaleTrigger were invalid. Please select a product and try again.");
                return Promise.reject(error);
            } else {
                return this._context.runtime.executeAsync(new StoreHours.GetStoreDaysByStoreRequest<StoreHours.GetStoreDaysByStoreResponse>(0));
            }
        }
    }
    ```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
