---
# required metadata

title: Use event-based data actions
description: This topic describes how to use event-based data actions. 
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
ms.dyn365.ops.version: 

---
# Use event-based data actions

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to use event-based data actions.

## Overview

In some scenarios you don't need a data action to run on the initial load of a page, but instead want it to run dynamically in response to some event on the client. Examples of such scenarios include adding a product to a customers cart in response to a button click, displaying search results in response to a text input change, or updating banner text because of a time-based event.

## Example

In the following example, a very basic module loads product information in response to a user clicking a button. 

First we show a react component that contains a button for a user to click.

```tsx
// product-button.tsx
import * as React from 'react';

/**
 * ProductAddToCart component
 */
class ProductButton extends React.Component {
    public render(): JSX.Element {
        return (
            <div>
                <button onClick={_getProductInfo}>Get Product Info!</button>
            </div>
        );
    }

    // On-Click handler function
    private _getProductInfo = () => {
        console.log('We need to get the product!');
    }
}

export default ProductButton;
```

Currently this component will just log a message to the console when the button is clicked. To replace that with the data action, we need to do three things:

- Import the data action and its input class
- Create an input for the data action
- Invoke the data action

The following code shows an updated react component that will now make a call for a product when the button is clicked.

```tsx
// product-button.tsx
import * as React from 'react';

// Import our data action and input class
// NOTE: Generally the data action is the DEFAULT export of the file it was written in.
import getProductDataAction, { ProductInput } from '../../actions/get-product';

/**
 * ProductAddToCart component
 */
class ProductButton extends React.Component {
    public render(): JSX.Element {
        return (
            <div>
                <button onClick={_getProductInfo}>Get Product Info!</button>
            </div>
        );
    }

    // On-click handler
    private _getProductInfo = async() => {
        // Create the input for our data-action
        const actionInput = new ProductInput('12345');
        
        // Run and await the result of the data action
        const product = await getProductDataAction(actionInput, {callerContext: this.props.context.actionContext});
        
        // Log the result to the console
        console.log(product);
    }
}

export default ProductButton;
```

[!NOTE] This example uses a hardcoded `productId`, but could be updated to read the `productId` from a text input or from the module's configuration properties.
