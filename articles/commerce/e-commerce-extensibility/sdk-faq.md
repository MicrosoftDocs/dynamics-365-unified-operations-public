---
# required metadata

title: Dynamics 365 Commerce online SDK FAQ
description: This topic summarizes answers to questions frequently asked by users of the Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
manager: annbe
ms.date: 01/28/2021
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
# Dynamics 365 Commerce online SDK FAQ

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic summarizes answers to questions frequently asked by users of the Dynamics 365 Commerce online software development kit (SDK).

### TSLint has been deprecated in online SDK version 9.27 (Commerce version 10.0.18 release) and replaced with ESLint
Due to the open source TSLint static analysis tool has being deprecated, the Dynamics 365 Commerce online SDK has changed to leverage the [ESLint](https://eslint.org/) static alaysis tool.  When updating to SDK 9.27, your packages.json file will need to be manually updated to remove the dependency on TSLint and add the dependency to the ESLint dependency.  You then may see new ESLint warnings in your customization code that did not previously exist.

The below packages.json is an example with dependency links to ESLint.  Your packages.json may be different if you have made any modifications to the default.

```
{
  "name": "Msdyn365.Commerce.Online",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "analyze": "SET ANALYZE_BUNDLE=true && yarn msdyn365b start",
    "analyze:prod": "SET ANALYZE_BUNDLE=true && yarn msdyn365b build",
    "build": "yarn msdyn365b build",
    "build:prod": "yarn clean && yarn msdyn365b build",
    "clean": "yarn rimraf build lib dist .tmp gendef.lock",
    "format": "yarn prettier **/**.{ts,tsx}",
    "format:fix": "yarn prettier **/**.{ts,tsx} --write",
    "lint": "yarn tslint src/**/*.{ts,tsx} --project tsconfig.json --format stylish",
    "lint:fix": "yarn tslint src/**/*.{ts,tsx} --project tsconfig.json --fix --format stylish",
    "precommit": "lint-staged",
    "start": "yarn msdyn365b start local",
    "start:prod": "SET NODE_ENV=production && node build/server.js"
  },
  "devDependencies": {
    "@types/fs-extra": "^5.0.4",
    "@types/jest": "^23.3.10",
    "@types/node-fetch": "^2.1.4",
    "@types/react": "16.9.0",
    "@types/react-dom": "16.0.11",
    "@types/react-test-renderer": "^16.0.2",
    "@types/reactstrap": "^6.4.3",
    "deep-equal": "1.0.1",
    "fs-extra": "^7.0.1",
    "identity-obj-proxy": "^3.0.0",
    "jest": "^23.6.0",
    "jest-junit": "^5.2.0",
    "lint-staged": "^7.3.0",
    "node-fetch": "2.6.1",
    "prettier": "^1.15.3",
    "react-test-renderer": "^16.4.2",
    "semver": "^5.6.0",
    "ts-jest": "^23.10.5",
    "tslint": "^5.12.0",
    "typeson": "5.10.1"
  },
  "dependencies": {
    "@msdyn365-commerce-modules/starter-pack": "9.26",
    "@msdyn365-commerce-modules/fabrikam-design-kit": "9.26",
    "@msdyn365-commerce/bootloader": "^1.0.0",
    "@msdyn365-commerce/retail-proxy": "9.26",
    "@msdyn365-commerce-modules/msdyn365-exp-test-connector": "^1.0.0",
    "reactstrap": "^6.5.0",
    "stack-trace": "^0.0.10",
    "tslib": "^1.9.3"
  },
  "lint-staged": {
    "*.(j|t)s(x)?": [
      "yarn format:fix",
      "yarn lint:fix",
      "git add"
    ]
  },
  "jest": {
    "preset": "@msdyn365-commerce/cli-internal"
  },
  "resolutions": {
    "@msdyn365-commerce/bootloader": "^1.0.0",
    "@msdyn365-commerce/core": "^1.0.0",
    "@msdyn365-commerce-modules/core-components": "^1.0.0"
  }
}
```

### After upgrading to module library version 9.27 (Commerce version 10.0.17 release), buy box module view extensions might generate a compilation error.

The compilation error is caused by code sharing that is related to the product quick view module that was introduced in the Commerce version 10.0.17 release. Because the quick view module shares lots of functionality with the buy box module, some common components were moved to a common folder, so that the buy box and quick view modules can share the code.

To fix the compilation error, update any import references in the buybox.tsx view file, as shown in the examples that follow.

This example shows the old code for imports in buybox.view.tsx.

```typescript
import { IBuyboxViewProps } from '../..';
import {
    IBuyboxAddToCartViewProps,
    IBuyboxAddToOrderTemplateViewProps,
    IBuyboxAddToWishlistViewProps,
    IBuyboxFindInStoreViewProps,
    IBuyboxKeyInPriceViewProps,
    IBuyboxProductConfigureDropdownViewProps,
    IBuyboxProductConfigureViewProps,
    IBuyboxProductQuantityViewProps,
    IBuyboxShopSimilarLookViewProps
} from './components';
```

This example shows the new code for imports in buybox.view.tsx.

```typescript
import { IBuyboxAddToCartViewProps, IBuyboxAddToOrderTemplateViewProps, IBuyboxAddToWishlistViewProps, IBuyboxKeyInPriceViewProps, IBuyboxProductConfigureDropdownViewProps, IBuyboxProductConfigureViewProps, IBuyboxProductQuantityViewProps, IBuyboxShopSimilarLookViewProps } from '../../common';
import { IBuyboxViewProps } from './buybox';
import { IBuyboxFindInStoreViewProps } from './components/buybox-find-in-store';
```

### After upgrading to module library version 9.24 (10.0.14 release), cloned modules that use data actions may display the error, "UserAuthorizationException. Customer account number on the request was wrong".

The following list of [core data actions](core-data-actions.md) have a signature change that moves the user account number parameter to the second parameter (instead of the first) and is now set as an optional parameter. In most scenarios where the user account number is no longer needed, the data action will execute in the context of the current signed-in user. In some custom scenarios where the user account number is different than the user account number of the signed-in user, you can fetch the user account number by using the **get-customer** data action and passing it to the data action.

Core data actions with signature changes include:
 
- **add-address**
- **get-address**
- **get-customer**
- **get-loyalty-card**
- **get-loyalty-transaction-estimation**
- **issue-loyalty**

The module library modules have been updated with the correct calling pattern to the above data actions, so you won't receive any errors in these modules. However, if one of the modules was previously [cloned](clone-starter-module.md) it will still have the older data action signature and display this error at runtime, "UserAuthorizationException. Customer account number on the request was wrong". The signatures will need to be updated accordingly. One way to resolve this issue is to temporarily clone the module library module again with a new name, then differentiate the new module code with the previously cloned custom module and merge the changes. The temporary module can then be deleted.

### After upgrading to module library version 9.23 (10.0.13 release), cloned modules or view extensions that import "CartlineComponent" or "WishListIconComponent" components may display the errors "export 'CartlineComponent' was not found in '@msdyn365-commerce/components'" or "export 'WishListIconComponent' was not found in '@msdyn365-commerce/components'".

The "CartlineComponent" and "WishListIconComponent" components have been renamed to "CartLineItemComponent" and "WishlistIconComponent" respectively. If the previous component names are used in either a cloned module or a view extension, the build errors mentioned above will be displayed. To fix these issues, update the previous component names to the new component names in the cloned module or view extension code.

## Additional resources

[Core data actions](core-data-actions.md)

[Clone a module library module](clone-starter-module.md)

[Best practices for Dynamics 365 Commerce development](best-practices-dev.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
