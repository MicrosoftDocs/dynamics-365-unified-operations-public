---
# required metadata

title: Dynamics 365 Commerce online SDK FAQ
description: This topic summarizes answers to questions frequently asked by users of the Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
ms.date: 04/21/2022
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
ms.dyn365.ops.version: Release 10.0.5

---
# Dynamics 365 Commerce online SDK FAQ

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic summarizes answers to questions frequently asked by users of the Dynamics 365 Commerce online software development kit (SDK).

### Why does my e-commerce extension package fail to build due to an incompatible version of Node.js?

If you updated to version 1.37 or higher of the online SDK package, you may experience a build break if you are using Node version 12.x since version 1.37 has been updated to support Node.js version 16.x. You will see the following error message:

`The engine "node" is incompatible with this module. Expected version ">=16.x.x". Got "12.22.6".` 

To resolve this issue you must update Node.js to version 16.x on local build environments and any automated build environments such as Azure DevOps pipelines. 

### How do I resolve heap out of memory errors?

If you are experiencing heap out of memory errors when building the online SDK, it is possible that the code has incorrect imports. To ensure that paths are set up correctly we recommend that you use the [CLI tools](cli-command-reference.md) included with the online SDK for creating customizations such as view extensions, component overrides, and module clones.

Imports from modules residing in the **node_modules** directory should always be against the namespace and module name. Any import of a module with an absolute path from the module's **src** folder causes the build process to run into a loop which could lead to heap out of memory errors.

The following example shows an invalid import because all of the importable components were already exported by the module.

```ts
import { IHeaderViewProps } from '@msdyn365-commerce-modules/header/src/header';
```

The following example shows a valid import. 

```ts
import { IHeaderViewProps } from '@msdyn365-commerce-modules/header';
```

### How do I increase node memory size?

The default memory setting should be sufficient for most customization scenarios. However, if your application needs more heap space you can specify the environment variable in the scripts section of the package.json file by adding **--max_old_space_size=4096**, as shown in the following example:

```JSON
"build": "SET NODE_OPTIONS=--max_old_space_size=4096 && yarn msdyn365b build --use-eslint",
```

### During package upload, I receive this error message: "The e-commerce package has an outdated online SDK. Please create a new package and retry." Or, during package deployment, I receive this error message: "The e-commerce package cannot be deployed due to an outdated online SDK. Please create a new package and retry deployment." Why?

To help decrease deployment time during package deployment, uploaded packages are prebuilt while the **yarn msdyn365 pack** [command-line interface (CLI) command](cli-command-reference.md#pack) is run by using the latest online SDK. If package upload fails, and you receive one of the error messages, update to the latest SDK by using the **[yarn msdyn365 update-versions sdk](cli-command-reference.md#update-versions)** CLI command. In this way, you ensure that the yarn.lock file is deleted before you run yarn to pull down the latest online SDK. You can then rebuild the package by using the **yarn msdyn365 pack** command, and then redeploy the new package.

### Can I opt in to using Webpack 5 to bundle the Commerce application?

The Dynamics 365 Commerce online SDK supports using the latest Webpack 5 release to bundle the Commerce application. Webpack 5 offers improved bundling together with better tree shaking and code generation to help reduce the amount of JavaScript that is downloaded and processed on a page.

In the version 1.32 (Commerce version 10.0.22) release of the online SDK, you can opt in to Webpack 5. In the version 1.34 (Commerce version 10.0.24) release, Webpack 5 will become the default option, and no opt in will be required.

You can enable Webpack 5 by running the **yarn msdyn365 upgrade-webpack** command. This command updates the package.json file with the list of dependencies that are required for Webpack 5. After the package.json file is updated, you can install the new dependencies by running the **yarn** command. The following example shows the two commands.

```Console
yarn msdyn365 upgrade-webpack

yarn
```

### How can I make server-side module failures more apparent?

Version 1.3 of the Dynamics 365 Commerce online SDK introduced a change in the number of modules that are rendered in the development environment. During module development, modules can be rendered on both the server side and the client side. If modules fail on the server side, those failures can be masked and difficult to detect because the modules are also running on the client side.

To make server-side failures more apparent, version 1.31 of the online SDK generates an error message. This message states that an issue occurred during module rendering on the server, and that the issue must be addressed before the module can be successfully rendered in the development environment. This validation occurs only in the development environment (the production environment isn't affected).

Here is an example of the error message that is shown in developer mode:

> 'test-module' threw exception
>
> Error: Error during server side rendering for module test-module of type test-module. NOTE: This error is only displayed in DEVELOPER mode. This won't affect PRODUCTION. This is a safety measure so developer can address issues that happen on the server. Please, address the following issue: window is not defined.

### Why are my custom Application Insights API calls failing to build after I upgrade to the Commerce online SDK version 9.30 release?

The Commerce online SDK version 9.30 release includes an update from the deprecated [Applications Insights SDK](https://www.npmjs.com/package/applicationinsights-js) to the newer [Microsoft Application Insights JavaScript SDK - Web](https://www.npmjs.com/package/@microsoft/applicationinsights-web).

The Applications Insights update contains breaking API changes that might affect your customization code if you've used these APIs to log telemetry into your Application Insights instance. For details about the changes, see [Upgrading from the old version of Application Insights](https://github.com/microsoft/ApplicationInsights-JS#upgrading-from-the-old-version-of-application-insights).

### What is replacing TSLint, which has been deprecated in SDK version 1.28 (the Commerce version 10.0.18 release)?

Because the open-source TSLint static analysis tool has been deprecated, the Dynamics 365 Commerce online SDK is replacing it with the [ESLint](https://eslint.org/) static analysis tool. TSLint will continue to work until SDK version 1.30 (the Commerce version 10.0.20 release). Before SDK version 1.30, you can manually update to ESLint if you want. However, in SDK version 1.30, update to ESLint will be enforced.

After you update to SDK version 1.28, you will receive a deprecation warning when you run the **yarn** command. You can switch to ESLint at any time afterward. However, you might receive new errors and warnings against your custom code.

If you retrieved the online SDK from GitHub, together with the Commerce 10.0.18 preview release, it will contain the required changes to ESLint. No further changes are required. However, if you're updating from an older version of the SDK, you must manually update to ESLint before SDK version 1.30. 

Follow the instructions in this section to manually update from TSLint to ESLint.

#### Replace TSLint with ESLint

After you [update to SDK version 1.28](sdk-updates.md) or later, you must create an ESLint file and change your **package.json** file so that it includes the ESLint dependencies. You must also update the commands so that they use ESLint. You can leave the TSLint dependency in the **package.json** file if you want to use both TSLint and ESLint. After you update to ESLint, you might receive new warnings against your code. You can fix or ignore the warnings as required.

##### Create an .eslintrc.js file

You must add a new file that is named **.eslintrc.js** to your root SDK folder. (In that folder, you should also see an existing **tslint.json** file.) The **.eslintrc.js** file contains a base rule set that can be extended.

The base configuration contains a set of core rules that are relaxed in terms of linting restrictions. You can also define your own rule set or extend another rule set.

To use the base rule set that is provided, create the **.eslintrc.js** file, and paste in the following code.

```javascript
module.exports = {
    extends: '@msdyn365-commerce/eslint-config',
    ignorePatterns: ['.eslintrc.js', '*.html', 'src/__mocks__/**', 'src/__tests__/**'],
    parserOptions: {
        project: ['tsconfig.json'],
        sourceType: 'module',
        ecmaFeatures: {
            jsx: true // Allows for the parsing of JSX
        },
        tsconfigRootDir: __dirname
    }
};
```

If there are additional files and directories that you don't want lint rules to be applied to, you can add them to the **ignorePatterns** section.

You can also extend or replace rules by defining rules in the **.eslintrc.js** file. For example, the **header/header** rule requires a header on all files, and you want to extend the base configuration to turn off that rule. In this case, use the following code in the configuration file.

```javascript
module.exports = {
    extends: '@msdyn365-commerce/eslint-config',
    ignorePatterns: ['.eslintrc.js', '*.html', 'src/__mocks__/**', 'src/__tests__/**'],
    parserOptions: {
        project: ['tsconfig.json'],
        sourceType: 'module',
        ecmaFeatures: {
            jsx: true // Allows for the parsing of JSX
        },
        tsconfigRootDir: __dirname
    },
    rules: {
        'header/header': 'off'
    }
};
```

You might also want to override or declare new rules for some types of files. In this case, use the **overrides** property, as shown in the following example.

```javascript
overrides: [
    {
        files: ['*.props.autogenerated.ts', '*.data.ts'],
        rules: {
            'header/header': 'off'
        }
    },
    {
        files: ['*.tsx', '*.view.tsx', '*.test.ts'],
        rules: {
            'max-len': 'off',
            'max-lines': 'off'
        }
    }
],
```

For more information and help, see the [ESLint documentation](https://eslint.org/docs/2.0.0/user-guide/configuring).

##### Create a .prettierrc file

Prettier is an opinionated code formatter that can be configured to format your code after you save a file. A .prettierrc file allows you to add new rules that Prettier will use. You will need to create a **.prettierrc** file in the root SDK folder with the following default settings.

```json
{
    "tabWidth": 4,
    "singleQuote": true,
    "printWidth": 140,
    "jsxSingleQuote": true,
    "bracketSpacing": true
}
```

##### Update the package.json file

If you want to use both TSLint and ESLint, you can leave the TSLint dependency in your **package.json** file and add the following dependencies in the **devDependencies** section.

```json
"@msdyn365-commerce/eslint-config": "^1.27.7",
"@typescript-eslint/eslint-plugin": "^4.2.0",
"@typescript-eslint/parser": "^4.10.0",
"eslint": "^7.16.0",
"eslint-config-prettier": "^7.0.0",
"eslint-plugin-header": "^3.1.0",
"eslint-plugin-import": "^2.22.1",
"eslint-plugin-jsdoc": "^30.7.8",
"eslint-plugin-no-null": "^1.0.2",
"eslint-plugin-prettier": "^3.3.0",
"eslint-plugin-react": "^7.21.5",
```

Then change the **lint** and **lint:fix** commands as shown here.

```json
"lint": "yarn eslint src/**/*.{ts,tsx}",
"lint:fix": "yarn eslint src/**/*.{ts,tsx} --fix"
```

Finally, change the **build** and **start** commands as shown here.

```json 
"start": "yarn msdyn365b start local --use-eslint",
"build": "yarn msdyn365b build --use-eslint",
"build-prod": "yarn clean && yarn msdyn365b build --use-eslint",
```

#### Fix ESLint errors

Although this step is optional, we recommend that you install the ESLint extension for Visual Studio Code. This extension helps identify errors and warnings directly in your editor. Additionally, quick actions let you use comments to ignore linting errors.

You might receive new ESLint errors, because all the TSLint errors that were suppressed through TSLint comments are being shown again. The ESLint errors can be fixed or disabled, and you can choose to ignore the warnings.

If you use `–use-eslint` flags in your code, builds will fail when errors occur. However, warnings will be ignored.

#### Disable linting in code

You can fix TSLint errors by replacing TSLint disable comments with ESLint disable comments. You can use file find and replace functionality if that approach is easier. However, be sure to verify the results.

Here are some helpful tips:

- Like TSLint warnings, ESLint warnings can be disabled by using comments.
- To disable the next line, use `// eslint-disable-next-line <rule1>, <rule2>...`.
- To add a comment that explains why you're disabling a rule, you must add two hyphens (--) (for example, `// eslint-disable-next-line <rule1> -- Disabling this rule for reasons`).
- To disable a rule for a whole file, you must use multiline comments (for example, `/* eslint-disable <rule1>, <rule2> */`).

The following table lists common equivalents in TSLint and ESLint.

| TSLint rule | ESLint rule |
|---|---|
| // tslint:disable-next-line:no-any | // eslint-disable-next-line @typescript-eslint/no-explicit-any |
| // tslint:disable:no-any | /\* eslint-disable @typescript-eslint/no-explicit-any \*/ |
| // tslint:disable-next-line:cyclomatic-complexity | // eslint-disable-next-line complexity |
| // tslint:disable-next-line:no-empty | // eslint-disable-next-line no-empty |

#### Continue to lint with TSLint

If you want to continue to lint using TSLint, you can use the **–use-tslint** argument in the package.json **build** and **start** commands, as shown here.

```json
"start": "yarn msdyn365b start local --use-tslint",
"build": "yarn msdyn365b build --use-tslint",
"build-prod": "yarn clean && yarn msdyn365b build --use-tslint",
```

> [NOTE] 
> Support for TSLint is limited and it is encouraged to use ESLint whenever possible.

#### Completely disable linting during build time

If you want to completely disable linting during build time, you can use the **--disable-linter** argument in the **package.json** build command, as shown here.

```json 
"build": "yarn msdyn365b build --disable-linter",
"build:prod": "yarn clean && yarn msdyn365b build --disable-linter",
```

### After upgrading to module library version 9.27 (Commerce version 10.0.17 release), buy box module view extensions might generate a compilation error.

The compilation error is caused by code sharing that is related to the product quick view module that was introduced in the Commerce version 10.0.17 release. Because the quick view module shares many functionalities with the buy box module, some common components were moved to a common folder, so that the buy box and quick view modules can share the code.

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

The [core data actions](core-data-actions.md) listed below have a signature change that moves the user account number parameter to the second parameter (instead of the first) and is now set as an optional parameter. In most scenarios where the user account number is no longer needed, the data action will execute in the context of the current signed-in user. In some custom scenarios where the user account number is different than the user account number of the signed-in user, you can fetch the user account number by using the **get-customer** data action and passing it to the data action.

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
