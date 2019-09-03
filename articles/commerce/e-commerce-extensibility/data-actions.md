---
# required metadata

title: Data actions
description: This topic covers data actions in Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Data actions

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers data actions in Dynamics 365 Commerce.

## Overview

Data actions are JavaScript functions that are used within the Commerce architecture to facilitate the fetching and mapping of data needed by modules across applications.

Data actions offer improved performance with:

- Integrated app-level and request-level caches, enabling state-sharing scenarios.
- Built-in utilities that support batching to minimize external requests required by your application.
- Automatic de-duplication to ensure multiple data action calls are not duplicated.

The Commerce platform includes a set of core data actions that can be called from modules to perform common retail data retrieval such as returning product details. Also, you can create custom data actions to fetch and process data needed by modules.

## Anatomy of a data action

A template TypeScript file that is created for a new data action looks like the following example.

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
### Key parts of a data action

* The "Action" function

The "Action" function is the main function that contains the logic that executes when the action is called. This may include making API calls, reading cookies, or transforming passed-in data.

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

The "Action" input class is used to pass data into the action function. The "cacheObjectType" and "cacheKey" values indicate where in the cache it should put the result of the action.

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

The optional createInput method can be employed to build an instance of an action input that is used to load data when initially populating a page. See [Page Load Data Actions](TBD) for more information.

```Typescript
const createInput = (args: Msdyn365.ICreateActionContext): Msdyn365.IActionInput => {
    return new GetProductReviewsInput();
};
```
## Create a new custom data action

To create a new custom data action, do the following.

1. Open a command prompt and navigate to your Commerce extensibility code directory. For the example below we are using `c:\repos\myEcommerce`.
1. Run the `yarn msdyn365 add-data-action DATA_ACTION_NAME` command-line interface (CLI) command to create a new module, as in the following example.
    ```
    c:\repos\myEcommerceSite>yarn msdyn365 add-data-action getProductReviews
    ```
New TypeScript custom data action files are created under the `\src\actions\` directory using the name of the data action. For the example above, the new custom data action file path and name would be `\src\actions\getProductReviews.ts`.
