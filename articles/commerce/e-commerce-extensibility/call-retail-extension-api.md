---
# required metadata

title: Call Retail Server extension APIs
description: This topic describes how to call Microsoft Dynamics 365 Retail Server extension APIs from data actions or directly from module code.
author: samjarawan
manager: annbe
ms.date: 01/31/2020
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

[!include [banner](../includes/banner.md)]

This topic describes how to call Microsoft Dynamics 365 Retail Server extension application programming interfaces (APIs) from data actions or directly from module code.

## Overview

Dynamics 365 Retail Server extension APIs are usually implemented and called from the point of sale (POS) system. However, they can also be called from e-Commerce modules and data actions. To call the APIs in this way, you must create proxy module TypeScript (.ts) files by using a tool that is provided as part of the Dynamics 365 Retail software development kit (SDK). You can then include these files in your e-Commerce configurations and use them to call the Retail Server extension APIs from e-Commerce modules and data actions.

> [!NOTE]
> This topic doesn't explain how to create Retail Server extensions. For more information, see [Create a new Retail Server extension](https://docs.microsoft.com/dynamics365/retail/dev-itpro/retail-server-extension).

It's assumed that the following prerequisites are in place:

- A Retail extension has already been deployed.
- You have access to the Retail extension dynamic-link libraries (DLLs) that are available.

In addition, make sure that your .env file's **MSDyn365Commerce\_BASEURL** value points to the environment that has the deployed Retail extension, so that you can test against it. If this option isn't available, you can use mocks instead.

## Create proxy files

For information about how Retail extensions can be called from Retail POS, see [Typescript and C# proxies for Retail point of sale (POS)](https://docs.microsoft.com/dynamics365/retail/dev-itpro/typescript-proxy-retail-pos). That topic explain how to create a proxy file by using a command that resembles the following command.
 
```
C:\RetailSDK\SourceCode\RetailSDK\Code\References\CommerceProxyGenerator.10.9.19281.3\tools>
CommerceProxyGenerator.exe e:\NewSDK\RetailSDK\Code\References\Microsoft.Dynamics.Retail.Proxies.ExtensionsGenerator.9.18.19315.4\build\Microsoft.Dynamics.Retail.RetailServerLibrary.dll e:\NewSDK\RetailSDK\Code\References\RetailServer.Extensions.WarrantySample.dll /application:typescriptextensions
```

> [!NOTE]
> The SDK version that is referenced in the command might differ, depending on the version of Retail Server that you're running.

The process for creating proxy files for e-Commerce is similar, but the final **/application:typescriptextensions** option is replaced by **/application:typescriptmoduleextensions**, as shown in the following example.

```
C:\RetailSDK\SourceCode\RetailSDK\Code\References\CommerceProxyGenerator.10.9.19281.3\tools>
CommerceProxyGenerator.exe e:\NewSDK\RetailSDK\Code\References\Microsoft.Dynamics.Retail.Proxies.ExtensionsGenerator.9.18.19315.4\build\Microsoft.Dynamics.Retail.RetailServerLibrary.dll e:\NewSDK\RetailSDK\Code\References\RetailServer.Extensions.WarrantySample.dll /application:typescriptmoduleextensions
```

After you run the preceding command, two new files are generated: **DataActionExtension.g.ts** and **DataServiceEntities.g.ts**.

## Create a new data action

From the Dynamics 365 Commerce online SDK, include the two new files from the previous section in the **/src/actions/** directory. Then create a new data action .ts file, and paste in code that resembles the following example to call the Retail extension APIs from the data action. 

The following example uses a file that is named get-warranty-info.ts. Notice that it imports the DataActionExtension.g and DataServiceEntities.g files that were generated earlier, and it calls the **createGetWarrantyByProductIdInput** Retail extension API.

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

You can now call the data action just as you might call any other data action, by declaring it in the **dataActions** node of your module.definition.json file, as shown in the following example.

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

You must also add the return data type to the module's data.ts file, as shown in the following example.

```typescript
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';
import { IProductWarranty } from '../../actions/DataServiceEntities.g';

export interface IWarrantylistData {
    productWarranties: AsyncResult<IProductWarranty[]>;
}
```

Finally, you can access the data from your module React component by using the **this.props.data.productWarranties** property.

## Additional resources

[Data actions overview](data-actions.md)

[Test data actions with mocks](test-data-action-mocks.md)

[Page load data actions](page-load-data-action.md)

[Event-based data actions](event-based-data-actions.md)

[Core data actions](core-data-actions.md)
