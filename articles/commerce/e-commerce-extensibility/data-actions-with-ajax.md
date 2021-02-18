---
# required metadata

title: Call server-side data actions with AJAX
description: This topic describes how to call server-side data actions with AJAX in Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 03/01/2021
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
# Call server-side data actions with AJAX

[!include [banner](../includes/banner.md)]

This topic describes how to call server-side data actions with AJAX in Dynamics 365 Commerce.

## Overview

The Dynamics 365 Commerce online software development kit (SDK) offers support for invoking a server-side data action from the client browser using asynchronous JavaScript and XML (AJAX). This feature can be used in scenarios where data actions contain sensitive information such as an API key or secret needed to call a third-party service. In these cases, for security reasons you would not want the sensitive information to be revealed with a client-side data action call.

To invoke a data action on the server using AJAX, the following URL route with the **id** query parameter can be used, where the **id** parameter value specifies the data action that will be run on the server. This URL route supports both HTTP **GET** and **POST** requests.

```js
/api?id=<data_action_id>
```

The online SDK provides the **commerceAPIRequest** helper utility function, which provides controls on AJAX requests that include the ability to support additional context information.

### GET request format

```js
import * as MsDyn365 from '@msdyn365-commerce/core';

public async componentDidMount(): Promise<void> {
    const response = await MsDyn365.commerceApiRequest(
        this.props.context.request,
        '<data_action_id>',
        'get'
    );
}
```

### POST request format

```js
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
For POST requests, the post body can be accessed from the context object **ctx.requestContext.postBody** inside the data action, as in the following example.

 ```js
 async function action(
        input: Msdyn365.IActionInput[],
        ctx: Msdyn365.IActionContext
    ): Promise<IWeatherConditions[]> {
    const postBody = ctx.requestContext.postBody?.content;
    return postBody;
}
 ```

## Additional resources

[Data action overview](data-actions.md)

[Create an observable data action](create-observable-data-action.md)

[Data action cache settings](data-action-cache-settings.md)
