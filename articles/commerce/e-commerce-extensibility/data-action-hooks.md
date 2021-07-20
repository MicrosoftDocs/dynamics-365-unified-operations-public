---
# required metadata

title: Data action hooks
description: This topic describes how to hook into pre- and post- data action events to further process data if needed.
author: samjarawan
ms.date: 07/16/2020
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
ms.search.validFrom: 2020-01-31
ms.dyn365.ops.version: Release 10.0.10

---
# Data action hooks

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The data action hooks feature has been deprecated. To avoid performance issues, we strongly recommend that you use [data action overrides](data-action-overrides.md) to modify business logic in the data action layer.

This topic describes how to hook into pre- and post- data action events to further process data if needed.

The modules included with the Dynamics 365 Commerce software development kit (SDK) use pre-existing actions to fetch data for the modules to use. You may have scenarios where you want to change some business logic in the data action layer. In addition to support for data action overrides, the Commerce platform also has the ability to hook into pre- and post- data action events.

## Supported data action hook events

The following data action hook events are supported:
- **preHook**: Runs before the action starts to modify the data action input. This event is only applied to uncached data actions.
- **preReadOnlyHook**: Runs before the action starts but cannot modify the data action input. This event can be applied to both cached and uncached data actions.
- **postHook**: Runs after the data action completes and can modify the data action output. This event is only applied to uncached data actions.
- **postReadOnlyHook**: Runs after the data action completes but cannot modify the data action output. This event is supported on both cached and uncached data actions.

## Use data action hooks

To use a data action hook, you can leverage the **add-data-action** command-line interface (CLI) command to create the file. The following example creates a data action file named "get-address-hook.action.ts" under the "\src\actions" directory.

```Console
yarn msdyn365 add-data-action get-address-hook
```

Next, you replace the code in the data action file with the following template code and then add appropriate code to the event you are interested in.

```typescript
import { createDataActionHook, IActionInput } from '@msdyn365-commerce/core';
// import { Cart } from '@msdyn365-commerce/retail-proxy';

const beforeCart = async (inputs: IActionInput | IActionInput[]) => {
    // tslint:disable-next-line: no-console
    console.info('Pre Hook');
};

const afterCart = async (_inputs: IActionInput | IActionInput[], cartName: string | string[]) => {
    // tslint:disable-next-line: no-console
    console.info('Post Hook');
};

const preReadOnlyCart = async (inputs: IActionInput | IActionInput[]) => {
    // tslint:disable-next-line: no-console
    console.info('Pre ReadOnly Hook');
};

const postReadOnlyCart = async (_inputs: IActionInput | IActionInput[], cartName: string | string[]) => {
    // tslint:disable-next-line: no-console
    console.info('Post ReadOnly Hook');
};

createDataActionHook({
    actionId: 'Action_ID',
    postHook: afterCart,
    preHook: beforeCart,
    preReadonlyHook: preReadOnlyCart,
    postReadonlyHook: postReadOnlyCart
});
```

>[!NOTE]
> You'll need to change the **Action_ID** to the data action ID you are adding event hooks to. The module library list of data actions can be found in the …\Msdyn365.Commerce.Online\node_modules\@msdyn365-commerce-modules\retail-actions\dist\lib directory of the SDK.

## Additional resources

[Chain data actions](chain-data-actions.md)

[Batch data actions](batch-data-actions.md)

[Create an observable data action](create-observable-data-action.md)

[Share state across modules](share-state-across-modules.md)

[Data action overrides](data-action-overrides.md)

[Data action cache settings](data-action-cache-settings.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
