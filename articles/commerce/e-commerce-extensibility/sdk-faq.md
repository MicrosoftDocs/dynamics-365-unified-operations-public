---
title: Dynamics 365 Commerce online SDK FAQ
description: This article provides answers to frequently asked questions about the Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
ms.date: 02/05/2026
ms.topic: faq
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Dynamics 365 Commerce online SDK FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the Dynamics 365 Commerce online software development kit (SDK).

### Why does my e-commerce extension package fail to build due to an incompatible version of Node.js?

If you updated to version 1.37 or higher of the online SDK package, you might experience a build failure if you're using Node version 12.x. Version 1.37 supports Node.js version 16.x. You see the following error message:

`The engine "node" is incompatible with this module. Expected version ">=16.x.x". Got "12.22.6".` 

To resolve this problem, update Node.js to version 16.x on local build environments and any automated build environments such as Azure Pipelines.

### How do I upgrade to Node 18?

To upgrade to Node 18, ensure that you're using version 1.49 or later of the [Dynamics 365 Commerce Online SDK](setup-dev-environment.md#install-the-online-sdk-and-module-library).

> [!NOTE] 
> If after the upgrade you experience an error when running the **yarn** command such as `node-sass: Command failed`, remove `node-sass` and `sass-loader` from your package.json file, and then rerun the **yarn** command.

To run your deployed app on Node 18, set the **NODE_RUNTIME_VERSION** environment variable in your build script.

Your package.json should look like the following example.

```JSON

"build": "SET NODE_RUNTIME_VERSION=18 && yarn msdyn365b build --use-eslint",

```

### How do I resolve heap out of memory errors?

If you get heap out of memory errors when building the online SDK, the code might have incorrect imports. To make sure that paths are correct, use the [CLI tools](cli-command-reference.md) included with the online SDK for creating customizations such as view extensions, component overrides, and module clones.

Always import modules from the **node_modules** directory by using the namespace and module name. If you import a module by using an absolute path from the module's **src** folder, the build process runs into a loop. This loop can cause heap out of memory errors.

The following example shows an invalid import because all of the importable components are already exported by the module.

```ts
import { IHeaderViewProps } from '@msdyn365-commerce-modules/header/src/header';
```

The following example shows a valid import. 

```ts
import { IHeaderViewProps } from '@msdyn365-commerce-modules/header';
```

### How do I increase node memory size?

The default memory setting works for most customization scenarios. However, if your application needs more heap space, specify the environment variable in the scripts section of the package.json file by adding **--max_old_space_size=4096**, as shown in the following example:

```JSON
"build": "SET NODE_OPTIONS=--max_old_space_size=4096 && yarn msdyn365b build --use-eslint",
```

### Can I clear a node app's cache?

Yes. To clear a node app's cache in Commerce site builder, select **Site settings \> Extensions**, select the **Configuration** tab, and update the value of the **Cache key suffix** setting value to any random characters (for example, "xyz"). Updating the value clears the node app's cache.

### During package upload, I receive this error message: "The e-commerce package has an outdated online SDK. Please create a new package and retry." Or, during package deployment, I receive this error message: "The e-commerce package can't be deployed due to an outdated online SDK. Please create a new package and retry deployment." Why?

To help decrease deployment time during package deployment, the latest online SDK prebuilds uploaded packages while running the **yarn msdyn365 pack** [command-line interface (CLI) command](cli-command-reference.md#pack). If package upload fails, and you receive one of the error messages, update to the latest SDK by using the **[yarn msdyn365 update-versions sdk](cli-command-reference.md#update-versions)** CLI command. This step ensures that the yarn.lock file is deleted before you run yarn to pull down the latest online SDK. You can then rebuild the package by using the **yarn msdyn365 pack** command, and then redeploy the new package.

### Can I opt in to using Webpack 5 to bundle the Commerce application?

The Dynamics 365 Commerce online SDK supports using the latest Webpack 5 release to bundle the Commerce application. Webpack 5 offers improved bundling together with better tree shaking and code generation to help reduce the amount of JavaScript that is downloaded and processed on a page.

In version 1.32 (Commerce version 10.0.22) of the online SDK, opt in to Webpack 5. In version 1.34 (Commerce version 10.0.24) of the online SDK, Webpack 5 is the default option.

Enable Webpack 5 by running the **yarn msdyn365 upgrade-webpack** command. This command updates the package.json file with the list of dependencies that are required for Webpack 5. After the package.json file is updated, install the new dependencies by running the **yarn** command. The following example shows the two commands.

```Console
yarn msdyn365 upgrade-webpack

yarn
```

### How can I make server-side module failures more apparent?

Version 1.3 of the Dynamics 365 Commerce online SDK introduced a change in the number of modules that are rendered in the development environment. During module development, modules render on both the server side and the client side. If modules fail on the server side, those failures can be masked and difficult to detect because the modules are also running on the client side.

To make server-side failures more apparent, version 1.31 of the online SDK generates an error message. This message states that an issue occurred during module rendering on the server, and that the issue must be addressed before the module can be successfully rendered in the development environment. This validation occurs only in the development environment (the production environment isn't affected).

Here's an example of the error message that is shown in developer mode:

> 'test-module' threw exception
>
> Error: Error during server side rendering for module test-module of type test-module. NOTE: This error is only displayed in DEVELOPER mode. This won't affect PRODUCTION. This is a safety measure so developer can address issues that happen on the server. Please, address the following issue: window is not defined.

### Why are my custom Application Insights API calls failing to build after I upgrade to the Commerce online SDK version 9.30 release?

The Commerce online SDK version 9.30 release includes an update from the deprecated [Applications Insights SDK](https://www.npmjs.com/package/applicationinsights-js) to the newer [Microsoft Application Insights JavaScript SDK - Web](https://www.npmjs.com/package/@microsoft/applicationinsights-web).

The Applications Insights update contains breaking API changes that might affect your customization code if you use these APIs to log telemetry into your Application Insights instance. For more information, see [Upgrading from the old version of Application Insights](https://github.com/microsoft/ApplicationInsights-JS#upgrading-from-the-old-version-of-application-insights).

### What replaces TSLint, which is deprecated in SDK version 1.28 (the Commerce version 10.0.18 release)?

Because the open-source TSLint static analysis tool is deprecated, the Dynamics 365 Commerce online SDK replaces it with the [ESLint](https://eslint.org/) static analysis tool. TSLint continues to work until SDK version 1.30 (the Commerce version 10.0.20 release). Before SDK version 1.30, you can manually update to ESLint if you want. However, in SDK version 1.30, update to ESLint is enforced.

After the update to SDK version 1.28, you receive a deprecation warning when you run the **yarn** command. You can switch to ESLint at any time afterward. However, you might receive new errors and warnings against your custom code.

If you retrieved the online SDK from GitHub, together with the Commerce 10.0.18 preview release, it contains the required changes to ESLint. No further changes are required. However, if you're updating from an older version of the SDK, you must manually update to ESLint before SDK version 1.30. 

Follow the instructions in this section to manually update from TSLint to ESLint.

#### Replace TSLint with ESLint

After you [update to SDK version 1.28](sdk-updates.md) or later, you must create an ESLint file and change your **package.json** file so that it includes the ESLint dependencies. You must also update the commands so that they use ESLint. You can leave the TSLint dependency in the **package.json** file if you want to use both TSLint and ESLint. After the update to ESLint, you might receive new warnings against your code. You can fix or ignore the warnings as required.

##### Create an .eslintrc.js file

You must add a new file named **.eslintrc.js** to your root SDK folder. (In that folder, you should also see an existing **tslint.json** file.) The **.eslintrc.js** file contains a base rule set that can be extended.

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

If there are other files and directories that you don't want lint rules to be applied to, you can add them to the **ignorePatterns** section.

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

For more information, see the [ESLint documentation](https://eslint.org/docs/latest/).

##### Create a .prettierrc file

Prettier is an opinionated code formatter that you can configure to format your code after you save a file. A .prettierrc file allows you to add new rules for Prettier to use. You must create a **.prettierrc** file in the root SDK folder with the following default settings.

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

If you want to use both TSLint and ESLint, keep the TSLint dependency in your **package.json** file and add the following dependencies in the **devDependencies** section.

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

Although this step is optional, install the ESLint extension for Visual Studio Code. This extension helps identify errors and warnings directly in your editor. Additionally, quick actions let you use comments to ignore linting errors.

You might receive new ESLint errors because all the TSLint errors that were suppressed through TSLint comments are now shown again. You can fix or disable the ESLint errors, and you can choose to ignore the warnings.

If you use `–use-eslint` flags in your code, builds fail when errors occur. However, warnings are ignored.

#### Disable linting in code

You can fix TSLint errors by replacing TSLint disable comments with ESLint disable comments. You can use file find and replace functionality if that approach is easier. However, be sure to verify the results.

Use the following tips:

- Like TSLint warnings, you can disable ESLint warnings by using comments.
- Use `// eslint-disable-next-line <rule1>, <rule2>...` to disable the next line.
- To add a comment that explains why you're disabling a rule, add two hyphens (--) (for example, `// eslint-disable-next-line <rule1> -- Disabling this rule for reasons`).
- Use multiline comments to disable a rule for a whole file (for example, `/* eslint-disable <rule1>, <rule2> */`).

The following table lists common equivalents in TSLint and ESLint.

| TSLint rule | ESLint rule |
|---|---|
| // tslint:disable-next-line:no-any | // eslint-disable-next-line @typescript-eslint/no-explicit-any |
| // tslint:disable:no-any | /\* eslint-disable @typescript-eslint/no-explicit-any \*/ |
| // tslint:disable-next-line:cyclomatic-complexity | // eslint-disable-next-line complexity |
| // tslint:disable-next-line:no-empty | // eslint-disable-next-line no-empty |

#### Continue to lint by using TSLint

If you want to continue linting by using TSLint, add the **–use-tslint** argument in the package.json **build** and **start** commands, as shown in the following example.

```json
"start": "yarn msdyn365b start local --use-tslint",
"build": "yarn msdyn365b build --use-tslint",
"build-prod": "yarn clean && yarn msdyn365b build --use-tslint",
```

> [!NOTE]
> Support for TSLint is limited. Use ESLint whenever possible.

#### Completely disable linting during build time

If you want to completely disable linting during build time, add the **--disable-linter** argument in the **package.json** build command, as shown in the following example.

```json 
"build": "yarn msdyn365b build --disable-linter",
"build:prod": "yarn clean && yarn msdyn365b build --disable-linter",
```

### After upgrading to module library version 9.27 (Commerce version 10.0.17 release), buy box module view extensions might generate a compilation error

The compilation error is caused by code sharing that is related to the product quick view module that was introduced in the Commerce version 10.0.17 release. Because the quick view module shares many functionalities with the buy box module, some common components were moved to a common folder, so that the buy box and quick view modules can share the code.

To fix the compilation error, update any import references in the `buybox.tsx` view file, as shown in the following examples.

This example shows the old code for imports in `buybox.view.tsx`.

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

This example shows the new code for imports in `buybox.view.tsx`.

```typescript
import { IBuyboxAddToCartViewProps, IBuyboxAddToOrderTemplateViewProps, IBuyboxAddToWishlistViewProps, IBuyboxKeyInPriceViewProps, IBuyboxProductConfigureDropdownViewProps, IBuyboxProductConfigureViewProps, IBuyboxProductQuantityViewProps, IBuyboxShopSimilarLookViewProps } from '../../common';
import { IBuyboxViewProps } from './buybox';
import { IBuyboxFindInStoreViewProps } from './components/buybox-find-in-store';
```

### After upgrading to module library version 9.24 (10.0.14 release), cloned modules that use data actions might display the error, "UserAuthorizationException. Customer account number on the request was wrong".

The following [core data actions](core-data-actions.md) have a signature change that moves the user account number parameter to the second parameter instead of the first parameter, and is set as an optional parameter. In most scenarios where the user account number is no longer needed, the data action executes in the context of the current signed-in user. In some custom scenarios where the user account number is different than the user account number of the signed-in user, you can fetch the user account number by using the **get-customer** data action and passing it to the data action.

Core data actions with signature changes include:
 
- **add-address**
- **get-address**
- **get-customer**
- **get-loyalty-card**
- **get-loyalty-transaction-estimation**
- **issue-loyalty**

The module library modules are updated with the correct calling pattern to the preceding data actions, so you don't receive any errors in these modules. However, if one of the modules was previously [cloned](clone-starter-module.md), it still has the older data action signature and displays the following error at runtime: "UserAuthorizationException. Customer account number on the request was wrong." The signatures need to be updated accordingly. One way to resolve this issue is to temporarily clone the module library module again with a new name, then differentiate the new module code with the previously cloned custom module and merge the changes. You can then delete the temporary module.

### After upgrading to module library version 9.23 (10.0.13 release), cloned modules or view extensions that import **CartlineComponent** or **WishListIconComponent** components might display the errors "export 'CartlineComponent' wasn't found in '@msdyn365-commerce/components'" or "export 'WishListIconComponent' wasn't found in '@msdyn365-commerce/components'".

The **CartlineComponent** and **WishListIconComponent** components are renamed to **CartLineItemComponent** and **WishlistIconComponent** respectively. If you use the previous component names in either a cloned module or a view extension, you see the build errors. To fix these errors, update the previous component names to the new component names in the cloned module or view extension code.

## Additional resources

[Core data actions](core-data-actions.md)

[Clone a module library module](clone-starter-module.md)

[Best practices for Dynamics 365 Commerce development](best-practices-dev.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
