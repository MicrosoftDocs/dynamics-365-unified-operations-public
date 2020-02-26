--
# required metadata

title: Data action overrides
description: This topic describes how to overrride default module data actions with custom data actions.
author: samjarawan
manager: annbe
ms.date: 02/20/2020
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
# Data action overrides

[!include [banner](../includes/banner.md)]

This topic describes how to overrride default module data actions with custom data actions.

## Overview

The set of modules included with the module library use pre-existing data actions to fetch data for the module to use.  There may be times when you want to have a module use a custom data action but do not want to clone the module since you won't be changing the UX rendered by the module but perhaps may want to alter the business logic in the data action.  With data action overrides, you can override the registered action by creating a new action with the same action id. Overriding a data action will cause all previous uses of the data action, either through import or inclusion in the module definition.json file, to use your new data action.

## ID naming convention
Each data action has a data action id. Which is assigned by the data action creator when createObservableDataAction is called through the "id" property. The id should follow the convention [package name]/[module name]/[action name]

```typescript
export default createObservableDataAction({
    id: '@msdyn365-commerce-modules/retail-actions/get-address',
    action: <IAction<Address[]>>getAddressAction,
    input: <(args: ICreateActionContext) => IActionInput>createGetAddressInput
});
```

## Example

To override the get-address data action you need to create a new data action that uses the get-address ID inside of the /src/actions folder.

The below command will create a new data action under the \src\actions directory.

```console
yarn msdyn365 add-data-action custom-get-address
```

Next replace the default template code with your code.  In the example below, note the data action **ID** is the same as used in the …\Msdyn365.Commerce.Online\node_modules\@msdyn365-commerce-modules\retail-actions\dist\lib\get-address.js data action **@msdyn365-commerce-modules/retail-actions/get-address**.

```typescript
import { CacheType, IAction, IActionContext, IActionInput, ICommerceApiSettings } from '@msdyn365-commerce/core';
import { createObservableDataAction, ICreateActionContext } from '@msdyn365-commerce/core';
import { Address } from '@msdyn365-commerce/retail-proxy';

import { readAsync } from '@msdyn365-commerce/retail-proxy/dist/DataActions/CustomersDataActions.g';

/**
 *  Input class for the getAddress data action
 */
export class AddressInput implements IActionInput {
    public userAccountNumber: string;
    private apiSettings: ICommerceApiSettings;

    constructor(userAccountNumber: string, apiSettings: ICommerceApiSettings) {
        this.userAccountNumber = userAccountNumber;
        this.apiSettings = apiSettings;
    }

    public getCacheKey = () => this.userAccountNumber
    public getCacheObjectType = () => 'GetAddress';
    public dataCacheType = (): CacheType => 'request';
}

/**
 * createInput method for the getAddress method
 * @param inputData The input data passed to the createInput method
 */
export const createGetAddressInput = (inputData: ICreateActionContext): IActionInput => {
    const { requestContext } = inputData;
    if (!requestContext.user.isAuthenticated || !requestContext.user.customerAccountNumber) {
        throw new Error('Unable to create address input.  User is not authenticated.');
    }

    return new AddressInput(requestContext.user.customerAccountNumber, inputData.requestContext.apiSettings);
};

/**
 * The action method for the getAddress data action
 * @param input The action input
 * @param ctx The action context
 */
export async function getAddressAction(input: AddressInput, ctx: IActionContext): Promise<Address[]> {

    const customer = await readAsync({ callerContext: ctx }, input.userAccountNumber);

    if (!customer) {
        throw new Error('Not able to get customer');
    }

    // fetch customer address from external source
    return customer.Addresses || [];
}

/**
 * The getAddress data action
 * Gets a customers information via the read RetailServer API
 * Returns address information associated with the retrieved customer
 */
export default createObservableDataAction<Address[]>({
    id: '@msdyn365-commerce-modules/retail-actions/get-address',
    action: <IAction<Address[]>>getAddressAction,
    input: <(args: ICreateActionContext) => IActionInput>createGetAddressInput
});
```


