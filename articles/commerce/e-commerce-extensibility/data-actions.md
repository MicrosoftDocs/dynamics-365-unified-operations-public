---
title: Data actions
description: This article covers data actions in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 08/01/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Data actions

[!include [banner](../includes/banner.md)]

This article covers data actions in Microsoft Dynamics 365 Commerce.

Data actions are JavaScript functions that are used in the Dynamics 365 Commerce architecture to help fetch and map data that is required by modules across applications.

Data actions offer improved performance through the following features:

- Integrated application-level and request-level caches enable state sharing scenarios.
- Built-in utilities support batching to minimize the number of external requests that your application requires.
- Automatic deduplication helps guarantee that multiple data action calls aren't duplicated.

The Dynamics 365 Commerce platform includes a set of core data actions that can be called from modules to do typical data retrieval. For example, core data actions can return product details. You can also create custom data actions to fetch and process data that is required by modules.

## Anatomy of a data action

Here is an example of a template TypeScript file that is created for a new data action.

```typescript
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

* **Action function** – The main function that contains the logic that is run when the action is called. This function might involve making application programming interface (API) calls, reading cookies, or transforming data that was passed in.

    ```typescript
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

* **Action input class** – The class that is used to pass data into the action function. The **"cacheObjectType"** and **"cacheKey"** values indicate where in the cache the class should put the result of the action.

    ```typescript
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

* **createInput method** – This optional method can be used to build an instance of an action input class that is used to load data when a page is first populated. 

    ```typescript
    const createInput = (args: Msdyn365.ICreateActionContext): Msdyn365.IActionInput => {
        return new GetProductReviewsInput();
    };
    ```

### Create a new custom data action

To create a new custom data action, follow this step.

- At a command prompt, go to your root software development kit (SDK) folder, and run the **yarn msdyn365 add-data-action DATA\_ACTION\_NAME** command-line interface (CLI) command to create a data action, as shown in the following example.

    ```Console
    c:\repos\Msdyn365.Commerce.Online>yarn msdyn365 add-data-action get-product-reviews
    ```

TypeScript files for new custom data actions are created under the \\src\\actions\\ directory. The name of each file uses the name of the data action. For the preceding example, the path and name of the file for the new custom data action are **\\src\\actions\\getProductReviews.ts**.

## Additional resources

[Data action cache options](data-action-cache.md)

[Test data actions with mocks](test-data-action-mocks.md)

[Page load data actions](page-load-data-action.md)

[Event-based data actions](event-based-data-actions.md)

[Core data actions](core-data-actions.md)

[Call Retail Server APIs](call-retail-server-apis.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
