---
# required metadata

title: Module data files
description: This topic provides information about module data files. A module data file contains the typings for data actions that the module uses to fetch data. 
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
# Module data files

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

A module data file contains the typings for data actions that the module uses to fetch data. The naming convention for module data files is *MODULE\_NAME.data.ts*.

The software development kit (SDK) includes a set of core data actions that can get data from Microsoft Dynamics 365 Retail ratings and reviews or the recommendations service. You can find the list of data actions under the SDK's \\node\_modules\\@msdyn365-commerce-modules\\retail-actions\\dist\\lib directory.

## Example

The following example shows a sample data file for a new module.

```typescript
/*---------------------------------------------------------------------------------------------
 *  Copyright (c) Microsoft Corporation. All rights reserved.
 *  Licensed under the MIT License. See License.txt in the project root for license information.
 *--------------------------------------------------------------------------------------------*/

import { SimpleProduct } from '@msdyn365-commerce/commerce-entities';
import { AsyncResult } from '@msdyn365-commerce/retail-proxy';
import { IGetProductReviewsData } from '../../actions/getProductReviews';

export interface IProductFeatureData {
    products: AsyncResult<SimpleProduct>[];
    productReviews: AsyncResult<IGetProductReviewsData>;
}
```
