---
# required metadata

title: Event based data actions
description: In some scenarios you don't need a Data Action to run on the inital load of a page, but instead you want them to run dynamically in response to some event on the client. This could be adding a product to a customers cart in response to a button click, displaying search results in response to a text input changing, or updating banner text because of a time-based event. 
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
# Event based data actions

In some scenarios you don't need a Data Action to run on the inital load of a page, but instead you want them to run dynamically in response to some event on the client. This could be adding a product to a customers cart in response to a button click, displaying search results in response to a text input changing, or updating banner text because of a time-based event. 

## Example
In this example, we will use a very basic module that will load product information in response to a user clicking a button. To start, lets show an example react component which contains a button for a user to click:

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
    private _getProductInfo() {
        console.log('We need to get the product!');
    }
}

export default ProductButton;
```

Currently this component will just log a message to the console when the button is clicked, to replace that with our data action, we need to do three things:

1. Import the data action and it's Input Class
2. Create an input for the data action
3. Invoke the data action

Here is an updated React component which will now make a call for a product when the button is clicked:

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
    private async _getProductInfo() {
        // Create the input for our data-action
        const actionInput = new ProductInput('12345');
        
        // Run and await the result of the data action
        const product = await getProductDataAction(actionInput, this.props.context.actionContext);
        
        // Log the result to the console
        console.log(product);
    }
}

export default ProductButton;
```

Note: This example uses a hardcoded `productId`, but could be updated to read the `productId` from a text input or from the modules configuration properties.
