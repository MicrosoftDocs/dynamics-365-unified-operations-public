---
title: 'How to: Create a SubmitToWorkflow Class'
TOCTitle: 'How to: Create a SubmitToWorkflow Class'
ms:assetid: 134385b2-6cdc-46f7-b641-c66668b7ad5a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Cc583139(v=AX.60)
ms:contentKeyID: 35240587
ms.date: 05/18/2015
mtps_version: v=AX.60
---

# How to: Create a SubmitToWorkflow Class 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

In Microsoft Dynamics AX, a workflow is started when the user clicks the **Submit** button on the workflow toolbar. The **Submit** button is bound to an action menu item that calls the main method on a class that you create to activate a workflow. This topic describes how to create a SubmitToWorkflow class using the workflow type name to activate the workflow.

The same procedure can be used to activate a workflow by using the workflow configuration ID or the workflow sequence number. For more information, see [Activating a Workflow](activating-a-workflow.md).


> [!NOTE]
> <P>If you used the Workflow Wizard to create the workflow type, a workflow submit manager class will have already been created by the wizard. You will need to add code to this class.</P>



### To create a SubmitToWorkflow class

1.  In the Application Object Tree (AOT), expand the **Classes** node.

2.  Right-click the **Classes** node, and then select **New Class**. A class group displays under the **Classes** node.

3.  Right-click the new class, and then click **New Method**. A new method node displays under the **Classes** node.

4.  Right-click the new method and then click **Edit**. Enter the following main method code to activate the workflow from the workflow type name. This example applies to workflow submissions for the Microsoft Dynamics AX client. For an example that also works with Enterprise Portal, see [Adding Enterprise Portal Support for Workflow Submission](adding-enterprise-portal-support-for-workflow-submission.md).
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

[Activating a Workflow](activating-a-workflow.md)

[How to: Create a New Workflow Type](how-to-create-a-new-workflow-type.md)

[Workflow::activateFromWorkflowType Method](https://msdn.microsoft.com/en-us/library/gg812416\(v=ax.60\))

[Workflow::activateFromWorkflowSequenceNumber Method](https://msdn.microsoft.com/en-us/library/gg812415\(v=ax.60\))

[Workflow::activateFromWorkflowConfigurationId Method](https://msdn.microsoft.com/en-us/library/gg812414\(v=ax.60\))
