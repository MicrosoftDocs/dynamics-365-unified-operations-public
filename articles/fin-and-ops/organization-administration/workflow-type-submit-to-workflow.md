---
# required metadata

title: Create a SubmitToWorkflow class
description: This topic describes how to create a SubmitToWorkflow class in Dynamics 365 for Finance and Operations.
author: RobinARH
manager: AnnBe
ms.date: 06/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 202694
ms.assetid: 33349e0d-d8ac-4d20-8f9b-5f85d4e01004
ms.search.region: Global
# ms.search.industry: 
ms.author: RobinARH
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Create a SubmitToWorkflow class 

In Finance and operations, a workflow is started when the user clicks the **Submit** button on the workflow toolbar. The **Submit** button is bound to an action menu item that calls the main method on a class that you create to activate a workflow. This topic describes how to create a SubmitToWorkflow class using the workflow type name to activate the workflow.

The same procedure can be used to activate a workflow by using the workflow configuration ID or the workflow sequence number. For more information, see [Activating a workflow](https://docs.microsoft.com/en-us/dynamicsax-2012/developer/activating-a-workflow).


> [!NOTE]
> <P>If you used the Workflow Wizard to create the workflow type, a workflow submit manager class will have already been created by the wizard. You will need to add code to this class.</P>



### To create a SubmitToWorkflow class

1.  In the Application Object Tree (AOT), expand the **Classes** node.

2.  Right-click the **Classes** node, and then select **New Class**. A class group displays under the **Classes** node.

3.  Right-click the new class, and then click **New Method**. A new method node displays under the **Classes** node.

4.  Right-click the new method and then click **Edit**. Enter the following main method code to activate the workflow from the workflow type name. This example applies to workflow submissions for the Finance and Operations client. For an example that also works with Enterprise Portal, see [Adding enterprise portal support for workflow submission](https://docs.microsoft.com/en-us/dynamicsax-2012/developer/adding-enterprise-portal-support-for-workflow-submission).
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
        
                        // Updates the workflow button to diplay Actions instead of Submit.
                        args.caller().updateWorkflowControls();
                }
        
                catch(exception::Error)
                {
                    // ToDo Insert your error code here.
                }
            }
        }
    ```
5.  Close the **Editor** window and click **Yes** to save changes.
    

    > [!NOTE]
    > <P>When you save this code, you will get the <STRONG>Empty compound statement</STRONG> warning message in the <STRONG>Compiler Output</STRONG> window unless you add valid code in the catch(exception::Error) block.</P>



## See also

[Activating a workflow](https://docs.microsoft.com/en-us/dynamicsax-2012/developer/activating-a-workflow)

[Create a new workflow type](workflow-type-create-new.md)

[Workflow::activateFromWorkflowType method](https://docs.microsoft.com/en-us/previous-versions/dynamics/ax-2012/application-classes/gg812416(v=ax.60))

[Workflow::activateFromWorkflowSequenceNumber method](https://docs.microsoft.com/en-us/previous-versions/dynamics/ax-2012/application-classes/gg812415(v=ax.60))

[Workflow::activateFromWorkflowConfigurationId method](https://docs.microsoft.com/en-us/previous-versions/dynamics/ax-2012/application-classes/gg812414(v=ax.60))
