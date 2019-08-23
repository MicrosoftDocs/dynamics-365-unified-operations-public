---
# required metadata

title: Data actions
description: Data Actions are JavaScript functions that are used within the Dynamics 365 Commerce e-Commerce architecture to facilitate the fetching and mapping of data needed by modules across your application.
author: SamJarawan
manager: JeffBl
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: SamJar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---
# Data actions

Data actions are JavaScript functions that are used within the Dynamics 365 Commerce e-Commerce architecture to facilitate the fetching and mapping of data needed by modules across your application.

Data Actions offer improved performance with:

1. Integrated app-level and request-level caches, enabling state-sharing scenarios
2. Built-in utilities to support batching to minimize external requests required by your application
3. Automatic de-duplication to ensure multiple data action calls are not duplicated

The Dynamics 365 Commerce platform includes a set of core Data Actions that can be called from your module to perform common retail data retrieval such as returning product details or custom Data Actions can be created to fetch and process data needed by your modules.


## Creating a new custom Data Action

To create a new data action:
1. Open a command prompt and navigate to your Dynamics 365 Commerce extensibility code directory.  For our example below we are using `c:\repos\myEcommerce`.
1. run the `yarn msdyn365 add-data-action DATA_ACTION_NAME` CLI command to create a new module, example:
    ```
    c:\repos\myEcommerceSite>yarn msdyn365 add-data-action getProductReviews
    ```
You will find a new typescript Data Action file created under the `\src\actions\` directory with the name of the data action.  In the example above we would have a new file: `\src\actions\getProductReviews.ts`.

## Anatomy of a Data Action

Below is the template typescript file that is created for a new data action.

```Typescript
/*---------------------------------------------------------------------------------------------
 *  Copyright (c) Microsoft Corporation. All rights reserved.
 *  Licensed under the MIT License. See License.txt in the project root for license information.
 *--------------------------------------------------------------------------------------------*/

import * as Msdyn365 from '@msdyn365-commerce/core';

/**
 * GetProductReviews Input Action
 */

export class GetProductReviewsInput extends Msdyn365.CommerceEntityInput implements Msdyn365.IActionInput {

    // TODO: Determine if the results of this get action should cache the results and if so provide
    // a cache object type and an appropriate cache key
    constructor() {
        super({shouldCacheOutput: true, cacheObjectType: 'TODO', cacheKey: 'TODO'});
    }

    public getCacheKey = () => `TODO`;
    public getCacheObjectType = () => 'TODO';
    public dataCacheType = (): Msdyn365.CacheType => 'application';
}

// TODO: Create a data model here or import one to capture the response of the action
export interface IGetProductReviewsData {
    text: string;
}

/**
 * TODO: Use this function to create the input required to make the action call
 */
const createInput = (args: Msdyn365.ICreateActionContext): Msdyn365.IActionInput => {
    return new GetProductReviewsInput();
};

/**
 * TODO: Use this function to call your action and process the results as needed
 */
async function action(input:GetProductReviewsInput, ctx: Msdyn365.IActionContext):Promise<IGetProductReviewsData> {
    // const apiSettings = Msdyn365.msdyn365Commerce.apiSettings;

    // TODO: Uncomment the below line to get the value from a service
    // const response = await Msdyn365.sendRequest<IGetProductReviewsData[]>('/get/example/id/1', 'get');
    return {text: 'Static data from action'};
}

export const IGetProductReviewsAction =  Msdyn365.createObservableDataAction({
    action: <Msdyn365.IAction<IGetProductReviewsData>>action,
    input: createInput
});
```
### Key parts of a Data Action
* The "Action" function

This is the main function that contains the logic to execute when the action is called. This may include making API calls, reading cookies, or transforming passed in data.
```Typescript
async function action(input:GetProductReviewsInput, ctx: Msdyn365.IActionContext):Promise<IGetProductReviewsData> {
    // const apiSettings = Msdyn365.msdyn365Commerce.apiSettings;

    // TODO: Uncomment the below line to get the value from a service
    // const response = await Msdyn365.sendRequest<IGetProductReviewsData[]>('/get/example/id/1', 'get');
    return {text: 'Static data from action'};
}

// TODO: Create a data model here or import one to capture the response of the action
export interface IGetProductReviewsData {
    text: string;
}
```

* The "Action" input

This class is used to pass data into the action function. The "cacheObjectType" and "cacheKey" are used to indicate where in the cache it should put the result of your action.
```Typescript
export class GetProductReviewsInput extends Msdyn365.CommerceEntityInput implements Msdyn365.IActionInput {

    // TODO: Determine if the results of this get action should cache the results and if so provide
    // a cache object type and an appropriate cache key
    constructor() {
        super({shouldCacheOutput: true, cacheObjectType: 'TODO', cacheKey: 'TODO'});
    }

    public getCacheKey = () => `TODO`;
    public getCacheObjectType = () => 'TODO';
    public dataCacheType = (): Msdyn365.CacheType => 'application';
}
```

* The createInput method

This is an optional method that you can create which is used to build an instance of you Action Input for use on loading data to initally populate your page. See Page Load Data Actions for more information.
```Typescript
const createInput = (args: Msdyn365.ICreateActionContext): Msdyn365.IActionInput => {
    return new GetProductReviewsInput();
};
```
