# Using Activity Diagrams with BPM
You can associate an activity diagram with a business process. Activity diagrams are used to describe how a business process or task is completed in a proposed software solution.
There are 3 types of activity diagrams:
- **Task recordings** - Business processes associated with Dynamics 365 for Operations Task recordings include automatically generated activity diagrams and process steps.
- **Microsoft Visio** - You can associate a business process with a Visio diagram by manually uploading a Visio file.
- **User-defined** - You can manually create (or edit) a BPM activity diagram.
In addition to activity diagrams, you can describe a business process using detailed process steps.
## Browse activity diagrams
The **Diagrams** column in your BPM library indicates when a particular business process is associated with an activity diagram. The number indicates the number of child processes that include diagrams and the icon next to the number indicates whether the current node/process is associated with a diagram. These indicators do not apply to Visio diagrams.
![image 1](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost10.png "image 1")
To view or edit an activity diagram, navigate to the business process, and then in the **Overview** pane, select **Diagrams**. This will open the **Flowchart** page.

![image 2](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost15.png "image2")
## Activity diagrams created from Task recordings
You can create a Task recording in your Dynamics 365 for Operations environment and save it directly to LCS. This will associate a Task recording with a business process in a BPM library. For more information, see [Connecting the help system](https://ax.help.dynamics.com/en/wiki/working-with-help/#connecting-the-help-system) and [Create documentation or training using task recordings](https://ax.help.dynamics.com/en/wiki/task-recorder/).
The task recorder tool in Dynamics 365 for Operations allows you to create a distributable recording file (_.axtr_). You can associate a business process in BPM with a Task recording by manually uploading a recording (_.axtr_) file. In BPM, select the desired business process then select **Upload**.
![image 3](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost16.png "image 3")

BPM automatically generates an activity diagram and detailed process steps for all recordings created in Dynamics 365 for operations.

![image 4](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost17-1024x483.png "image 4")
## Edit activity diagrams
To edit an activity diagram, right-click on a blank area of the flowchart and in the bottom toolbar, select **Edit**. For more information about BPM flowcharts, see [Flowcharts in Business process modeler](https://ax.help.dynamics.com/en/wiki/flowcharts-in-business-process-modeler/).
## Microsoft Visio files
You can associate a business process with a Visio diagram. Typically, this is used for high-level processes that cannot be represented with a Task recording. BPM supports .vsd and .vsdx files, .vsdm files (macros) are not supported. When .vsd files have macros, BPM disables the execution of the macro.
1. To view or upload a Visio file, navigate to the business process, and then select **Diagrams** in the **Overview** pane. This will open the flowchart page.

![image 5](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost18.png "image 5")

2. Select the **Visio** tab. For more information, see [Unconnected flowcharts](https://ax.help.dynamics.com/en/wiki/flowcharts-in-business-process-modeler/#unconnected-flowcharts).
## Edit process steps
1. To edit process steps, right-click on a blank area of the flowchart, and select **Edit** in the bottom toolbar.
2. In the **Process steps** text box, enter the process steps, one step per line.
3. To indent steps, which is the same as defining sub steps), use the **=** (equal sign). You can have more than one **=** sign to indicate a deeper level of indentation.
For example, to render the following process steps:
![image 6](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost19.png  "image 6")
4. Right-click the flowchart, and then select **Edit**.
5. In the **Process steps** text box, enter the information shown in the following graphic.

![image 7](https://github.com/ntecklu/Dynamics-365-Operations/blob/nahva-bpm-overview/dev-itpro/lifecycle-services/media/NEWBPM_BlogPost20.png "image 7")

Note: The **=** sign indicates the hierarchy level of a sub step.
