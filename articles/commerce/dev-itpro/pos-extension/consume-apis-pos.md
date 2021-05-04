---
# required metadata

title: POS Extensibility basics
description: This topic explains how to Consume Custom Headless Commerce Engine APIs and Entities in POS using Proxy.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18

---

# Consume Custom Headless Commerce Engine APIs and Entities in POS

[!include [banner](../../../includes/banner.md)]

This topic explains how to Consume Custom Headless Commerce Engine APIs and Entities in POS using Proxy, this topic applies to Retail software development kit (SDK) version 10.0.18 and later.

1.	Ensure that your Commerce Runtime extension project is referencing the Microsoft.Dynamics.Commerce.Sdk.Runtime Nuget package and that your POS extension project is referencing the Microsoft.Dynamics.Commerce.Sdk.Pos Nuget package.
2.	Add a project reference from your POS extension project to the Commerce Runtime project that defines your APIs.
3.	Build your POS extension project to generate the TypeScript Entities and DataServiceRequests for your Headless Commerce Engine extensions
    
    + This will generate two TypeScript files in a folder named DataService in your project root.
        + **DataServiceEntities.g.ts** – Contains the TypeScript entities for all the referenced Commerce Runtime extension projects.
        + **DataServiceRequests.g.ts** – Contains the TypeScript DataServiceRequests for all the referenced Commerce Runtime extension projects.
4.	Import your data service entities and requests in your extensions code as shown in the snippet below.

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
