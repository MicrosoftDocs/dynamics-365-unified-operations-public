---
# required metadata

title: Module Data File
description: The MODULE_NAME.data.ts file contains data actions that are used by the module to fetch data. 
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
# Module Data File
The MODULE_NAME.data.ts file contains data actions that are used by the module to fetch data.  A set of core data actions are included in the SDK that can get data from the Dynamics 365 Retail, Ratings and Review or the Recommendations service.  The list of data actions can be found under the SDK \node_modules\@msdyn365-commerce-modules\retail-actions\dist\lib directory.

Below is a sample data file for a new module

## Example
```typescript
/*---------------------------------------------------------------------------------------------
 *  Copyright (c) Microsoft Corporation. All rights reserved.
 *  Licensed under the MIT License. See License.txt in the project root for license information.
 *--------------------------------------------------------------------------------------------*/

import { SimpleProduct } from '@msdyn365-commerce/commerce-entities';
import { ObservablePromise } from '@msdyn365-commerce/core';
import { IGetProductReviewsData } from '../../actions/getProductReviews';

export interface IProductFeatureData {
    /**
     * @dataAction @msdyn365-commerce-modules/retail-actions/dist/lib/get-simple-products
     * @runAt server
     */
    products: ObservablePromise<SimpleProduct>[];

    /**
     * @dataAction ../../actions/getProductReviews
     * @runAt server
     */
   productReviews: IGetProductReviewsData;
}
```
