---
# required metadata

title: Data action hooks
description: This topic describes how to hook into data action pre/post events to further process data if needed.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
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

This topic describes how to hook into data action pre/post events to further process data if needed.

## Overview

The set of modules included with the module library use pre-existing data actions to fetch data for the module to use.  You may have scenarios where you want to change some business logic in the data action layer. Along with [data action overrides](data-action-overrides.md) the Commerce e-Commerce platform has the ability to hook into pre and post data action events.

## Supported hook events

The following list of hooks are supported:
1. **prehook** - runs before the action starts to modify the data action input.  Note this is only applied to uncached data actions.
1. **preReadOnlyHook** - runs before the action start but cannot modify the data action input.  Note this can be applied to both cached and uncached data actions.
1. **postHook** - runs after the data action completes and can modify the data action output.  Note this is only applied to unchached data actions.
1. **postReadOnlyHook** - runs after the data action completes but cannot modify the data action output.  This is supported on both cached and uncached data actions.

rendered by the module but perhaps may want to alter the business logic in the data action.  With data action overrides, you can override the registered action by creating a new action with the same action id. Overriding a data action will cause all previous uses of the data action, either through import or inclusion in the module definition.json file, to use your new data action.

## Using data action hooks

To use a data action hook you can leverage the **add-data-action** CLI to create the file.  The below example will create a data action file "get-address-hook.action.ts" under the "\src\actions" directory.

```console
yarn msdyn365 add-data-action get-address-hook
```

Next, replace the file with the below template code and add the appropriate code to the event you are interested in.

```typescript
/*!
 * Copyright (c) Microsoft Corporation.
 * All rights reserved. See LICENSE in the project root for license information.
 */

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

Note you'll need to change the **Action_ID** to the data action ID you are adding event hooks to.  The module library list of data actions can be found under the SDK …\Msdyn365.Commerce.Online\node_modules\@msdyn365-commerce-modules\retail-actions\dist\lib directory.

