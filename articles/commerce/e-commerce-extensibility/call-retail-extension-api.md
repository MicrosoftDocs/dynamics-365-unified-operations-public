---
# required metadata

title: Call Retail Server Extension APIs
description: This topic explains how to call a Microsoft Dynamics 365 Retail Server extension API from a data action or directly from module code.
author: samjarawan
manager: annbe
ms.date: 10/25/2019
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
# Call Retail Server Extension APIs

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic explains how to call a Microsoft Dynamics 365 Retail Server extension API from a data action or directly from module code.

## Overview
You may have many Dynamics 365 Retail server extensions implemented and are calling them from the Dynamics 365 POS (Point of sale), these APIs can also be called from the e-Commerce modules and data actions.  To do this you will need to use a tool that is provided as part of the Dynamics 365 Retail SDK to create proxy module typescript files.  You can then include these files in your e-Commerce configurations and use them to call the Retail extension APIs from within your e-Commerce module and/or data actions.

Note: this guide will not cover the details of building a Retail see the following docs for more details: [Create a Retail Server Extension](https://docs.microsoft.com/en-us/dynamics365/retail/dev-itpro/retail-server-extension).

As a pre-requistite we are assuming you have a retail extension already deployed and have access to the Retail extension DLLs available. Also ensure your .env file `MSDyn365Commerce_BASEURL` is pointing to the environment that has the deployed Retail extension to test against it.  Mocks can also be used if this is not available.

## Creating Proxy files
Retail extensions can be called from Retail POS (Point of sale) by following the instructions here: [Typescript Proxies for Retail POS](https://docs.microsoft.com/en-us/dynamics365/retail/dev-itpro/typescript-proxy-retail-pos).

The above instructions will have you create a proxy using similar command as below:
 
```C:\RetailSDK\SourceCode\RetailSDK\Code\References\CommerceProxyGenerator.10.9.19281.3\tools>
CommerceProxyGenerator.exe e:\NewSDK\RetailSDK\Code\References\Microsoft.Dynamics.Retail.Proxies.ExtensionsGenerator.9.18.19315.4\build\Microsoft.Dynamics.Retail.RetailServerLibrary.dll e:\NewSDK\RetailSDK\Code\References\RetailServer.Extensions.WarrantySample.dll /application:typescriptextensions
```

Note the SDK version above may be different depending on the version of Retail Server you are running.

Creating proxy files for e-Commerce is identical to above except replace the final option **/application:typescriptextensions** with **/application:typescriptmoduleextensions**.

Example
```
C:\RetailSDK\SourceCode\RetailSDK\Code\References\CommerceProxyGenerator.10.9.19281.3\tools>
CommerceProxyGenerator.exe e:\NewSDK\RetailSDK\Code\References\Microsoft.Dynamics.Retail.Proxies.ExtensionsGenerator.9.18.19315.4\build\Microsoft.Dynamics.Retail.RetailServerLibrary.dll e:\NewSDK\RetailSDK\Code\References\RetailServer.Extensions.WarrantySample.dll /application:typescriptmoduleextensions
```
Once you have run the above command, 2 new files will be generated `DataActionExtension.g.ts` and `DataServiceEntities.g.ts`.

## Create a new data action 
From within the Dynamics 365 online SDK, include the 2 new files created above in the `/src/actions/` directory.  Then create a new data action ts file and copy similar code as below to call the Retail extension api from within the data action.  The below example is using a file called get-warranty-info.ts.  Notice how it is importing the `DataActionExtension.g` and `DataServiceEntities.g` files created above and calling the Retail extension API **createGetWarrantyByProductIdInput**.

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

Now we can call the data action just like we call any other by declaring it in the *dataActions* node in our module.definition.json file.  Below is an example.

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

We also need to add the return data type to the module data.ts file.  Below is an example.

```typescript
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';
import { IProductWarranty } from '../../actions/DataServiceEntities.g';

export interface IWarrantylistData {
    productWarranties: AsyncResult<IProductWarranty[]>;
}
```

Finally we can access the data from within our module React component using this.props.data.productWarranties property.





