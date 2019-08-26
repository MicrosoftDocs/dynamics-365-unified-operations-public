---
# required metadata

title: Batch data actions
description: This topic describes how to batch data actions.
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
# Batch data actions

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to batch data actions.

## Overview

In many scenarios you will have an application that requires many calls to the same API during the load of a single page. An example of this is a product feature page that showcases information about not just one, but many products. A typical solution would be to call the data action to get products multiple times resulting in many individual HTTP requests to get the product info, which may not be very efficient. To solve this problem, the data action architecture supports batchable data actions.

## Examples

The main difference between a batch data action and a standard data action is its support for an array of ActionInputs. Looking at an example action method inside a data action, you can see only a single `ProductInput` class is accepted.

```typescript
async function getSimpleProductAction(input: ProductInput, ctx: IActionContext): Promise<SimpleProduct>
```

If we wanted to turn this into a batch data action, we would update the method signature to the following.

```typescript
async function getSimpleProductsAction(inputs: ProductInput[], ctx: IActionContext): Promise<SimpleProduct[]>
```

Notice that we are expecting our action to receive an array of inputs and return an array of products back from our API. In order to support this, the action function needs to be updated.

```typescript
async function getSimpleProductsAction(inputs: ProductInput[], ctx: IActionContext): Promise<SimpleProduct[]> {
    const { apiSettings } = ctx.requestContext;

    // Construct our HTTP request using information available in actionContext (ctx), and our Action Input (input)
    const requestUrl = `${apiSettings.baseUrl}/Products`;

    // Construct our request context from all the passed inputs
    const requestBody = {
        productIds: inputs.map(input => input.productId);
    }

    // Get the SimpleProducts
    return sendCommerceRequest<SimpleProduct[]>(requestUrl, 'post', requestBody})
        .then((response: IHTTPResponse) => {

            if(response.data) {
                return response.data;
            }

            ctx.trace('[getSimpleProductsAction] Invalid response from server');
            return <SimpleProduct[]>[];
        })
        .catch((error: IHTTPError) => {
            ctx.trace(error.message);
            ctx.trace(error.stack || '');
            ctx.trace(`Unable to Fetch Products.`);
            return <SimpleProduct[]>[];
        });
    }
```

Now that the data action method has been updated to handle an array of inputs, we need to set the `isBatched` in the action creation call to true.

```typescript
export default createObservableDataAction({
    action: <IAction<SimpleProduct[]>>getSimpleProductsAction,
    input: createInput,
    isBatched: true
});
```

Since this action now supports batching, if this action is called in multiple places over the course of a page load, the data action framework will automatically group these requests together. This will minimize the amount of HTTP requests required and maximize performance.

[!NOTE]
Certain APIs may not support batching on their side, so when creating a batched data action confirm that the service you are using can support the action.
