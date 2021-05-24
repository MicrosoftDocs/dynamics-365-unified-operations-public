---
# required metadata

title: Preview and debug a module
description: This topic describes how to test a module by previewing and debugging it in a web browser.
author: samjarawan
ms.date: 09/15/2020
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
# Preview and debug a module

[!include [banner](../includes/banner.md)]

This topic describes how to test a module by previewing and debugging it in a web browser.

During development of a module, you can preview and debug the module in your local web browser.

## Preview a module

To preview a module in a local web browser, follow these steps.

1. At a command prompt, go to your root SDK folder, and run the **yarn start** command. Here is an example.

    ```Console
    c:\repos\Msdyn365.Commerce.Online\yarn start
    ```

1. In a web browser, open the following URL to view the module: `https://localhost:4000/modules?type=product-feature`. Notice the module name in the **type=MODULE\_NAME** query string parameter. This parameter is shorthand for **type=:MODULE\_NAME:MOCK\_FILE\_NAME**, where the default mock file that matches the name of the module is loaded. Therefore, the preceding URL is equivalent to `https://localhost:4000/modules?type=product-feature:product-feature`.

By adding **&debug=true**, you can get more verbose debug information in the Yarn output window, and the browser will show the details of any error details that occur.

`https://localhost:4000/modules?type=product-feature&debug=true`

## Debug a module

A debugger can be attached to both the client and the server. Sometimes, you might have to use both methods.

### Debug the client (browser)

You can debug in the browser in two ways:

- Add a **debugger;** statement in your code, and then open the developer tools window in your browser. (In modern browsers, you can typically open the developer tools by pressing the **F12** key.) Your breakpoint should be hit, and you can then use the debugging capabilities of your web browser (for example, watch, locals, or expression evaluation).
- Open the developer tools window, and open the file where you want to set a breakpoint. Depending on your browser, you might be able to use the **Ctrl+P** keyboard shortcut to go to the file and show full source maps. After you set a breakpoint at the desired line number and refresh the page, execution should pause at that breakpoint.

### Debug the server (Node.js)

#### Open debugging tools

Node.js includes dedicated tools that let you attach a debugger to a running application.

To open debugging tools in Google Chrome, go to **chrome://inspect**.

From the view that is opened, you can attach a debugger to the running Node.js applications that expect a debugger to connect. Keep this view open while you attach the debugger.

#### Attach the debugger

To inform Node.js that you want to attach a debugger, start your application by using the following command.

```Console
yarn start --inspect-brk
```

As you can see, the **inspect-brk** argument is added to the regular **start** command. After the application is compiled, a message that resembles the following message should appear in your console: "Waiting for debugger..."

The previously opened window should gain focus. The application isn't actually run until you select **Play** in the debugging window. After you allow the application to continue, you can set breakpoints by using the methods that are described in the [Debug the client (browser)](#debug-the-client-browser) section earlier in this topic.

### Additional reading

- [Documentation for debugging Node.js in Microsoft Visual Studio Code (VS Code)](https://code.visualstudio.com/docs/nodejs/nodejs-debugging)

### Troubleshooting

- If the debugger doesn't stop at the breakpoint that you set, it's usually a good idea to restart the server. In this way, you help guarantee that you have a clean build, because the Hot Module Replacement (HMR) functionality doesn't always achieve the best results.
- Sometimes, the transpiled code (TypeScript to JavaScript) makes debugging more challenging, and you must review the raw JavaScript to understand the code that is running. In these cases, you should turn off JavaScript source maps and follow standard instructions for adding breakpoints in JavaScript code.
- If you're debugging a node, make sure that the debugging port is configured for auto-connection by using the dedicated DevTools for Node.js.

## Additional resources

[Create a new module](create-new-module.md)

[Clone a module library module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Test modules by using module mocks](test-module-mock.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)

[Localize a module](localize-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
