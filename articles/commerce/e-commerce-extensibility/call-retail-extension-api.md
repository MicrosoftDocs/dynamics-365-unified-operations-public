---
title: Call Retail Server extension APIs
description: This article describes how to call Microsoft Dynamics 365 Retail Server extension APIs from data actions or directly from module code.
author: samjarawan
ms.date: 08/01/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-22
ms.custom: 
  - bap-template
---
# Call Retail Server extension APIs

[!include [banner](../includes/banner.md)]

This article describes how to call Microsoft Dynamics 365 Retail Server extension application programming interfaces (APIs) from data actions or directly from module code.

Dynamics 365 Retail Server extension APIs can be called from either the point of sale (POS) system or from e-Commerce modules and data actions. To call the APIs from e-Commerce modules and data actions, you must create proxy module TypeScript (.ts) files by using a tool that is provided as part of the Dynamics 365 Retail software development kit (SDK). You can then include these files in your e-Commerce configurations and use them to call the Retail Server extension APIs from e-Commerce modules and data actions.

> [!NOTE]
> This article doesn't explain how to create Retail Server extensions. For more information, see [Create a Retail Server extension API](../dev-itpro/retail-server-icontroller-extension.md).

It's assumed that the following prerequisites are in place:

- A Retail Server extension has already been deployed.
- You have access to the Retail Server extension dynamic-link libraries (DLLs) that are available.

In addition, make sure that the .env file **MSDyn365Commerce\_BASEURL** has a value that points to the environment that has the deployed Retail Server extension, so that you can test against it. If this option isn't available, you can use a mock-up instead.

If you're developing on the local Tier 1 Retail Server virtual machine (VM), you must point **MSDyn365Commerce\_BASEURL** to the local URL (`https://usnconeboxax1ret.cloud.onebox.dynamics.com/`), and make sure that **MSDyn365Commerce\_CHANNELID** and **MSDyn365Commerce\_OUN** are set to the appropriate online channel that you're using. Here is an example of an .env file.

```text
…
MSDyn365Commerce_BASEURL=https://usnconeboxax1ret.cloud.onebox.dynamics.com/
MSDyn365Commerce_CHANNELID=68719478279
MSDyn365Commerce_CATALOGID=0
MSDyn365Commerce_OUN=128
…
```
For more information, see [Configure a development environment (.env) file](configure-env-file.md).

You might also have to change the following setting in the Retail Server web.config file, so that the call can go through in the local development environment.

```code
<add key="AllowedOrigins" value="*" />
<!-- <add key="AllowedOrigins" value="https://usnconeboxax1pos.cloud.onebox.dynamics.com;https://usnconeboxax1ecom.cloud.onebox.dynamics.com" /> -->
```

## Create proxy files

You will need the Retail SDK to generate proxy files. If you are using a Tier 1 development VM environment, make sure that you have the latest Retail SDK installed. For more information, see [Migrate the Retail SDK from Visual Studio 2015 to Visual Studio 2017](../dev-itpro/retail-sdk/migrate-sdk.md).

For information about how Retail extensions can be called from Retail POS, see [Typescript and C# proxies for Retail point of sale (POS)](../dev-itpro/typescript-proxy-retail-pos.md). That article explains how to create a proxy file by using a command that resembles the following command.
 
```Console
K:\RetailSDK\References\microsoft.dynamics.commerce.tools.coreproxygenerator\10.14.20128.1\tools>CommerceProxyGenerator.exe ..\..\..\microsoft.dynamics.commerce.tools.extensionsproxygenerator\9.22.20167.4\tools\Microsoft.Dynamics.Retail.RetailServerLibrary.dll k:\WarrantySample\Contoso.RetailServer.WarrantySample.dll /application:typescriptextensions
```

> [!NOTE]
> The SDK version that is referenced in the command might differ, depending on the version of Retail Server that you're running.

The process for creating proxy files for e-Commerce is similar, but the final **/application:typescriptextensions** option is replaced by **/application:typescriptmoduleextensions**, as shown in the following example.

```Console
K:\RetailSDK\References\microsoft.dynamics.commerce.tools.coreproxygenerator\10.14.20128.1\tools>CommerceProxyGenerator.exe ..\..\..\microsoft.dynamics.commerce.tools.extensionsproxygenerator\9.22.20167.4\tools\Microsoft.Dynamics.Retail.RetailServerLibrary.dll k:\WarrantySample\Contoso.RetailServer.WarrantySample.dll /application:typescriptmoduleextensions
```

After you run the preceding command, two new files are generated: **DataActionExtension.g.ts** and **DataServiceEntities.g.ts**.

### Proxy data methods

The proxy is closely linked to the data action framework. For every Retail Server extension API, there are two exposed proxy methods:

- **createInput** – This method creates an **IActionInput** class that can be used either to run a page load data action, or to do a direct state update or fetch via the **actionContext.update()** or **actionContext.get()** methods. This method is always named **create{COMMERCE_SCALE_UNIT_EXTENSION_API_NAME}Input**.
- **action** – This method can be invoked on its own as an event-based data action, or it can be added inside another action method to create a data action chain. This method is always named **{RETAIL_SERVER_API_NAME}Async**.

## Call a proxy API with a data action

From the Dynamics 365 Commerce online SDK, include the two new files from the previous section in the **/src/actions/** directory. Then create a new data action .ts file, and paste in code that resembles the following example to call the Retail Server extension APIs from the data action. 

The following example uses a file that is named **get-warranty-info.ts**. Notice that it imports the **DataActionExtension.g** and **DataServiceEntities.g** files that were generated earlier, and it calls the **createGetWarrantyByProductIdInput** Retail Server extension API as defined in the proxy file.

```typescript
import { createObservableDataAction, IAction, ICreateActionContext } from '@msdyn365-commerce/core';
import { retailAction } from '@msdyn365-commerce/retail-proxy';
import { createGetWarrantyByProductIdInput } from './DataActionExtension.g';
import { IProductWarranty } from './DataServiceEntities.g';
/**
 * Get Warranty Info Data Action
 */
export default createObservableDataAction({
    action: <IAction<IProductWarranty[]>>retailAction,
    input: (context: ICreateActionContext) => {
        return createGetWarrantyByProductIdInput({Paging:{Top:250}}, '12345');
    }
});
```

You can now call the data action just as you might call any other data action, by declaring it in the **dataActions** node of your module.definition.json file, as shown in the following example. The data action will be called at page load time.

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

Finally, you can access the data from your module React component by using the **this.props.data.productWarranties** property. The following example shows a sample module view.tsx file that renders data coming back from the Retail Server extension API.

```typescript
import * as React from 'react';
import { IWarrantylistsampleViewProps } from './warrantylistsample';
export default (props: IWarrantylistsampleViewProps) => {
    const {
        data: { productWarranties }
    } = props;
    if (productWarranties && productWarranties.result) {
        return (
            <table className='table'>
                <thead>
                    <tr>
                        <th>Warranty</th>
                        <th>Price</th>
                    </tr>
                </thead>
                <tbody>
                    {productWarranties.result.map(warranty => (
                        <tr>
                            <td>{warranty.Description}</td>
                            <td>${warranty.Price}</td>
                            <button type='button' className='btn btn-primary'>Buy Now</button>
                        </tr>
                    ))}
                </tbody>
            </table>
        );
    } else {
        return <div>No warranty info returned</div>;
    };
};
```

## Call proxy APIs directly

The following example shows a Retail Server API being called directly inside of a module's typescript React view code without using a data action.

```
import * as React from 'react';
import { getWarrantyByProductIdAsync } from '../../actions/DataActionExtension.g';
import { IWarrantylistViewProps } from './warrantylist';
export default (props: IWarrantylistViewProps) => {
    const _getWarrantyOnClick = async() => {
        getWarrantyByProductIdAsync({ callerContext: props.context.actionContext }, '12345').then( result => {
           ...
        });
    }
    
    return (
        <div>
            <button onClick={_getWarrantyOnClick}>Get Warranty Info</button>
        </div>
    );    
};
```

## Additional resources

[Data actions overview](data-actions.md)

[Data action cache options](data-action-cache.md)

[Test data actions with mocks](test-data-action-mocks.md)

[Page load data actions](page-load-data-action.md)

[Event-based data actions](event-based-data-actions.md)

[Core data actions](core-data-actions.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
