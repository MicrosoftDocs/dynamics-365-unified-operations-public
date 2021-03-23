---
# required metadata

title: Debugging best practices for Dynamics 365 Commerce development 
description: This topic describes some best practices to follow when debugging Dynamics 365 Commerce customizations.  
author: samjarawan
manager: annbe
ms.date: 02/11/2021
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
# Debugging best practices for Dynamics 365 Commerce development 

[!include [banner](../includes/banner.md)]

This topic describes some best practices to follow when debugging Dynamics 365 Commerce customizations. 


## Stepping through code in a modern browser on localhost
An easy way to debug code is to use a modern browsers debugger and stepping through code such as a module or data action that is normally run on the server side.  This can be done if you have set up a local development environment as found in the [Set up a development environment](setup-dev-environment.md) article and are using a Chromium based browser such as Edge or Chrome.

First, you will want to identify the breakpoints in your code or where you would like to start stepping through the code. To create a breakpoint in your code, add the **debugger** statement. 

For example, if we want to debug a data action that is running server side and we want to insert a breakpoint right before we make an API call that creates the Cart. To do this we would insert the debugger statement before making this API call as shown in the following image:

![Adding debugger to code](media/debugging-best-practices-1.png)

The next step is to start the local Node server in debug mode using the **yarn start --inspect-brk** command.

![Start Node in debug mode](media/debugging-best-practices-2.png)

Once it is finished building and the Node server is running you should see similar output to below indicating that the debugger is listening:

![Node listening](media/debugging-best-practices-3.png)


At this point the local Chrome DevTools can be opened up.  In the browser you can navigate to ```edge://inspect``` or ```chrome://inspect``` depending on the browser you are using.  After a few seconds you should see a **Target** listed similar to below:

![DevTools inspect](media/debugging-best-practices-4.png)

Hitting the inspect link will attach the DevTools to your node server and bring up a debugging window. By default, the debugger will be paused before the node server starts accepting requests, so go ahead and resume script execution by clicking on ‘resume script execution’.

![Resume script execution](media/debugging-best-practices-5.png)

The local Node server is now ready to handle requests. Next navigate to the page or module mock that will call the action and the breakpoin withh be triggered.

![Debugger breakpoint hit](media/debugging-best-practices-6.png)

The breakpoint has been triggered. From here we can step through the code and debug as necessary.
You may also add additional breakpoints in this file or in any other files by clicking on the line numbers. These breakpoints will get triggered on the next request.

## Using Fiddler to capture network requests

To enable Fiddler to capture network requests, startup Fiddler before you start your node server in local dev mode.  You will then need to enable Fiddler to [capture HTTPS traffic](https://docs.telerik.com/fiddler/configure-fiddler/tasks/decrypthttps). Once that is complete, start your node server using `yarn start`.
Navigate to any page on localhost and add the query string parameter `debug=true`, you will see a popup in Fiddler about the certificate not being validated.  Select the "Ignore erorrs (unsafe) and proceed" option. You should now be able to intercept and inspect network requests the Node server is making.

## Accessing debug data through the browser console window
In your browser once the page loads, you can use the Console tab in your web debugger to examine information about page state that might be useful for debugging.

### Initial Data

The ```___initialData___``` object provides information about the modules that were loaded, the request context and cache information that was computed during server-side render. 
To access this information, open the console tab in the web debugger and type in ```___initialData___``` and hit enter to reveal this debug information. In the request context object you can check your SDK version and starter-kit version (if installed).

![Debug data](media/debugging-best-practices-7.png)

### _msdyn365
The _msdyn365 also provided additional debug information in the debug console. This object contains request details after the client-render has also completed. It can be useful to check if there are any differences between _msdyn365 and ___initialData___ to see if there is a mismatch between server and client-side renders.


## Useful query strings
The online SDK provides a handful of query strings that can be appended to any page to gather debugging information.

### Debug query string
Adding the query string ```?debug=true``` turns on debug mode and displays module errors. In addition, if this query string is added to a request that is hitting your local dev server, the server-side action calls will show up in a network debugging tool such as Fiddler.

### Node service proxy query string
Adding the query string ```?item=nodeserviceproxy:true``` will return the raw page context in JSON format provided by the platform. This can be useful to determine which modules that page is rendering in as well as checking request context properties. 

### Lazy load module query string
Adding the query string ```setswitch=node_lazyload_{module | all}``` will force a module (or all modules) to be loaded client side. When hitting a production url, the server-side actions are abstracted away from the browser causing these requests to not show up in browser’s networking tab. When this query string is applied the actions and modules will be forced to load client-side at which point you can use a networking tool such as Fiddler or the Chrome network tab to track the data-actions requests a module is making. 


## Help with common issues

### My module is not loading
1.	Try loading the page with the debug=true query string parameter. If the module has any errors, it will log the error there. If the error module displays an error the most likely case is the module is misconfigured. Contact the module author to debug further.
2.	If no error module loads check that the module is in the page context. Add the item=nodeserviceproxy:true flag to see if it is present. If the module is not present update the page in tooling or your pagemock
3.	If the module is present, verify that it is registered. Check your server for any build errors or the versions page to see if your module is registered.

### My data action is not firing
1.	Load the action client side so you can check the API calls in your browser's network tab using the lazyload switch.
2.	If the network call you expect is not executing but a breakpoint in your action using the JavaScript debugger. You should be able to trace what is happening.
3.	If the debugger is never triggered verify that your module definition includes the expected action chain.

## Other tips and tricks
*	You may use console.trace() statements to print debug information to the console. One thing to note is that if these console.trace() statements are in server-side actions, these logs will not show up in the browser or console unless the debugger is attached to the running node process.
*	It can be helpful sometimes to run yarn –force to force yarn to fetch the latest packages even if they’ve already been installed
*	To perform a clean install, remove the node_modules, yarn.lock file and run yarn cache clean before running yarn.


## Additional resources

[Dynamics 365 Commerce architecture overview](../commerce-architecture.md)

[Online channel extensibility overview](overview.md)

[System requirements](system-requirements.md)

[Set up a development environment](setup-dev-environment.md)

[best-practices-dev](best-practices-dev.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
