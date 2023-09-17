---
title: Create a SubmitToWorkflow class
description: This article describes how to create a SubmitToWorkflow class.
author: josaw1
ms.date: 06/19/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.custom: 202694
ms.assetid: 33349e0d-d8ac-4d20-8f9b-5f85d4e01004
---

# Create a SubmitToWorkflow class 

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

A workflow is started when the user selects the **Submit** button on the workflow toolbar. The **Submit** button is bound to an action menu item that calls the **main** method of a class that you create to activate a workflow. This article describes how to create a **SubmitToWorkflow** class and use the name of the workflow type to activate the workflow.

You can also activate a workflow by using the workflow configuration ID or the workflow sequence number. The basic procedure is the same. For more information, see [Activating a workflow](/dynamicsax-2012/developer/activating-a-workflow).

> [!NOTE]
> If you used the **Workflow** wizard to create the workflow type, the wizard has already created a workflow submission manager class. You just have to add code to it.

## Create a SubmitToWorkflow class

1. In Application Explorer, expand the **Classes** node.
2. Right-click the **Classes** node, and then select **New Class**. A class group appears under the **Classes** node.
3. Right-click the new class, and then select **New Method**. A new method node appears under the **Classes** node.
4. Right-click the new method, and then select **Edit**.
5. Enter the following code for the **main** method to use the name of the workflow type to activate the workflow.

    > [!NOTE]
    > This example applies to workflow submissions. For an example that also works with Enterprise Portal, see [Adding enterprise portal support for workflow submission](/dynamicsax-2012/developer/adding-enterprise-portal-support-for-workflow-submission).

    ```X++
    public static void main(Args args)
    {
        // Variable declaration.
        recId _recId = args.record().RecId;
        WorkflowCorrelationId _workflowCorrelationId;
        // Hardcoded workflow type name.
        WorkflowTypeName _workflowTypeName = workflowtypestr("MyWorkflowType");
        // Initial note is the information that users enter when they
        // submit the document for workflow.
        WorkflowComment _initialNote = "";
        WorkflowSubmitDialog workflowSubmitDialog;
        // Opens the submit to workflow dialog box for user comments.
        workflowSubmitDialog = WorkflowSubmitDialog::construct(args.caller().getActiveWorkflowConfiguration());
        workflowSubmitDialog.run();
        if (workflowSubmitDialog.parmIsClosedOK())
        {
            _recId = args.record().RecId;
            // Get user comments from the submit to workflow dialog box.
            _initialNote = workflowSubmitDialog.parmWorkflowComment();
            try
            {
                ttsbegin;
                // Activate the workflow from a template.
                _workflowCorrelationId = Workflow::activateFromWorkflowType(_workflowTypeName, _recId, _initialNote, NoYes::No);
                ttscommit;
                // Updates the workflow button to display Actions instead of Submit.
                args.caller().updateWorkflowControls();
            }
            catch(exception::Error)
            {
                // ToDo Insert your error code here.
            }
        }
    }
    ```

6. Close the **Editor** window, and select **Yes** to save your changes.

    > [!NOTE]
    > When you save this code, you will receive an "Empty compound statement" warning message in the **Compiler Output** window unless you add valid code in the **catch(exception::Error)** block.

## See also

[Activating a workflow](/dynamicsax-2012/developer/activating-a-workflow)

[Create a new workflow type](workflow-type-create-new.md)

[Workflow::activateFromWorkflowType method](/previous-versions/dynamics/ax-2012/application-classes/gg812416(v=ax.60))

[Workflow::activateFromWorkflowSequenceNumber method](/previous-versions/dynamics/ax-2012/application-classes/gg812415(v=ax.60))

[Workflow::activateFromWorkflowConfigurationId method](/previous-versions/dynamics/ax-2012/application-classes/gg812414(v=ax.60))


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
