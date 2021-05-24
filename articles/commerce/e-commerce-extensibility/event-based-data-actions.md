---
# required metadata

title: Use event-based data actions
description: This topic describes how to use event-based data actions. 
author: samjarawan
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
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

[!include [banner](../includes/banner.md)]

This topic describes how to use event-based data actions.

In some scenarios, you don't want a data action to run when a page is first loaded. Instead, you want it to run dynamically in response to some event on the client. For example, a product can be added to a customer's cart in response to a button click, search results can be shown in response to a change in the text input, or banner text can be updated in response to a time-based event.

## Example

In the following example, a very basic module loads product information when a user clicks a button. 

The following code shows a **react** component that contains a button that users can click.

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

Currently, this component just logs a message to the console when the button is clicked. To replace that behavior with the data action, you must do three things:

1. Import the data action and its input class.
1. Create an input for the data action.
1. Invoke the data action.

The following code shows an updated **react** component that makes a call for a product when the button is clicked.

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

> [!NOTE]
> This example uses a hard-coded **productId** value. However, it can be updated so that the **productId** value is read from text input or the module's configuration properties.

## Additional resources

[Data actions overview](data-actions.md)

[Data action cache options](data-action-cache.md)

[Test data actions with mocks](test-data-action-mocks.md)

[Page load data actions](page-load-data-action.md)

[Core data actions](core-data-actions.md)

[Call Retail Server APIs](call-retail-server-apis.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
