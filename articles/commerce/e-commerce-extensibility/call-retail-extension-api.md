---
# required metadata

title: Call Retail Server extension APIs
description: This topic describes how to call Microsoft Dynamics 365 Retail Server extension API from data actions or directly from module code.
author: samjarawan
manager: annbe
ms.date: 01/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2020-01-22
ms.dyn365.ops.version: Release 10.0.8

---
# Call Retail Server extension APIs

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to call Microsoft Dynamics 365 Retail Server extension APIs from data actions or directly from module code.

## Overview

Dynamics 365 Retail Server extensions APIs are usually implemented and called from the Dynamics 365 Retail's Point of Sale (POS) system, but these APIs can also be called from e-Commerce modules and data actions. To do this, you will need to use a tool to create proxy module typescript files that is provided as part of the Dynamics 365 Retail software develpment kit (SDK). You can then include these files in your e-Commerce configurations and use them to call the Retail Server extension APIs from within e-Commerce module or data actions.

> [!NOTE]
> This topic does not cover the details of creating a Retail Server extension, for more information see [Create a new Retail Server extension](https://docs.microsoft.com/en-us/dynamics365/retail/dev-itpro/retail-server-extension).

As a prerequisite, it is assumed that you already have a retail extension already deployed and have access to the Retail extension DLLs that are available. In addition, ensure that your .env file `MSDyn365Commerce_BASEURL` is pointing to the environment that has the deployed Retail extension, so you can test against it. Mocks can also be used if this option is not available.

## Create proxy files

Retail extensions can be called from Retail POS by following the instructions here: [Typescript and C# proxies for Retail point of sale (POS)](https://docs.microsoft.com/en-us/dynamics365/retail/dev-itpro/typescript-proxy-retail-pos).

These instructions describe how to create a proxy using a command similar to the following:
 
```C:\RetailSDK\SourceCode\RetailSDK\Code\References\CommerceProxyGenerator.10.9.19281.3\tools>
CommerceProxyGenerator.exe e:\NewSDK\RetailSDK\Code\References\Microsoft.Dynamics.Retail.Proxies.ExtensionsGenerator.9.18.19315.4\build\Microsoft.Dynamics.Retail.RetailServerLibrary.dll e:\NewSDK\RetailSDK\Code\References\RetailServer.Extensions.WarrantySample.dll /application:typescriptextensions
```

> [!NOTE]
> The SDK version referenced above may differ, depending on the version of Retail Server you are running.

Creating proxy files for e-Commerce is similar to the process above, with the exception of replacing the final option **/application:typescriptextensions** with **/application:typescriptmoduleextensions**, as in the following example.

```
C:\RetailSDK\SourceCode\RetailSDK\Code\References\CommerceProxyGenerator.10.9.19281.3\tools>
CommerceProxyGenerator.exe e:\NewSDK\RetailSDK\Code\References\Microsoft.Dynamics.Retail.Proxies.ExtensionsGenerator.9.18.19315.4\build\Microsoft.Dynamics.Retail.RetailServerLibrary.dll e:\NewSDK\RetailSDK\Code\References\RetailServer.Extensions.WarrantySample.dll /application:typescriptmoduleextensions
```
Once you have run the command above, two new files will be generated: `DataActionExtension.g.ts` and `DataServiceEntities.g.ts`.

## Create a new data action

From within the Dynamics 365 Commerce online SDK, include the two new files created above in the `/src/actions/` directory. Then create a new data action .ts file and copy code similar to that in the example below to call the Retail extension API from within the data action. 

The following example uses a file called **get-warranty-info.ts**. Notice how it is importing the `DataActionExtension.g` and `DataServiceEntities.g` files created above and calling the Retail extension API **createGetWarrantyByProductIdInput**.

```typescript
import { createObservableDataAction, IAction, ICreateActionContext } from '@msdyn365-commerce/core';
import { retailAction } from '@msdyn365-commerce/retail-proxy';
import { createGetWarrantyByProductIdInput } from './DataActionExtension.g';
import { IProductWarranty } from './DataServiceEntities.g';

/**
 * Get Org Unit Configuration Data Action
 */
export default createObservableDataAction({
    action: <IAction<IProductWarranty[]>>retailAction,
    input: (context: ICreateActionContext) => {
        return createGetWarrantyByProductIdInput({ Paging: { Top: 250 } }, '12345');
    }
});
```

Now we can call the data action like any other by declaring it in the **dataActions** node of our module.definition.json file, as in the following example.

```json
{
    "$type": "contentModule",
    "friendlyName": "Warranty List",
    "name": "warrantylist",
    "description": "Provides a list of available warranty services available for purchase.",
    "categories": [
        "warranty"
    ],
    "tags": [
        ""
    ],
    "dataActions": {
        "productWarranties": {
            "path": "../../actions/get-warranty-info",
            "runOn": "server"
        }
    },
    "resources": {
        "warrantyName": {
            "value": "Warranty Name",
            "comment": "Text for the warranty name header"
        },
        "warrantyDescription": {
            "value": "Description",
            "comment": "Text for the warranty description header"
        },
        "warrantyPrice": {
            "value": "Price",
            "comment": "Text for the warranty price header"
        },
        "warrantyBuyButton": {
            "value": "Buy now",
            "comment": "Text for the warranty action button"
        }
    }
}
```

We also need to add the return data type to the module data.ts file, as in the following example.

```typescript
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';
import { IProductWarranty } from '../../actions/DataServiceEntities.g';

export interface IWarrantylistData {
    productWarranties: AsyncResult<IProductWarranty[]>;
}
```

Finally we can access the data from within our module React component using the **this.props.data.productWarranties** property.

## Additional resources



