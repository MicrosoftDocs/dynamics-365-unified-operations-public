---
title: Call server-side data actions with AJAX
description: This article describes how to call server-side data actions by using Asynchronous JavaScript and XML (AJAX) in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 07/31/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Call server-side data actions with AJAX

[!include [banner](../includes/banner.md)]

This article describes how to call server-side data actions by using Asynchronous JavaScript and XML (AJAX) in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce online software development kit (SDK) supports using AJAX to invoke server-side data actions from the client browser. This feature can be used in scenarios where data actions contain sensitive information, such as an API key or secret that is required to call a third-party service. In these scenarios, for security reasons, you don't want the sensitive information to be revealed through a client-side data action call.

To use AJAX to invoke a data action on the server, you can use the following URL route, where the ID parameter value specifies the data action that will be run on the server. This URL route supports both HTTP **GET** and **POST** requests.

```js
/api?id=<data_action_id>
```

The online SDK provides the **commerceAPIRequest** helper utility function. This function provides controls for AJAX requests, such as the ability to support additional context information.

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

For **POST** requests, the post body can be accessed from the **ctx.requestContext.postBody** context object inside the data action, as shown in the following example.

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

[Observable data actions](create-observable-data-action.md)

[Data action cache settings](data-action-cache-settings.md)
