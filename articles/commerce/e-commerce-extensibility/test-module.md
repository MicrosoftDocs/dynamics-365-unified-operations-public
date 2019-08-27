---
# required metadata

title: Test a module
description: This topic describes how to test a module by previewing and debugging it in a web browser.
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
# Test a module

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to test a module by previewing and debugging it in a web browser.

## Overview

During development of a module, a module can be previewed and debugged in your local web browser.

## Preview a module

To preview a module in a local web browser, do the following.

1. At a command prompt, go to your root SDK folder and run the **yarn start** command. Here is an example.

    ```
    c:\repos\MyEcommerceSite\yarn start
    ```

1. Open the following URL in a web browser to view the module: `https://localhost:4000/modules?type=productFeature`. Notice the module name in the **"type=MODULE\_NAME"** query string parameter.  This is shorthand for `type=:MODULE_NAME:MOCK_FILE_NAME` where the default mock file matching the name of the module is loaded. In this example, `https://localhost:4000/modules?type=productFeature:productFeature` is the equivalent.

Adding **&debug=true** will provide more verbose debug information in the yarn output window. 
`https://localhost:4000/modules?type=productFeature&debug=true`. 

## Debug a module
A debugger can be attached to both the client and the server, and there are times that you may need to use both methods.

### Debug the client (browser)

You can debug in the browser one of two ways:
- Add a `debugger;` statement in your code and open the developer tools window in your browser (typically F12 across modern browsers). Your breakpoint should hit and you can then proceed to use the debugging capabilities of your browser (for example, watch, locals, or expression evaluation).
- Open the developer tools window and navigate to the file you want to set a breakpoint in. Depending on your browser, you may be able to use the `CTRL + P` shortcut to jump to the file with full source maps. Setting a breakpoint at the desired line number and refreshing the page should pause execution at the desired breakpoint.

### Debug the server (node)

#### Open debugging tools

NodeJS comes with dedicated tools that allow you to attach a debugger to a running application.

To open debugging tools in Google Chrome, do the following.

- Navigate to `chrome://inspect` in your browser

From this view, you will be able to attach a debugger to the running NodeJS applications that expect a debugger to connect. Keep this view open while attaching the debugger.

#### Attach the debugger

In order to let NodeJS know that you want to attach a debugger, start your application with the following command.

```
yarn start --inspect-brk
```

As you can see, the `inspect-brk` argument was added to our normal start command. Once the compilation of the application is complete, you should see a message similar to the following appeaer in your console.

```
Waiting for debugger...
```

The previously opened window should gain focus. The application does not actually run until you click **Play** in the debugging window. Once you allow the application to continue, breakpoints can be set using the two methods described in the Debug the client section above.

### Additional Reading

- [VSCode documentation on debugging nodejs](https://code.visualstudio.com/docs/nodejs/nodejs-debugging)

### Troubleshooting

- If the debugger is not stopping your breakpoint, it is typically a good idea to restart your server to ensure that you have a clean build, since the Hot Module Replacement (HMR) functionality does not always achieve the best results.
- Sometimes the transpiled code (TypeScript to JavaScript) makes debugging more challenging and the raw JavaScript needs to be reviewed to understand the running code. In such cases, you should turn off JavaScript sourcemaps and follow standard instructions for adding breakpoints in JavaScript code.
- If debugging a node, ensure that the debugging port is one that is configured for auto-connection using the `dedicated DevTools for Node`.
