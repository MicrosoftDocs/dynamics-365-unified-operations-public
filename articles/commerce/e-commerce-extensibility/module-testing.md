---
# required metadata

title: Testing a module
description: During development of a module, the module can be previewed and debugged in your local web browser.
author: SamJarawan
manager: annbe
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
# Testing a module
During development of a module, the module can be previewed and debugged in your local web browser.

To preview the new module in a local web browser, follow these steps.

1. At a command prompt, go to your root SDK folder, and run the **yarn start** command. Here is an example.

    ```
    c:\repos\MyEcommerceSite\yarn start
    ```

2. Open the following URL in a web browser to view the module: `https://localhost:4000/modules?type=productFeature`. Notice the module name in the **"type=MODULE\_NAME"** query string parameter.  This is shorthand for `type=:MODULE_NAME:MOCK_FILE_NAME` where the default mock file matching the name of the module is loaded.  In this example, `https://localhost:4000/modules?type=productFeature:productFeature` is equivalent.

Adding **&debug=true** will provide more verbose debug information in the yarn output window: `https://localhost:4000/modules?type=productFeature&debug=true`. 

# Debugging
A debugger can be attached to both the server (node) or the client and at times you might need to do both.  The steps below outlines how to debug on the client and the server.

## Debugging the client (browser)
You may debug in the browser one of two ways:
1. Add a `debugger;` statement in your code and open the Developer Tools window in your browser (typically F12 across modern browsers). Your breakpoint should hit and you can proceed with debugging capabilities of your browser (e.g. watch, locals, expression evaluation)
2. Open the developer tools (typically F12 across modern browsers) and navigate to the file you want to set a breakpoint in. Depending on your browser, you may be able to use the `CTRL + P` shortcut to jump to file with full source maps.  Setting a breakpoint at the desired line number and refreshing the page should break at the desired breakpoint.

## Debugging the server (node)
### Getting started
NodeJS comes with dedicated tools which allow you to attach a debugger to the running application.

In order to open these debugging tools
1. Navigate to `chrome://inspect` in your browser

From this view, you will be able to attach a debugger to the running NodeJS applications that expect a debugger to connect.  Keep this view open while we move on to the next section.

### Attaching the debugger
In order to let NodeJS know that we want to attach a debugger, start your application with the following command:

```
yarn start --inspect-brk
```

As you can see, the `inspect-brk` argument was added to our normal start command.  Once the compilation of the application is complete, you should see a message similar to the following appeaer in your console:

```
Waiting for debugger...
```

The previous window we opened should gain focus.  The application does not actually run until you hit `Play` in the debugging window.  Once you do allow the application to continue, breakpoints can be set via the two methods described in the `Debugging the Client` section.


### Additional Reading
- [VSCode documentation on debugging nodejs](https://code.visualstudio.com/docs/nodejs/nodejs-debugging)

## Troubleshooting
- If the debugger is not stopping your breakpoint, it is typically a good idea to restart your server to ensure you have a clean build as the HMR functionality does not always achieve the best results.
- Sometimes the transpiled code (Typescript to JavaScript) makes debugging more challenging and the raw javascript is needed to be reviewed in order to understand the running code. In such cases, you should turn off JavaScript sourcemaps and follow standard instructions for adding breakpoints in JavaScript code.
- If debugging node, ensure that the debugging port is one that is configured for auto-connection via the `dedicated DevTools for Node`.
