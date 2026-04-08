---
title: Build and debug projects
description: This tutorial uses the Fleet Management app to show you how to set breakpoints, modify code, and build the result.
author: pvillads
ms.author: pvillads
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/30/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 5c2378fe-cb34-4a81-a940-57d4e13eb282
---

# Build and debug projects

[!include [banner](../includes/banner.md)]

In this tutorial, you learn how to use the tools in Visual Studio to analyze and debug code in the Fleet Management application. You go through a simple developer scenario in which you set breakpoints, modify some code, and build the result.

## Prerequisites

Previous experience with code and Visual Studio is helpful to get the full benefit of this tutorial. This tutorial requires you to access the environment by using Remote Desktop and that you're provisioned as an administrator on the instance.

## Key concepts

- Use the debugger in Visual Studio to analyze and debug code for your projects.
- When you examine the running application, you can use the standard features of the Visual Studio debugger. These features include modifying values of variables, setting breakpoints, and more.
- IntelliSense and other features of Visual Studio are vital to efficient code editing and comprehension.
- Development is an iterative process. After you make modifications to the code, build the project and test the changes.

## Scenario

The rental company experiences unfortunate events when customers rent cars by using credit cards that are past the expiration dates. You, the developer, are tasked with revising the application to help prevent this situation. You identify the problem by using the debugger in Visual Studio. After you identify the problem, edit some code to implement a fix. Finally, build the project and validate that the fix was successful.

## Run to a breakpoint

1. On the desktop, double-click the Visual Studio shortcut to open the development environment.
1. Open the FleetManagement solution. On the **File** menu, point to **Open**, and then click **Project/Solution**.
1. Browse to the desktop, and then open the **FleetManagement** folder. If the solution file isn't on your computer, the steps to create it are listed in [End-to-end scenario for the Fleet Management sample application](fleet-management-sample.md).
1. Select the file named **FleetManagement**. The file type listed is SLN File.
1. Click **Open**. Loading the solution might take some time.
1. Make the **FleetManagement** project the startup project. In **Solution Explorer**, right-click the **Fleet Management** project, and choose **Set as StartUp Project** in the context menu.
1. In **Solution Explorer**, double-click the **Fleet Management** project to display its content.
1. Double-click the **Classes** folder of the Fleet Management project. Locate the **FMRentalCheckoutProcessor** class. Right-click this class, and then click **Open**. Alternatively, you can use the solution explorer search bar at the top of the solution explorer window. As you enter the name in the search bar, you see the corresponding artifacts selected in the solution explorer. You can now see the X++ code for the class. This class has a method named **FinalizeRentalCheckout**.
1. Place a breakpoint in this method on the line following the first comment. To do this, click in the margin to the left of the line of code where you want the debugger to pause execution. You can also click anywhere in the line of code, and then press F9. The following illustration shows a breakpoint, which is displayed as a red-filled circle in the margin.

    :::image type="content" source="./media/redcirclemargin_builddebugproj.png" alt-text="Screenshot of a breakpoint displayed as a red-filled circle in the margin of the FMRentalCheckoutProcessor class.":::

    The FinalizeRentalCheckout method is called when a rental transaction is saved. This method calls the delegate named RentalTransactionAboutTobeFinalizedEvent. You can implement an event handler method, which is called by this delegate. The method that calls the delegate passes a parameter, named RentalConfirmation, which contains a value that indicates whether the rental should be allowed or blocked. If the rental is allowed, the value contains "true"; if it's blocked, the value contains "false". An event handler can change this value, based on any test the developer chooses to implement in code. In this case, you modify the code to test the expiration date of the credit card.

1. Press F5 to start the application for debugging, or, on the **Debug** menu, click **Start Debugging**. It's important that you start the application in one of these ways. If you don't, the Visual Studio debugger won't start, so you won't hit any of the breakpoints you set. **Note**: The debugger needs to relate code position to source positions. It does this through consuming PDB files produced alongside the assemblies and net modules. The debugger loads symbols from the PDB files as described in the settings in the global tools settings. To open the options page containing the setting that controls which symbols load, go to the **Tools** menu and choose **Options**. In the **Microsoft Dynamics 365 Finance** group, select the **Debugging** page. If this option is selected, the system loads symbols from only the PDB files related to the artifacts in the current solution. This selection reduces the startup time significantly, so be sure it’s selected for this lab. Be aware that when this option is selected, it isn’t possible to see source code from entities outside of the current solution. After a few moments, the browser starts and displays the startup object that you selected in the project.
1. The **Current Rentals** page opens.
    1. In the Action Pane, click **Edit**.
    1. When the page is displayed, click **Show list** in the **Show/Hide** list (or press **Ctrl+F8**).
1. Make a change to any existing rental. For example, click **Edit**, and change the time that the rental period started.
1. Click **Save** to force a validation of the rental record. The method in which you placed a breakpoint is called. Execution pauses at the line of code that contains the breakpoint.

    :::image type="content" source="./media/forcevalidation_builddebugproj.png" alt-text="Screenshot of execution paused at a breakpoint in Visual Studio.":::

    While the application is paused at a breakpoint, you can examine the application state. Use the same techniques that you typically use for any application developed with Visual Studio. For example, place the cursor over a variable or a parameter to see its value in a tooltip.

    :::image type="content" source="./media/tooltip_builddebugproj.png" alt-text="Screenshot of a tooltip showing a variable value while execution is paused at a breakpoint.":::

1. The other debugging tools in Visual Studio are available as well. For example, the **Locals** window shows all of the local variables for the location where execution stopped. Click the **Locals** tab at the bottom of Visual Studio, and expand the **fmrentalrecord** variable. You see the internal state of the record, showing the values of all the fields in the record.

    :::image type="content" source="./media/internalstate_builddebugproj.png" alt-text="Screenshot of the Locals window showing the internal state of the fmrentalrecord variable."::: 

    Notice the value of the **Vehicle** property of the **fmrentalrecord** variable. This property is a foreign key field in the **FMRental** table. The debugger allows you to peek into the related record in the FMVehicle table. It shows values that belong to the **AutoIdentification** field group.
1. The **Breakpoints** window lists all of the breakpoints that you set. Click the **Breakpoints** tab to see its content.

    :::image type="content" source="./media/breakpoint_builddebugproj.png" alt-text="Screenshot of the Breakpoints window listing all breakpoints that have been set.":::

1. Press F10 a few times to step through the code, line-by-line, and use the full complement of debugger features. Notice that the **Locals** window updates the values of variables immediately with each statement that's executed.
1. On the toolbar, click **Continue**, or press F5
1. Close Microsoft Edge to close the **Fleet Management** application. Visual Studio exits the debugging mode. An alternative is to choose **Stop Debugging** from the **Debug** menu. This choice leaves Microsoft Edge open, so the next debugging session starts faster.

## Add the validation code

In the **FinalizeRentalCheckout** method, you saw that the developer added code to call the delegate that determines the validity of the rental. To solve the problem of expired credit cards, add an event handler that verifies the credit card isn't expired. To simplify the lab, add the handler in the same file that contains the delegate. Use the following code as inspiration. Rather than copying and pasting the code, type it in manually to see the IntelliSense features in action. These features add to the high level of productivity that Visual Studio users expect.

```xpp
[SubscribesTo(classstr(FMRentalCheckoutProcessor), 
    delegatestr(FMRentalCheckoutProcessor, RentalTransactionAboutTobeFinalizedEvent))]
public static void RentalFinalizedEventHandler(FMRental rentalrecord, Struct rentalConfirmation)
{
    FMPaymentInformation paymentInfo;
    date ccExpiryDate, lastDayOfExpiryMonth;
    str s;

    select firstonly * from paymentInfo where paymentinfo.RecId == rentalRecord.PaymentInformationId;

    if (paymentInfo)
    {
        // Check if the payment info is valid
        // For now, we will check if the credit card is expired
        // Credit cards expire on the last day of the month indicated
        ccExpiryDate = mkdate(1, str2int(paymentInfo.ExpirationMonth), paymentInfo.ExpirationYear);
        lastDayOfExpiryMonth = endmth(ccExpiryDate);

        if (lastDayOfExpiryMonth < today())
        {
            rentalConfirmation.value('OktoRent', false);
            s = "Credit card validation failed for rental ";
        }
        else
        {
            s = "Credit card validation succeeded for rental ";
        }

        info (s + rentalrecord.RentalId);
    }
    else
    {
        rentalConfirmation.value('OktoRent', false);
        info ("No Credit card available for " + rentalrecord.RentalId);
    }
}
```

The preceding code is straightforward. Mark the method as a handler for the relevant delegate by using the **SubscribesTo** attribute, as shown. In the code, the customer record is retrieved, and then the credit card date is compared to today's date. If the expiration date of the credit card is in the past, the event handler sets a value in the **RentalConfirmation** structure to signal that the customer isn't eligible to rent a vehicle. The idea is that any number of handlers can subscribe to the delegate. If any handler determines that a rental shouldn't proceed, it sets the **OkToRent** flag to false. A superior implementation might refrain from doing any analysis if it determines that the **OkToRent** flag is already set to false.

1. Be sure that you're working in the FMRentalCheckoutProcessor.xpp file. Begin by adding the new event handler definition to the FMRentalCheckoutProcessor class. Add the following code on an empty line just above the brace (}) that marks the end of the class definition.

    ```xpp
    public static void RentalFinalizedEventHandler(FMRental rentalrecord, Struct rentalConfirmation)
    {

    }
    ```

1. Add the attributes to the beginning of the event handler. These attributes indicate which delegate the event handler is subscribing to.

    ```xpp
        [SubscribesTo(classstr(FMRentalCheckoutProcessor),
            delegatestr(FMRentalCheckoutProcessor, RentalTransactionAboutTobeFinalizedEvent))]
            public static void RentalFinalizedEventHandler(FMRental rentalrecord, Struct 
                                                                           RentalConfirmation)
        {

        }
    ```

1. Add the code that checks the credit card expiration value. The completed method should look similar to the following code.

    ```xpp
    [SubscribesTo(classstr(FMRentalCheckoutProcessor), 
        delegatestr(FMRentalCheckoutProcessor, RentalTransactionAboutTobeFinalizedEvent))]
    public static void RentalFinalizedEventHandler(FMRental rentalrecord, Struct rentalConfirmation)
    {
        FMPaymentInformation paymentInfo;
        date ccExpiryDate, lastDayOfExpiryMonth;
        str s;

        select firstonly * from PaymentInfo where paymentinfo.RecId == rentalRecord.PaymentInformationId;

        if (paymentInfo)
        {
            // Check if the payment info is valid
            // For now we will check if the credit card is expired
            // Credit cards expire on the last day of the month indicated
            ccExpiryDate = mkdate(1, str2int(paymentInfo.ExpirationMonth), paymentInfo.ExpirationYear);
            lastDayOfExpiryMonth = endmth(ccExpiryDate);

            if (lastDayOfExpiryMonth < today())
            {
                rentalConfirmation.value('OktoRent', false);
                s = "Credit card validation failed for rental ";
            }
            else
            {
                s = "Credit card validation succeeded for rental ";
            }

            info (s + rentalrecord.RentalId);
        }
        else
        {
            rentalConfirmation.value('OktoRent', false);
            info ("No Credit card available for " + rentalrecord.RentalId);
        }
    }
    ```

1. Make sure the handler and the delegate are separated by exactly one blank line.
1. On the toolbar in Visual Studio, click **Save**.
1. After you're satisfied with the code, build the code for the Fleet Management project. To do this, in **Solution Explorer**, right-click the **FleetManagement** project name, and then click **Build**. You might see errors or warnings if the code isn't correct. If so, correct the code, and build again until all warnings and errors are resolved. You're now ready to validate that the revision works as intended.
1. On the **Debug** menu, click **Delete All Breakpoints**.
1. Place a new breakpoint in the event-handler method at the line that contains the following statement:

    ```xpp
    if (lastDayOfExpiryMonth < today())
    ```

1. Start the Fleet Management sample with debugging active by pressing F5.
1. Browse to the **Current rentals** page, as described starting in step 11 of the previous section. Select one of the reservations, and click **Edit**.
1. In the **Customer** drop-down list, select Adrian Lannin from the list, and then click **Save**. Execution pauses at the breakpoint that you set in the event-handler method.
1. Press F10 three times to step through the code block.

    :::image type="content" source="./media/stepcodeblock_builddebugproj.png" alt-text="Screenshot of stepping through a code block in Visual Studio."::: 

1. Press F5 to continue. You see that the customer is disallowed.
1. In the same rental, change the customer name to Phil Spencer, and then click **Update**. This time, the transaction is allowed.
1. Close Microsoft Edge.
1. Comment out the **SubscribesTo** attribute on the **RentalFinalizedEventHandler** method. This step ensures that the credit card test no longer runs as you work on the remaining tutorials.

## Best practices

Earlier in this tutorial, you added code to the project and built the solution with your changes. The build process might not have been successful, so you needed to refer to the error window. By using this window, you can go to the error by clicking on the line that describes the error. You might notice some diagnostic messages that don't represent compilation errors. These messages come from the **Best Practice** checker. This tool checks for instances where the developer violates a known best practice, and it displays a warning when it finds one. The Best Practice rules apply to both code constructs and metadata. Each software development organization likely has its own set of best practices that it enforces. The organization might want to disregard some of the existing best practice checks. To support this action, individual developers can modify the set of reported best practice diagnostics. To demonstrate this process, complete the following steps:

1. On the **View** menu, select **Error List**. You should see a small number of best practice warnings.
1. On the **Dynamics 365** menu, select **Options**. In the **Dynamics 365** group, choose **Best Practices**.
1. In the **Model** drop-down list, make sure that the **Fleet Management** model is selected. The best practice rules apply to a particular model.
1. Select some of the sets of Best Practice rules. For example, if you select the entry for **CodeStyleRules**, the best practice guidelines for variables are examined. After you update the selections, select **OK**.
1. Rebuild the Fleet Management project by right-clicking the project name and then selecting **Rebuild**. You see that the violations of the best practice rules that you specified appear in the **Error list** window.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
