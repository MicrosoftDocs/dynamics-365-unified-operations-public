---
# required metadata

title: Call server side data actions with AJAX
description: This topic describes how to call server side data actions with AJAX.
author: samjarawan
manager: annbe
ms.date: 07/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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
ms.dyn365.ops.version: Release 10.0.5

---
# Call server side data actions with AJAX

[!include [banner](../includes/banner.md)]

This topic describes how to call server side data actions with AJAX.

## Overview

Dynamics 365 Commerce SDK offers support for invoking a server side data action from the client browser. This can be used in scenarios where data actions contains sensitive information such as an API Key or secret needed to call a third party service.  In these cases you would not want the secret to be revealed with a client side data action call.

To invoke a data action on the server, the below URL route can be used with the 'id' query parameter where 'id' is the data action that will be run on the server. The route supports supports both HTTP **GET** and **POST** requests.

```js
/api?id=<data_action_id>
```

The online SDK provides a helper utility function **commerceAPIRequest** which provides control on the AJAX request that includes additional context information.

#### GET Request

```jsx noeditor
import * as MsDyn365 from '@msdyn365-commerce/core';

public async componentDidMount(): Promise<void> {
    const response = await MsDyn365.commerceApiRequest(
        this.props.context.request,
        '<data_action_id>',
        'get'
    );
}
```

#### POST Request

```jsx noeditor
import * as MsDyn365 from '@msdyn365-commerce/core';

public async componentDidMount(): Promise<void> {
    const response = await commerceApiRequest(
        this.props.context.request,
        '<data_action_id>',
        'post',
        {
            content: 'sample text'
        }
    );
}
```
For POST requests, the post body can be accessed from the context object inside the data action.

```js noeditor
ctx.requestContext.postBody
```

## Additional resources

[Data action overview](data-actions.md)

[Create an observable data action](create-observable-data-action.md)

[Data action cache settings](data-action-cache-settings.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
