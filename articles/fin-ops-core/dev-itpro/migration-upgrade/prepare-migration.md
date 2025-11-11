---
title: Prepare to migrate code to finance and operations
description: Learn about how the code upgrade service and Visual Studio tools help you migrate from Dynamics AX 2012 R3 to finance and operations.
author: johnmichalak
ms.author: johnmichalak
ms.topic: upgrade-and-migration-article
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: a911b0f2-a7b0-4643-bf5b-16e55c9397be
---

# Prepare to migrate code to finance and operations

[!include [banner](../includes/banner.md)]

This article describes how the Lifecycle Services code upgrade service and Visual Studio tools help you migrate your code and metadata from Dynamics AX 2012 R3 to finance and operations. Most of these steps also apply to code migration between two major versions of finance and operations. 

## Prerequisites

You need access to a finance and operations development environment by using Remote Desktop, and you must be provisioned as an administrator on the instance. We recommend you become familiar with some of the Finance and Operations development, customization, and user interface concepts before you upgrade your code. Here are some references.

-   [Development tools](../dev-tools/developer-home-page.md)
-   [Models and packages](../dev-tools/models.md)
-   [X++ programming language](../dev-ref/xpp-language-reference.md)
-   [Extensions and Overlayering](../extensibility/extensibility-home-page.md)
-   [User interface development](../user-interface/user-interface-development-home-page.md)

## Overview of the code migration process
### Model split

The finance and operations apps are split into several packages, or assemblies: 

**Platform packages**

-   Application Platform
-   Application Foundation
-   Test Essentials

**Application packages**

-   Application Suite
-   Other application packages

ISV and customer code that you migrate from Dynamics AX 2012 R3 is rebaselined into the correct package.

### Automigration using the Lifecycle Services Code Upgrade service

The Lifecycle Services code upgrade service takes a Dynamics AX 2012 R3 model store as input and completes the following tasks:

-   Converts metadata into the latest format.
-   Rebaselines metadata by moving and merging it into the right model.
-   Provides an estimation to help you understand the effort required to upgrade the solution.
-   Runs migration rules that automigrate parts of a solution.
-   Runs migration rules that inform developers what to manually fix by using TODOs.
-   Automatically checks in the upgraded solution into your Azure DevOps project.

To configure and run the code upgrade service, see [Configure the code upgrade service in Lifecycle Services](../lifecycle-services/configure-execute-code-upgrade.md).

### Manual migration steps

After you upgrade your code by using the Lifecycle Services code upgrade service, configure your developer VM and Azure DevOps to connect to the upgraded code branch.

-   [Configure one-box development environments](../dev-tools/configure-developer-vm.md)
-   [Configure the Azure DevOps mapping during code migration](configure-vso-solution.md)

The code upgrade service provides Visual Studio solutions that you can open to compile your code. It provides a **code merge** solution for all elements that contain conflicts and an **upgraded** solution for all your upgraded elements. Typically, you can compile the application by fixing compilation errors in the order shown in the following list. The order is determined based on the package dependencies graph, starting with the lowest package in the graph. To determine package dependencies, see [Models and packages](../dev-tools/models.md). A typical order is Application Platform, Application Foundation, Directory, and Application Suite. For each of your upgraded models:

-   Fix merge conflicts.
-   Fix compilation errors related to a model split (references across packages).
    -   Typical error messages are:
        -   &lt;Element Type&gt; X refers to &lt;Element Type&gt; Y, which doesn't exist.
        -   The name &lt;Name&gt; doesn't denote a class, a table, or an extended data type.
    -   For example, your overlayering customizations might reference elements or code that are higher in the package dependency graph:
        -   A method in the Directory model references a table in the Application Suite package.
        -   A form in the Directory package references a data source in the Application Suite package.
    -   You need to refactor your code to address these dependencies by moving model elements or business logic to higher level packages.
    -   [Solve dependencies among models by using delegates during code migration](delegates-migration.md) describes how to use delegates to solve some of these issues.
-   Fix compilation errors.

After you resolve all of the compilation errors, all packages compile. Next, complete the following tasks:

1.  Address guided code upgrade TODOs and code upgrade-specific best practice warnings. Some examples and details are in the sections that follow.
1.  Replace deprecated controls, such as ActiveX, or find an alternative.
1.  Apply form patterns and subpatterns to all forms.
1.  Validate that all scenarios work in multiple browsers with different sizes for custom patterns.
1.  Write and run tests.

## Best practice setup
In the Best Practice framework, you need to resolve a subset of Best Practice warnings to complete migration. This requirement applies if you're migrating from Dynamics AX 2012 R3 or earlier.

1.  In Visual Studio, select **Dynamics 365 &gt; Options &gt; Best Practices**.
1.  In the **Model** drop-down menu, select **Application Suite** (Repeat with all models you're working on)

Set these rules to "ON" while migrating your solution. An XML file in the AxRuleSet folder drives the setting. For example, see the Application Suite xml file, BPRules.xml, located under C:\\Packages\\ApplicationSuite\\Foundation\\AxRuleSet. 

:::image type="content" source="./media/bpupgraderules.png" alt-text="Screenshot of bpupgraderules.":::

To complete the migration, you need to fix all migration-specific Best Practice rules. The errors show up in the error list as warnings. In the error list, you see compiler warnings and best practice errors. Best Practice errors are prefixed with the text **BP**. For example, **BPErrorFormControlPatternUnspecified**.

## Debugging
By default, finance and operations optimizes the debugging experience for the files that you're working on. As a result, when you step into a file (F11) that isn't in your project, the PDBs aren't loaded and you can't debug the code. To work around this issue, change the project debugging setting by selecting <strong>Dynamics 365 **&gt; **Options</strong> &gt; <strong>Debugging</strong>. Verify that the <strong>Load symbols only for items in the solution</strong> check box isn't selected. This option is selected by default because it significantly improves the debugger speed. Another debugging setting that you might want to turn off is Intellitrace. Intellitrace collects the complete execution history of an application. It creates a lot of noise in the IDE when debugging. To turn off Intellitrace, select <strong>Options</strong> &gt; <strong>IntelliTrace</strong> &gt; <strong>Enable IntelliTrace</strong>, clear the check box, and then select <strong>OK</strong>. Intellitrace is only available in the Enterprise version of Visual Studio.  

## Address code migration tasks
When you migrate metadata to finance and operations apps, multiple autoupgrade scripts run. In the case where developers need to complete manual migration tasks, To-dos and Best Practices (BP) are added.

-   To-dos are prefixed with `/* TODO: (Code Upgrade)`, and need to be fixed as a part of code migration.
-   BP migration specific rules also need to be fixed as part of code migration.

The following example uses the **PurchCommitment\_PSN** form to walk you through the migration task of fixing navigation. Specifically, you see examples of duplicate buttons and Action Pane TODOs.

### Setup

1.  In Visual Studio, open **Application Explorer**, and search for the form, PurchCommitment\_PSN.
1.  Select **OK**.
1.  Right-click the project and select **Properties**.
1.  In the Model property, select **Application Suite**.
1.  In the Company property, select FRSI.
1.  Note: The form is located in the French demo data company FRSI.
1.  Press **Ctrl+F5** to see the form.

While the form looks complete, you still need to complete code migration tasks. 

:::image type="content" source="./media/i1.png" alt-text="Screenshot of i.":::

### Navigation migration tasks

1.  In Visual Studio, build the project, then on the toolbar, select **View** &gt; **Task List**.
1.  Select the **Comments** drop-down list to view the TO DO: (Code Upgrade) tasks.
1.  In the list, find the ActionPane TODOs.

:::image type="content" source="./media/j1.png" alt-text="Screenshot of j.":::

### Code upgrade rule - Action Pane

In finance and operations apps, the system provides the following core actions as system-defined buttons:

-   New
-   Delete
-   Edit
-   Export

As part of the automigration process, the Action Pane rule runs to identify redundant buttons. To complete this part of migration, you need to manually:

-   Remove or move the code.
-   Delete redundant controls in the application code.

> [!NOTE]
> In the section below, we provide examples of how to migrate and modify the code on modeled buttons that replicate system-defined buttons. However, in practice, before making changes similar to those made in this article, evaluate the code with respect to the scenario to determine if it's still needed.

First, fix the TODO for the DeleteCmdButton, which duplicates the system-defined Delete button.

1.  In Visual Studio, find the TODO shown in the following image, and then double-click the TODO.

    :::image type="content" source="./media/k1.png" alt-text="Screenshot of k.":::

1.  Replace the TODO and the line of code as shown in the following image.
    -   The state of the system-defined **Delete** button is controlled by the AllowDelete property on the firstmaster datasource. By setting AllowDelete to false, the delete task doesn't execute when the keyboard shortcut is used.

        ```xpp
        // Delete button
        /* TODO: (Code Upgrade) [Action Pane Rule] Please consider moving all references to the form task override method and remove the control: DeleteCmdButton */
        deleteCmdButton.enabled(purchCommitmentHeader && purchCommitmentHeader.canDelete());
        PurchCommitmentHeader_DS.allowDelete(purchCommitmentHeader && purchCommitmentHeader.canDelete());
        ```

1.  In the editor, find and remove DeleteCmdButton from the form design. 

    :::image type="content" source="./media/l1.png" alt-text="Screenshot of l.":::

1.  Press **Ctrl+S** to save the form.
    -   Next, focus on the EditCmdButton that duplicates the system Edit button, handling the two TODOs associated with this button and removing this button.

1.  In Visual Studio, find the TODO shown in the following image, and then double-click the TODO.

    :::image type="content" source="./media/m1.png" alt-text="Screenshot of m.":::

1.  Because the visibility of the **Edit** button is controlled by the View/Edit mode of the form, you need to modify this code so it sets that property. Replace the TODO and the line of code as shown in the following graphic.

    ```xpp
    /* TODO: (Code Upgrade) [Action Pane Rule] Please consider moving all references to the form task override method and remove the control: EditCmdButton */
    editCmdButton.enabled(purchCommitmentHeader && isInDraftOrUnderRevisionStatus && !isInWorkFlowReviewState && !isLineReferenced);

    if(purchCommitmentHeader && isInDraftOrUnderRevisionStatus && !isInWorkFlowReviewState && !isLineReferenced)
    {
        element.design().ViewEditMode(ViewEditMode::Auto);
    }
    else
    {
        element.design().ViewEditMode(ViewEditMode::View);

    }
    ```

1.  Double-click the other TODO for this button.

    :::image type="content" source="./media/n1.png" alt-text="Screenshot of n.":::

1.  Inspect the code on the modeled **Edit** button. You need to move this logic to the form's task() method.

    ```xpp
    [Control("CommandButton")]
    class EditCmdButton
    {
        /* TODO: (Code Upgrade) [Action Pane Rule] Please consider moving this button code to the task override method and remove the control EditCmdButton. */
        void clicked()
        {
            if (purchCommitmentHeader.WorkflowApprovalState ==     
                PurchCommitmentWorkflowApprovalState_PSN::Approved)
            {
                if (Box::yesNo(strFmt("@SPS2140", purchCommitmentHeader.CommitmentNumber), 
                    DialogButton::No) == DialogButton::Yes)
                {
                    super();

                    PurchCommitmentHeader_PSN::setWorkflowState(purchCommitmentHeader.RecId, 
                        PurchCommitmentWorkflowApprovalState_PSN::NotSubmitted);
                }
            }
            else
            {
                super();
            }
        }
    }
    ```

1.  On the left side of the Visual Studio designer, right-click **Methods** &gt; **Override**, and select **Task**, to add an override for the form's Task method.
1.  Update the task method as shown in the following code so that the code from the previous step is triggered when the system-defined **Edit** button is clicked.

    ```xpp
    /// 
        ///
        /// 
        /// 
        /// 
        public int task(int _taskId)
        {
            #Task
            int ret;

            switch (_taskId)
            {
                case #taskEditRecord:

                    if (purchCommitmentHeader.WorkflowApprovalState == PurchCommitmentWorkflowApprovalState_PSN::Approved)
                    {
                        if (Box::yesNo(strFmt("@SPS2140", purchCommitmentHeader.CommitmentNumber), DialogButton::No) == DialogButton::Yes)
                        {
                            ret = super(_taskId);

                            PurchCommitmentHeader_PSN::setWorkflowState(purchCommitmentHeader.RecId, PurchCommitmentWorkflowApprovalState_PSN::NotSubmitted);
                        }
                    }
                    else
                    {
                        ret = super(_taskId);
                    }

                    break;

                default:
                    ret = super(_taskId);
                    break;
            }

            return ret;
        }
    ```

1.  In the Editor, find and remove the **EditCmdButton** from the form design. 

    :::image type="content" source="./media/o1.png" alt-text="Screenshot of o.":::

1.  Press **Ctrl+S** to save the form.
1.  Press **Ctrl+F5** to view the form. Notice the **Delete** and **Edit** buttons in the **Commitment** tab are removed.

## Resolve casting exceptions
In finance and operations apps, X++ is completely intermediate-language (IL) based and therefore has stricter runtime type behavior than the interpreted Dynamics AX 2012. This stricter runtime type behavior can generate exceptions in migrated Dynamics AX 2012 R3 metadata. You likely encounter these exceptions during your migration. The casting exceptions can occur in different runtime scenarios, such as down-casting, casting runtime to design time objects, and side-casting. In the following section, we walk through an example where a form, CosJournalName, generates controls at runtime, and has a type mismatch, which causes a .NET exception because it's strongly typed.

### Example: Side-casting exception

1.  In Visual Studio, select and right-click **Project Properties**, and verify that USMF is the default company.
1.  Add the display menu item CosJournalName to your project, and set the menu item as your Startup object.
1.  Add the CosJournalName form to your project.
1.  Add the cosDimCheckBoxController class to your project.
1.  Rebuild your project.
1.  Press **Ctrl+F5** to run the form.
1.  You get an exception, similar to the following, when running the form.

    :::image type="content" source="./media/u1.png" alt-text="Screenshot of u.":::

1.  Right-click the class, cosDimCheckBoxController, and then select **View Code**.
1.  Set a breakpoint on the cosDimCheckBoxController::getBuildControl().
1.  Press **F5**.
    -   The breakpoint is hit. This point is where the casting error occurs. The reason for the casting error is because the code tries to return a control of type `FormBuildCheckboxControl` but the object expects `FormBuildStringControl`.

1.  Hover over the buildcontrol to see the type and notice the differences.

    :::image type="content" source="./media/v1.png" alt-text="Screenshot of v.":::

1.  Press **F10** to hit the exception.

    :::image type="content" source="./media/w2.png" alt-text="Screenshot of w.":::

1.  Stop debugging.
1.  To fix the exception, change the method declaration from `FormBuildStringControl` to `FormBuildCheckBoxControl`.

    ```xpp
    protected FormBuildStringControl getBuildControl()
    protected FormBuildCheckBoxControl getBuildControl()
    ```
    
1.  Rebuild the project, and press **Ctrl+F5**. The form should open successfully because the casting error is resolved.

    :::image type="content" source="./media/a.png" alt-text="Screenshot of a.":::

## Migrating context menus and mouse double-click code
To migrate code from Dynamics AX 2012 that deals with context menus and mouse double-click actions, see the following articles:

-   [Code migration - Context menu code](code-migration-context-menus.md)
-   [Code migration - Mouse double-click logic](code-migration-double-click.md)






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
