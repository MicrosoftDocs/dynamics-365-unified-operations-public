# Synchronize with VSTS, collect requirements, and review processes

The implementation stage of a project starts by synchronizing a BPM library with your Visual Studio Team Services (VSTS) project. The enables you to review processes and associate requirements with business processes. It also enables you to track the progress of your implementation project in VSTS and associate work items like bugs, tasks, backlog items, tests, and documents with requirements and business processes.

Currently, VSTS does not support custom work types or synchronization of business processes with custom work types.

To learn more about VSTS, visit [www.visualstudio.com/team-services](http://www.visualstudio.com/team-services).

## LCS project settings: Set up Visual Studio Team Services

If you have already setup Visual Studio Team Services from LCS, you can skip this section.

### Create a personal access token

To connect to a VSTS project, LCS is authenticated by using a personal access token. Use the following steps to create a personal access token in VSTS.

1. Sign in to (https://www.visualstudio.com/) and locate your VSTS project.
2. In the top right corner, hover over your name, and in the menu that appears, select **Security**.
3. Click **Add** to create a new personal access token.
4. Give the token a name, and then enter the amount of time that you want the token to last for.
5. Click **Create Token**.
6. Copy the token to your clipboard. You will not be able to find the token details after this step is completed, so be sure that you have copied the token before navigating away from this page.

### Configure your LCS project to connect to VSTS

1. In your LCS project, go to the **Project settings** tile.
2. Select **Visual Studio Team Services** , and then click **Setup Visual Studio Team Services**. This configuration is needed by many LCS tools, if you have already configured LCS to connect to your VSTS project, you can skip this section or click **Change** to change the existing setup.
![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/master/NEWBPM_BlogPost22-1024x378.png "image")

3. Enter the root URL for your VSTS account and the access token that you created earlier, and then click **Continue**.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/master/NEWBPM_BlogPost23-1024x484.png "image")

1. Select your Visual Studio Team Services project.
2. Select the work item type mappings. These are the mappings between an LCS/BPM item and the associated VSTS work item types.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/master/NEWBPM_BlogPost24.png "image")

3. Click **Continue,** review your changes, and then click **Save**.

## BPM VSTS Synchronization

After you have set up the connection between the LCS project and a VSTS project you will be able to synchronize a library with a VSTS project. When you synchronize a BPM library with a VSTS project, a VSTS work item is created for each business process line in the BPM library. In addition, the hierarchy of business processes in BPM is reflected in the hierarchy of work items in VSTS. The type of work items created in VSTS depends on your LCS project settings.

This is a one-way sync, changes in LCS are reflected in VSTS but not the other way around.

The following is synchronized:

- Business process name
- Business process description
- Keywords (as tags)
- Countries/regions (as tags)
- Industry (as tags)

## Synchronize a BPM library with a VSTS project

Go to the **Business process libraries** page, select the ellipsis (…) of the library that you want to synchronize, and select **VSTS sync**.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/master/NEWBPM_BlogPost25.png "image")

You can also start VSTS sync from the toolbar of a BPM library.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/master/NEWBPM_BlogPost26.png "image")

## Turn Off BPM VSTS Synchronization

If you want to turn off sync, go back to the same menu.

## Review processes and add requirements

During the requirements gathering phase of a project, use the BPM library to review business processes and tasks, and to identify requirements. In BPM, you can mark business processes as **Reviewed** to track the review process.

To mark a process or sub process, as reviewed, select the process in BPM, and then select **Mark as reviewed** in the **Overview** pane.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/master/NEWBPM_BlogPost27.png "image")

When a business process is marked as reviewed, the **Reviewed** column is updated.

The **Reviewed** column shows the following:

- A fraction indicating the number of direct child processes that have been reviewed.
- An icon indicating whether this process and all its children are fully reviewed (green check mark), partially reviewed (yellow circle), or not reviewed (red dash).

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/master/NEWBPM_BlogPost28.png "image")

If the BPM library is synchronized with a VSTS project, when you mark a process as reviewed its state changes to **Active** in VSTS.

While reviewing a business process that is connected to VSTS, you can add a requirement directly to your VSTs project.

1. Select the desired business process.
2. Select the **Requirements** tab.
3. Select **Add requirement**.
4. Enter a name, description, and type, and then click **Create**.

![image](https://github.com/ntecklu/Dynamics-365-Operations/blob/master/NEWBPM_BlogPost29-179x300.png "image")

This will create a requirement work item in VSTS associated with the current business process.

On the **Requirements** tab, you can also navigate to the VSTS work items associated with the current business process by selecting the appropriate links.
