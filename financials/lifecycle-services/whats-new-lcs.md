---
# required metadata

title: What's new in Lifecycle Services
description: 
author: kfend
manager: AnnBe
ms.date: 2015-12-02 16 - 48 - 17
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 13321
ms.assetid: 3ab3bb5c-302b-4990-a9ca-24e19998c797
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# What's new in Lifecycle Services



Microsoft Dynamics Lifecycle Services provides a cloud-based collaborative workspace that customers and their partners can use to manage Microsoft Dynamics AX projects from pre-sales to implementation and operations. Based on the phase of your project and the industry that you are working in, the site provides checklists and tools that help you manage the project. The site also provides a dashboard, so that you have a single location from which you can obtain up-to-date project information. Go to the Lifecycle Services [site](https://lcs.dynamics.com/en/). Read the documentation: [Lifecycle Services for Microsoft Dynamics User Guide (LCS)](lcs-user-guide.md) For more detailed information about Lifecycle Services releases, see the release posts on Lifecycle Services [blog](http://blogs.msdn.com/b/lcs/).

## September 2016
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the September release of Lifecycle Services. **NEW FEATURES** **Combined packages flow through LCS** In the September LCS release, you can now combine a maximum of 3 deployable packages into a single package that can then be deployed on the environment of your choice. This change significantly reduce the downtime resulting from the application of these packages. The following steps provide information about how to deploy the packages.

1.  Select the packages to include in the combined package, and the click **Merge**.
    -   Note: There are restrictions on the packages that can be included as part of a combined package.
        -   Only one package of each type can be selected. For example, you can only select one binary package, 1 application package, and 1 Retail package.
        -   Any packages selected for the combined package must be valid.
        -   A combined package cannot contain a combined package.

2.  In the slider that opens, enter a name and description for the new package, and then click **Confirm**. Before you can use your combined package, LCS must complete the process of merging the packages you selected into a new package. After the combined package is ready, the **Additional details** pane will show information about the package.Specifically, you can view information about:
    -   The packages used to create the combined package
    -   The service models and modules included in the combined package
    -   The validation status

    When the combined package is ready, it can be applied to an environment.
3.  On the **Environment details** page, click **Maintain** &gt; **Apply updates**.
4.  When the **Select the change type** slider opens, click **Merged package**. The **Select the Merged package to apply** slider will open. This slider shows all of the combined packages in the project that are ready to be used.
5.  Select the package that you want applied to the environment, and then click **Apply**. **Note:** Even when the child packages for a combined package have been applied on an environment, the combined package will still need to be applied on a sandbox environment. This is so that the combined package can be marked as a Release candidate and the request to apply the package on the Production environment can be made.

**Process Data Packages** When you are consuming process data packages, for example applying data packages associated with business processes, (i.e. applying data packages associated with business processes) to a Dynamics AX environment, you can select multiple packages and apply them concurrently to the destination environment. **Cloud-powered support is now Support** The **Cloud-powered support** tile has been renamed **Support**. This change has been applied to all instances of **Cloud-powered support** in LCS. This change is applicable to LCS projects for all supported Dynamics AX product versions. **Subfolders support for SharePoint Online library organization** In the September LCS release, you can now browse, upload, and download documents from subfolders in a SharePoint document library.

1.  To browse folders, from the **SharePoint Online Library** page, click on the folder name. The subfolders and documents within that folder will be shown.
2.  To download a document, click on the document name.
3.  To upload a document to a subfolder, navigate to the subfolder by clicking the name of the parent folder. [![LCSSept01](./media/lcssept01-300x172.jpg)](./media/lcssept01.jpg)
4.  Click **Upload** to add a document to the folder. [![LCSSept02](./media/lcssept02.jpg)](./media/lcssept02.jpg)

You can also select subfolders while attaching documents to a methodology or task.

1.  From the project dashboard, click **Attach document**. [![LCSSept03](./media/lcssept03-300x201.jpg)](./media/lcssept03.jpg)
2.  Browse to or select folders from the list on the slider, and then click Next to upload a document to the selected folder. [![LCSSept04](./media/lcssept04.jpg)](./media/lcssept04.jpg) The document will be uploaded to the folder that you selected and attached to the methodology task item on the dashboard.

## August 2016
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the August release of Lifecycle Services. **NEW FEATURES** **Database refresh request** Starting today, when you are working in an implementation project, you can request that sandbox environments to be refreshed with DB backups directly from LCS.

1.  To submit the request, under the **Environments** heading, click **Site reliability work items**. [![LCSWhat'sNew Aug\_01](./media/lcswhatsnew-aug_01.jpg)](./media/lcswhatsnew-aug_01.jpg)
2.  Click **+ Add**. [![LCSWhat'sNew Aug\_02](./media/lcswhatsnew-aug_02.jpg)](./media/lcswhatsnew-aug_02.jpg)
3.  Click **Database refresh request**.
4.  Select the source environment, target environment, data, and time, and then click **Submit**. [![LCSWhat'sNew Aug\_03](./media/lcswhatsnew-aug_03.jpg)](./media/lcswhatsnew-aug_03.jpg) You can find the most recent status under **Service request status**. [![LCSWhat'sNew Aug\_04](./media/lcswhatsnew-aug_04.jpg)](./media/lcswhatsnew-aug_04.jpg)
5.  To communicate with the service engineering team, click the work item, add a comment, and then click **Submit**. [![LCSWhat'sNew Aug\_05](./media/lcswhatsnew-aug_05.jpg)](./media/lcswhatsnew-aug_05.jpg)

**Methodology and SharePoint integration** In Microsoft Dynamics AX LCS projects, you can now attach documents to a methodology task. To upload a document, after you complete the SharePoint setup, select the task to which you want to upload the document and then click **Attach document**. Browse to the document and then upload it. [![LCSWhat'sNew Aug\_06](./media/lcswhatsnew-aug_06.jpg)](./media/lcswhatsnew-aug_06.jpg) Project team members can click **Download** to download the document. If the document is no longer relevant to the step, click **Detach** to remove the link between the document and the step. [![LCSWhat'sNew Aug\_07](./media/lcswhatsnew-aug_07.jpg)](./media/lcswhatsnew-aug_07.jpg) **Issue search** With the August release of LCS, the following updates to Issue search have been added:

-   View additional status details for active bugs: See when a bug is **Active**, **Investigating a fix**, or in a **Quality Assurance** step.
-   Subscribe to email notifications: Receive a notification when an issue is resolved . Enter a comma separated list of emails in the box and click **Add** to be notified when the bug is resolved. [![LCSWhat'sNew Aug\_08](./media/lcswhatsnew-aug_08-300x155.jpg)](./media/lcswhatsnew-aug_08.jpg) Additionally, improvements to the View changes page allows for viewable changes of Microsoft Dynamics AX fixes. Specifically, now that the changes enabled, you will see detailed information about the line number that the change was made at. If you click the method name \#linenumber, you will drill directly to that change in the method or object. [![LCSWhat'sNew Aug\_09](./media/lcswhatsnew-aug_09-300x49.jpg)](./media/lcswhatsnew-aug_09.jpg)

 

## July 2016
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the July release of Lifecycle Services. **NEW FEATURES** **SharePoint integration improvements in LCS (Preview)** With the July release, we have made significant improvements to simplify the LCS SharePoint integration for AX7 projects. The new framework uses user OAuth for performing operations in SharePoint. **Set up SharePoint in an LCS project**

1.  To set up a SharePoint site in an LCS project, go to your LCS AX7 Project, scroll to the right, and click the **Project Settings** tile.
2.  On the **Project settings** page, click the **SharePoint Online** tab.
3.  Enter your SharePoint site URL and then click **Next**. Make sure the account you are using has access to the SharePoint that you are trying to setup.[![LCSWhat'sNew July\_01](./media/lcswhatsnew-july_01.jpg)](./media/lcswhatsnew-july_01.jpg)
4.  Select the folder you want to use for the project. If you don’t have a folder, go to SharePoint and create a new folder. Then select that project from the project selection drop-down and click **Save**. [![LCSWhat'sNew July\_02](./media/lcswhatsnew-july_02.jpg)](./media/lcswhatsnew-july_02.jpg) After the setup is successfully complete, you will see a screen similar to the following: [![LCSWhat'sNew July\_03](./media/lcswhatsnew-july_03.jpg)](./media/lcswhatsnew-july_03.jpg)
5.  When you go to the SharePoint Online library in the project, you can see the list of documents in the folder. [![LCSWhat'sNew July\_04](./media/lcswhatsnew-july_04.jpg)](./media/lcswhatsnew-july_04.jpg)
6.  Add additional project documents by clicking +. [![LCSWhat'sNew July\_05](./media/lcswhatsnew-july_05.jpg)](./media/lcswhatsnew-july_05.jpg) LCS project team members who have access to SharePoint folder can directly download files from LCS and update new project documents. In SharePoint, you can see the document in the SharePoint folder. [![LCSWhat'sNew July\_06](./media/lcswhatsnew-july_06.jpg)](./media/lcswhatsnew-july_06.jpg)

**LCS solution improvements** If you are an ISV who is working on an AX solution, you can now add the Power BI report model to the solution from solution management. [![LCSWhat'sNew July\_07](./media/lcswhatsnew-july_07.jpg)](./media/lcswhatsnew-july_07.jpg) Customers looking for ISV solutions on Dynamics AX, can now find them at [Microsoft AppSource](https://appsource.microsoft.com/en-us/). Learn more about AppSource [here](https://www.youtube.com/watch?v=2wVJWfVVwlI). [![LCSWhat'sNew July\_08](./media/lcswhatsnew-july_08.jpg)](./media/lcswhatsnew-july_08.jpg) If you are interested in publishing your Dynamics AX solution to Microsoft AppSource, find more information about the listing process [here](https://appsource.microsoft.com/en-us/partners).

## June 2016
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the June release of Lifecycle Services. **NEW FEATURES** **LCS language selection** LCS now includes a translated version of the May APQC BPM library and the Getting Started library. To use LCS with a translated UI, click your account name in the upper right corner, click **Preferences**, and choose your language. [![LCS What's new 01](./media/lcs-whats-new-01.png)](./media/lcs-whats-new-01.png) **Ability to deploy Dev and Build/test environments** Starting today in the implementation project for AX 7, you can chose to deploy a Development environment or a Build and test environment. [![1](https://msdnshared.blob.core.windows.net/media/2016/07/11.png)](https://msdnshared.blob.core.windows.net/media/2016/07/11.png) **Methodology improvements** In the Implementation project, you can now **append your existing methodology** with the methodology that is shipped by Microsoft.

1.  To append a methodology click on **…** in your Implementation project methodology section and then select **Append methodology**.

![2](https://msdnshared.blob.core.windows.net/media/2016/07/21.png)

1.  Select the methodology from the list of available methodologies, and then click **Confirm**.

Before: ![3](https://msdnshared.blob.core.windows.net/media/2016/07/3.png)   After: ![4](https://msdnshared.blob.core.windows.net/media/2016/07/4.png) Now, you can customize the locked methodology by **adding phase and tasks** to the implementation methodology that is shipped by Microsoft for the new Dynamics AX. ![5](https://msdnshared.blob.core.windows.net/media/2016/07/5.png) **Subscription estimator improvements** Starting today, you must complete the Microsoft Excel **Usage profile** and upload the profile to LCS to complete the subscription estimate for your implementation project. You can download the **Sample usage profile** from the **Subscription estimator** page. Click **New estimate** to upload the completed **Usage profile**.   [![6](https://msdnshared.blob.core.windows.net/media/2016/07/6.png)](https://msdnshared.blob.core.windows.net/media/2016/07/6.png) [![7](https://msdnshared.blob.core.windows.net/media/2016/07/7.png)](https://msdnshared.blob.core.windows.net/media/2016/07/7.png)   You can download a completed usage profile from LCS at any time, make changes, and then upload the updated usage profile by clicking **Edit**. ![8](https://msdnshared.blob.core.windows.net/media/2016/07/8.png)   **Note:** We have added additional questions and improved the validation experience in the **Usage profile**, to help us better estimate your needs. **Monitoring and Diagnostic feature updates** Starting in June 2016, Monitoring and Diagnostics features in LCS will be publically available to all environments that are deployed through LCS. **Note:** Only Production environments that are deployed through LCS in **Microsoft Managed Subscription** will be actively monitored by the Microsoft Service Engineering team. All other environments do not have the monitoring features turned on. In addition to the user activity troubleshooting feature (**Activity Tab** on the **Environment monitoring** page), we have added additional features specifically for SQL Troubleshooting, which can be accessed by clicking the **Environment Monitoring** link in the **Monitoring** section on the **Environment Details** page. ![9](https://msdnshared.blob.core.windows.net/media/2016/07/9-1024x182.png)

-   **SQL Insights –** This feature gives customers/partners the opportunity to troubleshoot SQL issues by looking at an aggregated view of the most expensive queries that were executed on the environment based on duration, logical IO, CPU, execution count and contention. This feature also provides an advanced troubleshooting experience by showing a trend of the selected query. Detailed metrics for the selected query are shown, along with the query statement and an option to download the query execution plan for diagnostics.

  [![10](https://msdnshared.blob.core.windows.net/media/2016/07/10-1024x343.png)](https://msdnshared.blob.core.windows.net/media/2016/07/10.png) [![11](https://msdnshared.blob.core.windows.net/media/2016/07/111-1024x287.png)](https://msdnshared.blob.core.windows.net/media/2016/07/111.png) [![12](https://msdnshared.blob.core.windows.net/media/2016/07/12-1024x289.png)](https://msdnshared.blob.core.windows.net/media/2016/07/12.png)

-   **Just in time SQL Troubleshooting –** This feature gives the customers/partners the opportunity to troubleshoot SQL issues in real time by locating the queries that are blocked and the queries are blocking. This feature also provides a view of aggregated lock information for the tables that currently hold locks on them.

You can ciew this by clicking on the **SQL Now** tab on the **Environment monitoring page**. ![13](https://msdnshared.blob.core.windows.net/media/2016/07/13-1024x471.png)   **BPM and Task guides** The list of task guides that were made available with the February 2016 release of Dynamics AX has been published, and can be found here, [New task guides available (February 2016)](new-task-guides-available-february-2016.md). **BPM Integration with VSTS (Public preview)**

1.  On the LCS portal, select the **Preview feature management** tile and turn on the feature named **VSO WorkItem Mapping**. This will enable you to preview the new BPM functionality.
2.  After you have configured Visual Studio Team Services (VSTS) from the LCS project settings, go to your BPM library and on the left-pane, under **Implementation views**, click **Review processes**.
3.  Click **Sync with VSTS**.

This will synchronize the BPM library hierarchy into your VSTS project, as a hierarchy of work items (Epics, Features, …etc.). This is a one-way sync from LCS to VSTS that will keep your VSTS work items updated with any changes that are made in the LCS BPM library. ![14](https://msdnshared.blob.core.windows.net/media/2016/07/14.png) The VSTS work item types associated with LCS items can be configured from the **VSTS** tab in your LCS project’s **Project settings**. Work item type mapping (VSTS work item type) must be configured before a connection to a VSTS project is established. ![15](https://msdnshared.blob.core.windows.net/media/2016/07/15-1024x487.png)   **Add requirements to a business process** As part of the fit/gap analysis stage of your project, in the **Review processes** view, you can select a business process line and add a requirement that is associated with the selected business process. This requirement will be stored as a requirement work item in VSTS. The **Process details** page will list all requirements in VSTS that are associated with the current business process line. It also allows you to add a new requirement. [![16](https://msdnshared.blob.core.windows.net/media/2016/07/16.png)](https://msdnshared.blob.core.windows.net/media/2016/07/16.png)   When you add a requirement,  enter a title and adescription, and assess whether it is a fit or a gap. ![17](https://msdnshared.blob.core.windows.net/media/2016/07/17.png) **Configuration and data manager: Apply more than one data package at a time** **Configuration and data manager** is a tool that enables you to apply data packages to Dynamics AX cloud environment by using the AX data management framework. With this release, you can select more than one data package and apply them at once to a specific AX instance. When you select more than one package and click **Apply**, you can choose whether you want to apply the packages sequentially or concurrently. [![18](https://msdnshared.blob.core.windows.net/media/2016/07/18.png)](https://msdnshared.blob.core.windows.net/media/2016/07/18.png)   You should apply sequentially if the selected data packages depend on each other. If you select **Apply sequentially**, you will first be prompted to select the order in which the packages are applied. Use the sequence number drop down menus to define the order. ![19](https://msdnshared.blob.core.windows.net/media/2016/07/19.png) You can also enter a tag. A tag can be used as a keyword that will appear on the history page to indicate that these packages have been applied as part of the same job.

## May 2016
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the May release of Lifecycle Services. **NEW FEATURES** **Microsoft Dynamics AX May 2016 Update is now available** Starting today, you can deploy the Microsoft Dynamics AX May 2016 Update from LCS When you select a topology for deployment in the partner project workspace or in Cloud hosted environment in customer implementation project, you can select either RTW or the May Update (Update 1). For more information about what’s new in the May Update, see the [What’s new or changed](whats-new-changed.md) wiki topic. ![1](https://msdnshared.blob.core.windows.net/media/2016/05/165-e1464377383160.png) When you click **Configure** in the **customer implementation project**,  you will be provided with an option to choose from RTW or the May Update (Update 1). ![2](https://msdnshared.blob.core.windows.net/media/2016/05/259.png) If you want to deploy the Dynamics AX May Update, select **Dynamics AX – Develop (Update 1)**.   ![3](https://msdnshared.blob.core.windows.net/media/2016/05/339.png) This will load the May Update-specific deployment configuration screen for you.   ![4](https://msdnshared.blob.core.windows.net/media/2016/05/432-1024x742.png)   If you want to change back to RTW, click **Supported version** &gt; **Change selected topology**.   ![5](https://msdnshared.blob.core.windows.net/media/2016/05/527-1024x748.png)   **Asset library improvements** The Binary hotfix in the Asset library has a new home.

1.  To locate the Binary hotfix, in the **Asset type** pane, click **Software deployable package**.
2.  In the pane that opens, in the **Package type** field, select **Binary hotfix**.

![6](https://msdnshared.blob.core.windows.net/media/2016/05/628-1024x492.png)   You can now make a **copy** of an asset directly from asset library. You no longer need to download and then  re-upload the file to LCS to make a copy.  To make a copy, select the file and then click **Copy**. ![7](https://msdnshared.blob.core.windows.net/media/2016/05/723-1024x474.png) A new **Usage profile** Excel worksheet is included in the **Subscription estimator** for the new Dynamics AX. The new worksheet includes an updated questionnaire and improved validations. When you deploy a new environment in the implementation project for the new AX,  you can specify users who need to be emailed about environment specific **notifications**, including planed downtimes. ![8](https://msdnshared.blob.core.windows.net/media/2016/05/817-1024x696.png)

## April 2016
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the April release of Lifecycle Services. **NEW FEATURES** **Asset library** You can now ship a new version of any file in the asset library and provide release  notes when you publish an asset. This is useful when you have assets that are published with your organization users. Organization users can now get additional versions of the same file and check what has changed with each version from the release notes, before they download a specific version.

1.  Select the published file for which are publishing a newer version and then click **Upload**, as shown below.

![1](https://msdnshared.blob.core.windows.net/media/2016/05/12.png) 2. Click **Browse** to navigate to the location where you have stored the new version of the file, and then click **Upload**.   [![2](https://msdnshared.blob.core.windows.net/media/2016/05/22.png)](https://msdnshared.blob.core.windows.net/media/2016/05/22.png)   3. Click **Yes** to add release notes. [![3](https://msdnshared.blob.core.windows.net/media/2016/05/32-1024x458.png)](https://msdnshared.blob.core.windows.net/media/2016/05/32.png)   4. Click **Browse** to navigate to your release notes file, and then click **Upload**. [![4](https://msdnshared.blob.core.windows.net/media/2016/05/42.png)](https://msdnshared.blob.core.windows.net/media/2016/05/42.png)   Note that the **Version** column shows the latest version number of the asset that is in the asset library. [![5](https://msdnshared.blob.core.windows.net/media/2016/05/52-1024x560.png)](https://msdnshared.blob.core.windows.net/media/2016/05/52.png)   Users can download a specific version by clicking on that version and download the related release notes. [![6](https://msdnshared.blob.core.windows.net/media/2016/05/62-1024x580.png)](https://msdnshared.blob.core.windows.net/media/2016/05/62.png)   [![7](https://msdnshared.blob.core.windows.net/media/2016/05/72.png)](https://msdnshared.blob.core.windows.net/media/2016/05/72.png) This is also useful when you have shared or imported these assets into a customer’s project. When you ship incremental versions, the customer will be able to download the files and release notes from their project. **LCS Solution improvements** When you create a process data package, you can use the **Select all** button to add all assets in your asset library to the process data package. [![8](https://msdnshared.blob.core.windows.net/media/2016/05/8.jpg)](https://msdnshared.blob.core.windows.net/media/2016/05/8.jpg)   **Solution edit** You can edit your solution and provide the updated version of your solution  to your customers. This task must be completed by a solution approver.

1.  On the Published solutions  page, click **Edit**.

[![9](https://msdnshared.blob.core.windows.net/media/2016/05/92.png)](https://msdnshared.blob.core.windows.net/media/2016/05/92.png)   Editing the solution is similar to how you created a solution in a project. 2. Select a project from the list of available projects. We recommend that when you edit a project solution, that you create a new solution creation project. Note that a solution can be opened for edit only once until it is published. If you would to like to collaborate on the editing process, the editing user needs to invite you to the Project. [![10](https://msdnshared.blob.core.windows.net/media/2016/05/10.png)](https://msdnshared.blob.core.windows.net/media/2016/05/10.png)   [![11](https://msdnshared.blob.core.windows.net/media/2016/05/112.png)](https://msdnshared.blob.core.windows.net/media/2016/05/112.png) When you click **Edit**, the solution will open in edit mode in the project that you selected. ![12](https://msdnshared.blob.core.windows.net/media/2016/05/121-1024x508.png)   Similar to how you created the solution, you can add and delete assets from the solution and you can also add release notes. After you have made the required changes, you can publish the solution. [![13](https://msdnshared.blob.core.windows.net/media/2016/05/13.png)](https://msdnshared.blob.core.windows.net/media/2016/05/13.png)     After you publish a new version of solution, all of your customers can access the newest version and the associated release notes from the asset library. [![14](https://msdnshared.blob.core.windows.net/media/2016/05/14.png)](https://msdnshared.blob.core.windows.net/media/2016/05/14.png)   A customer project will have a specific version as you can see below. Now the customer can review your release notes and, if they want, they can get the latest version of the solution. [![15](https://msdnshared.blob.core.windows.net/media/2016/05/15.png)](https://msdnshared.blob.core.windows.net/media/2016/05/15.png)   [![16](https://msdnshared.blob.core.windows.net/media/2016/05/16.png)](https://msdnshared.blob.core.windows.net/media/2016/05/16.png)   Now, the version in the project is the latest version of the solution. All of the most recent versions of the solution assets will be imported into the project. [![17](https://msdnshared.blob.core.windows.net/media/2016/05/17.png)](https://msdnshared.blob.core.windows.net/media/2016/05/17.png)   **Business Process Modeler (BPM)** **Create and build a new BPM library from scratch** With this release, you will be able to create and build new BPM libraries from scratch, without the need to import existing APQC libraries. These new libraries will not have the APQC logo.

1.  Go to the **Business process libraries** main page.

[![18](https://msdnshared.blob.core.windows.net/media/2016/05/18.png)](https://msdnshared.blob.core.windows.net/media/2016/05/18.png) 2. Right-click on any library tile. 3. Select **Create** in the toolbar at the bottom of the page. [![19](https://msdnshared.blob.core.windows.net/media/2016/05/19.png)](https://msdnshared.blob.core.windows.net/media/2016/05/19.png)   After you enter a new library name, the new library will appear under **My libraries**. 4. Open the new created library and on the left pane under **Core Views**, click **Author and edit**. [![20](https://msdnshared.blob.core.windows.net/media/2016/05/20.png)](https://msdnshared.blob.core.windows.net/media/2016/05/20.png)   From this page, you have access to the familiar BPM functionality:

-   Add a new business processes –  Drag and drop the **New Business Process** tile.
-   Import existing business process from other BPM libraries – Click **Import**, and then drag and drop a business process from a library into your new library.
-   Edit business process details.

Note that your new library will enable you to associate keywords, industries and countries/regions metadata with a business process. **Business process steps** In this release, we have improved the rendering and accuracy of process steps associated with task recordings that are stored in LCS. These updates include:

-   Correcting errors in the chronological order of steps.
-   Rendering of sub-steps in a hierarchical fashion.
-   Not showing hidden steps.

You can also now edit process steps and define sub-steps. For example, to render the following process steps: [![21](https://msdnshared.blob.core.windows.net/media/2016/05/211.png)](https://msdnshared.blob.core.windows.net/media/2016/05/211.png)

1.  Right click on the flowchart, and then select **Edit**.
2.  In the **Process steps** text box, enter the information shown in the following graphic.

**Note:** The “=” sign indicates the hierarchy level of a sub step. [![22](https://msdnshared.blob.core.windows.net/media/2016/05/221.png)](https://msdnshared.blob.core.windows.net/media/2016/05/221.png)   **Import BPM localizations** You can now import the localizations (translations) of a Dynamics AX 2012 BPM library. Previously, this functionality was only available for the newest version Dynamics AX. This is now available for Dynamics AX 2012 projects as well. **Methodology improvements** You can move a task from one phase to another in a methodology. You no longer need to recreate the task under another phase.

1.  On the **Project methodology** page, in the **Tasks** pane, select the task that you want to move and click the icon as shown below.

[![25](https://msdnshared.blob.core.windows.net/media/2016/05/25-1024x377.png)](https://msdnshared.blob.core.windows.net/media/2016/05/25.png)   2. In the **Move task** slide-out pane, select the phase to which you are moving the task and then click **Confirm**. [![24](https://msdnshared.blob.core.windows.net/media/2016/05/24.png)](https://msdnshared.blob.core.windows.net/media/2016/05/24.png) **Methodology operations in bulk** When you are editing a methodology, you can complete selected operations in bulk. [![25](https://msdnshared.blob.core.windows.net/media/2016/05/25-1024x377.png)](https://msdnshared.blob.core.windows.net/media/2016/05/25.png)       **Login information** You can now view the login that you used to gain access to LCS. This can be useful if you have multiple profiles in LCS, for example a Microsoft account or an O365 account. [![26](https://msdnshared.blob.core.windows.net/media/2016/05/261.png)](https://msdnshared.blob.core.windows.net/media/2016/05/261.png)   **New Dynamics AX presales project improvements** Additional services are now available in the presales project workspace. As a partner, you can use the pre-sales workspace for all prospective presales scenarios. Note that only partners can provision a new Dynamics AX cloud environment. [![27](https://msdnshared.blob.core.windows.net/media/2016/05/27-1024x514.png)](https://msdnshared.blob.core.windows.net/media/2016/05/27.png)   **Premier customers: Create an incident for a project** Premier customers can now create Dynamics AX support tickets from Lifecycle Services (LCS). This functionality is available in LCS as a preview for the Dynamics AX 2012 and the newest version of Dynamics AX. The entry point to file the support incident for AX 2012 varies slightly with new Dynamics AX. See the differences in step 1 below. **For AX 2012:**

1.  In LCS, click the **Cloud-powered support** tile, click on the **Premier** tab, and then click **New Premier incident**.

[![28](https://msdnshared.blob.core.windows.net/media/2016/05/28.jpg)](https://msdnshared.blob.core.windows.net/media/2016/05/28.jpg)   **For the new Dynamics AX:**

1.  In LCS, click the **Cloud-powered support** tile, click the **Submitted to Microsoft** tab, and then click **Submit an incident**.

[![29](https://msdnshared.blob.core.windows.net/media/2016/05/29.jpg)](https://msdnshared.blob.core.windows.net/media/2016/05/29.jpg) 2. Select the contract type, **Premier (Preview)** as shown in the screenshot below. [![30](https://msdnshared.blob.core.windows.net/media/2016/05/30.jpg)](https://msdnshared.blob.core.windows.net/media/2016/05/30.jpg)   For the remainder of the procedure, all steps are valid for both AX 2012 and the new version of Dynamics AX. 3. If you have never associated your Access ID with your LCS login credentials, you will be asked to provide the Access ID and password of your Premier support contract. Enter the Access ID and password, and then click **Add contract**. [![31](https://msdnshared.blob.core.windows.net/media/2016/05/31.jpg)](https://msdnshared.blob.core.windows.net/media/2016/05/31.jpg) You will be redirected to Issue Search to search for an existing solution. 4. If an existing solution is not found, click **Create incident**. [![32](https://msdnshared.blob.core.windows.net/media/2016/05/32.jpg)](https://msdnshared.blob.core.windows.net/media/2016/05/32.jpg) 5. Selects a premier support contract. If needed add another premier contract by clicking **Use another premier contract**. [![33](https://msdnshared.blob.core.windows.net/media/2016/05/33.jpg)](https://msdnshared.blob.core.windows.net/media/2016/05/33.jpg)   6. Select the severity level of the issue. [![34](https://msdnshared.blob.core.windows.net/media/2016/05/34.jpg)](https://msdnshared.blob.core.windows.net/media/2016/05/34.jpg) 7. Enter any additional details about the issue. [![35](https://msdnshared.blob.core.windows.net/media/2016/05/35.jpg)](https://msdnshared.blob.core.windows.net/media/2016/05/35.jpg) 8. Review the submission and then click **Submit**. [![36](https://msdnshared.blob.core.windows.net/media/2016/05/36.jpg)](https://msdnshared.blob.core.windows.net/media/2016/05/36.jpg)

## March 2016
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the March release of Lifecycle Services. **NEW FEATURES** **Asset library improvements** This is the first wave of updates where we will be enabling multi-select support for a set of operations in the Asset library. At this time, we support multi-select for most of the operations in asset library including Delete, Save to my library, and Mark as release candidate.   [![1](https://msdnshared.blob.core.windows.net/media/2016/04/114-1024x458.png)](https://msdnshared.blob.core.windows.net/media/2016/04/114.png) Starting with this update, you can provide descriptions for all the assets in the Asset library and the descriptions will be available to all users in LCS who are using the asset you upload.   **Performance improvements** With the March update, we have made significant performance improvements to the LCS.   **Business Process Modeler (BPM) Localization** **Export a BPM library for localization** Functionality now enables the localization (translation) of business process lines and task guide steps associated with business process lines.

1.  You can access this functionality by clicking on the **Localization** button in the **Author and Edit** view of you BPM library.

  ![2](https://msdnshared.blob.core.windows.net/media/2016/04/24.png) This will open the **Localization Center.** ![3](https://msdnshared.blob.core.windows.net/media/2016/04/33.png) From there you can export your BPM library. After the export process is complete, and the status shows as **Completed,** you can download and extract the .zip file containing the localizable resources. ![4](https://msdnshared.blob.core.windows.net/media/2016/04/43.png) The extracted .zip file contains one folder for every locale. If this is the first localization export of this library, you will start with one locale, en-us. ![5](https://msdnshared.blob.core.windows.net/media/2016/04/52.png)   The locale folder will have one folder for every business process (BP) line in your library which is represented by a numerical identifier. Within  the BP line folder you will find the localizable resource files line.xml and recording\_resources.xml.   ![6](https://msdnshared.blob.core.windows.net/media/2016/04/62.png)

-   Line.xml contains the BP line localizable strings.
-   Recording.xml contains the task recording text.
-   Recording\_resources.xml contains the localizable strings of a task recording associated with the current BP line.

  In order to navigate more easily to the desired folder in the BPM library, open the **hiearchymap.html** file in a web browser.   **Import BPM localizations** When you complete your localization activities:

1.  Update the localization.xml file with a new &lt;localization&gt; entry for every language you added.
2.  Zip the localization folder and import it back into LCS using the import button in the **Localization Center**.

If you have edited the title or description of your line after your last export, the import process will show a conflict in the import report and the conflicting lines will not be imported. You can override this behavior and force an import by modifying the &lt;ModifiedDate&gt; of the line in the \_manifest.xml file to a future date. **Work in progress ** After importing BPM localizations, a Dynamics AX client connected to your LCS project will be able to render task guides in the Dynamics AX user interface language. However, the LCS BPM portal does not have this functionality yet. Import functionality is still not available for AX2012 projects. **Solution creation** Solution creation partners can now create a process data package directly from the Asset library. To start solution creation, click **+**, enter the name and description, and then click confirm. ![7](https://msdnshared.blob.core.windows.net/media/2016/04/72.png) You can now consume a process data package directly from the Asset library. To start the consume process, click **Consume**. ![8](https://msdnshared.blob.core.windows.net/media/2016/04/81.png) **Methodology improvements** You can clone, or create copies of, an existing phase and the related tasks. ![9](https://msdnshared.blob.core.windows.net/media/2016/04/91.png) Select the phase that you want to clone and click **Clone selected phase**. ![10](https://msdnshared.blob.core.windows.net/media/2016/04/102.png) This will create a copy of the selected phase and it’s associated tasks. ![11](https://msdnshared.blob.core.windows.net/media/2016/04/115.png) **Content release** We have shipped 2 new **BPM libraries** for the new Dynamics AX.

-   (February 2016) Getting started
-   (Feb 2016) APQC Unified Library for Microsoft Dynamics AX

The **(February 2016) Getting started** library is for key Dynamics AX trial getting started scenarios and includes task guides that provide guidance with getting started. The **(February 2016) APQC Unified Library for Microsoft Dynamics AX** , is the new cross-industry library that includes over 500 business process task guides. **New GER files** Microsoft-owned configurations have been added under the **GER configuration** asset type in the Shared asset library. They replaced the GER configurations released in January for the Dynamics AX CTP8 release. GER provides one common way, through LCS Asset library, for Microsoft and partners to distribute electronic document configurations to other partners and customers. GER also makes it easier for partners and customers to customize, upgrade, and distribute electronic document formats for their specific business requirements. **New data packages** New industry-specific  data packages are also available in this release. To import these data packages to the project, in your LCS project go to **Asset library**, select **Process data package**, and then click **Import.** ![12](https://msdnshared.blob.core.windows.net/media/2016/04/122.png) Select the process data packages for your industry from the list and import them into the project. ![13](https://msdnshared.blob.core.windows.net/media/2016/04/131.png) During import, the status will be shown as **Publishing**. After import has completed successfully, the status will update to **Published**. After the data packages have published successfully, you will see all of the data packages under **Data package** in the Asset library.

## February 2016
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the February release of Lifecycle Services. **NEW FEATURES ** **Dynamics AX project workspace** With this release, customers signing up for the new Dynamics AX by using CSP or VL, will get the new implementation project workspace. This implementation project workspace is created when a customer signs up for Dynamics AX offer and provides the following:

-   Every customer gets One implementation project workspace which is automatically created during signup.
-   Based on the offer selected by the customer, features in this project workspace will be enabled.
-   Environments included in the offer will be deployed and managed by Microsoft.
-   The Action center will help guide you through the required actions that must be completed.
-   A new methodology experience includes locked tasks as you progress through the implementation.
-   A more complete trail specifying who completed each methodology phase and tasks.
-   Milestones that can be used to track critical project dates.

[![1](https://msdnshared.blob.core.windows.net/media/2016/02/114-1024x434.png)](https://msdnshared.blob.core.windows.net/media/2016/02/114.png)   **[![Capture1](https://msdnshared.blob.core.windows.net/media/2016/02/Capture11.jpg)](https://msdnshared.blob.core.windows.net/media/2016/02/Capture11.jpg)** **Partners creating projects** As a partner, you can now create 2 types of project:

1.  **Prospective presales:** Use this project workspace to work with new Dynamics AX prospects to help them understand the business processes available in Dynamics AX and evaluate their subscription needs.
2.  **Migrate, create solutions, and learn Dynamics AX**: You can use this option to create a Dynamics AX 2012 project workspace, a project for upgrading from Dynamics AX 2012 to the new AX, to learn the new Dynamics AX, or to create LCS solutions.

[![2](https://msdnshared.blob.core.windows.net/media/2016/02/213.png)](https://msdnshared.blob.core.windows.net/media/2016/02/213.png) **Subscription estimator** Use can use the subscription estimator to evaluate your subscription needs for the new Dynamics AX. To use the Subscription estimator,  download the Usage profile Excel workbook and complete the following sheets:

-   Deployment details
-   Instance Characteristics
-   Retail & Commerce

[![3](https://msdnshared.blob.core.windows.net/media/2016/02/311-1024x475.png)](https://msdnshared.blob.core.windows.net/media/2016/02/311.png) After you have completed the worksheets, enter the data from the summary sheet into the Subscription estimator as shown below by clicking on **+ New estimate**. [![4](https://msdnshared.blob.core.windows.net/media/2016/02/412-1024x492.png)](https://msdnshared.blob.core.windows.net/media/2016/02/412.png) You must also make one estimate the Active estimate. Please make sure the estimate you mark as **Active** is same as the offer you bought through the VL or CSP channel. **New Online service agreement** With this release of LCS, the LCS online service agreement has been updated. You can find the latest online service agreement [here](https://lcs.dynamics.com/Logon/Legal). You need to accept the new online service agreement to continue using LCS. **Issue search** Issue search will now show a download button for new Dynamics AX online issues.  The hotfix package is directly available for download from the **Issue search** page. You no longer need to navigate through the **Update** tile to obtain the hotfix package. **Business process modeler (BPM)** You can now rename a BPM library. To edit a library name or its description:

1.  Right-click the library and then click **Edit**.
2.  Enter the new library name and description and then click **OK**.

[![5](https://msdnshared.blob.core.windows.net/media/2016/02/58.png)](https://msdnshared.blob.core.windows.net/media/2016/02/58.png) **New business process library for new Dynamics AX** We have shipped 2 new BPM libraries for the new Dynamics AX.

1.  The **Getting started** library is for key Dynamics AX trial getting started scenarios.
2.  The New **APQC unified library** is the new cross industry library.

[![6](https://msdnshared.blob.core.windows.net/media/2016/02/68.png)](https://msdnshared.blob.core.windows.net/media/2016/02/68.png) **45+ solutions are now available for the new Dynamics AX** 45+ industry-specific Dynamics AX ISV solutions are available on Azure Marketplace and consumable through LCS. You can browse these solutions [here](https://azure.microsoft.com/en-us/marketplace/dynamics/). Dynamics AX customers and prospects can now discover these solutions in Azure marketplace and request the ISV’s for a trial of these solutions. [![7](https://msdnshared.blob.core.windows.net/media/2016/02/74.png)](https://msdnshared.blob.core.windows.net/media/2016/02/74.png) **New deployment experience:** Deployment services for Microsoft Dynamics AX are now available for both Partner functions and Customer Subscription offers. The new Dynamics AX SQL Azure deployments can now have encryption at rest, Premium storage support is enabled for all Dynamics AX demo VMs. [![Capture](https://msdnshared.blob.core.windows.net/media/2016/02/Capture1.jpg)](https://msdnshared.blob.core.windows.net/media/2016/02/Capture1.jpg)

## January 2016
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the January release of Lifecycle Services. **NEW FEATURES** **Cloud hosted environments** now supports the deployment of Dynamics AX 2012 CU10 for non-demo topologies. ![1](https://msdnshared.blob.core.windows.net/media/2016/01/123-1024x515.png) LCS is now available in 40 languages. Please refer to the December release notes under **Language preferences** on how to use this new functionality. [![2](https://msdnshared.blob.core.windows.net/media/2016/01/212.png)](https://msdnshared.blob.core.windows.net/media/2016/01/212.png)                           **Configuration manager and Data deployment templates for Dynamics AX 2012** A new Configuration section has been added to the **Environment** page. In your LCS project, when you open a Dynamics AX environment page, you can use the **Configuration** tab to deploy data templates on that environment. ![3](https://msdnshared.blob.core.windows.net/media/2016/01/310.png) Deployment templates are a collection of data processing groups. Data processing groups are defined on a Dynamics AX environment and can be pulled into LCS and then grouped into a deployment template. These deployment templates are stored in the asset library of your LCS project. From the **Configuration** tab on the environment’s page, you can: Deploy an existing template on the current environment. -or- Create a new deployment template by pulling processing groups from the current Dynamics AX environment, and store the template in the **Asset Library**. This new functionality is intended to replace the existing preview version of **Configuration manager** which will be removed. By using deployment templates instead of the configurations used by the **Configuration manager**:

1.  You can control the order in which data entities and data processing groups are applied.
2.  You can edit the content of data templates directly from LCS.

## **GER configuration** Microsoftowned configurations for CTP8 were added under the **GER configuration** asset type in the Shared asset library. GER provides one common way (through the LCS Asset library) for Microsoft and partners to distribute electronic document configurations to other partners and customers. GER also makes it easier for partners and customers to customize, upgrade, and distribute electronic document formats for their specific business requirements. ![4](https://msdnshared.blob.core.windows.net/media/2016/01/49.png) **LCS Administrators** With January release of LCS, all existing Office 365 administrators of your Microsoft Dynamics AX tenant will also be LCS administrators. Previously, one specific user was assigned the role of LCS administrator. **Business process modeler** We have addressed the issue with B**usiness process modeler** (BPM) search indexing. If you have experienced issues with help content delivery in the newest version of Dynamics AX, this fix helps resolve the issues you have seen. If you have seen the following message in your BPM library, it means that the indexing of the library is pending. ![5](https://msdnshared.blob.core.windows.net/media/2016/01/58.png) Below is a library that has been successfully indexed. ![6](https://msdnshared.blob.core.windows.net/media/2016/01/65.png) **Process data package** We have made significant performance improvements to the process data package creation experience. New Dynamics AX solutions creators can now add database backups to a solution package. ![7](https://msdnshared.blob.core.windows.net/media/2016/01/781024x663.png)
December 2015
-------------

The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the December release of Lifecycle Services.

### NEW FEATURES

Microsoft Dynamics AX Public Preview is here! The public preview of Microsoft Dynamics AX is now available. You can now sign up and deploy a cloud instance of Microsoft Dynamics AX, based on our latest development milestone, known as CTP8. This public preview of Microsoft Dynamics AX can be deployed through Microsoft Dynamics Lifecycle Services. Microsoft Dynamics AX CTP8 is available only to existing Microsoft Dynamics channel partners and customers who are currently enrolled in the Business Ready Enhancement Plan (BREP) service plan. Existing customers can find details on how to get to the preview from [here ](https://mbs.microsoft.com/customersource/global/AX/news-events/news/Microsoft_Dynamics_AX_Public_Preview)and partners can find the details [here](https://mbs.microsoft.com/partnersource/global/news-events/news/Microsoft_Dynamics_AX_Public_Preview). **Language preferences** Starting today, LCS will release the public preview of the language preference feature. To enable this for your account, login to LCS , click on your name on the top right corner, and then select **Preferences**. ![1](https://msdnshared.blob.core.windows.net/media/2015/12/110.png) Select your preferred language from the drop down and then click **Save**. [![2](https://msdnshared.blob.core.windows.net/media/2015/12/21.png)](https://msdnshared.blob.core.windows.net/media/2015/12/21.png) **New Unified library** We have shipped the new APQC unified library for the newest version of Microsoft Dynamics AX . This new library is for CTP 8. [![3](https://msdnshared.blob.core.windows.net/media/2015/12/3.png)](https://msdnshared.blob.core.windows.net/media/2015/12/3.png) **Updated methodologies ** We have also shipped two updated methodologies for the newest version of Dynamics AX. [![4](https://msdnshared.blob.core.windows.net/media/2015/12/4.png)](https://msdnshared.blob.core.windows.net/media/2015/12/4.png)To use these new methodology, login to your LCS project and click **Change methdology**. [![5](https://msdnshared.blob.core.windows.net/media/2015/12/5.png)](https://msdnshared.blob.core.windows.net/media/2015/12/5.png) Select the methodology you want to use and then click **Save**. **Note:** If you want to keep the existing phases and tasks in the methodology keep the toggle set to **Yes**. ![6](https://msdnshared.blob.core.windows.net/media/2015/12/6.png) **New data packages** Over 250 new data packages for CTP 8 were also shipped in this release. To import these to the project, in your LCS project go to **Asset library**, select **Process data package**, and then click **Import**. [![7](https://msdnshared.blob.core.windows.net/media/2015/12/7.png)](https://msdnshared.blob.core.windows.net/media/2015/12/7.png) Select the Process Data Packages from the list and import them into the project. [![8](https://msdnshared.blob.core.windows.net/media/2015/12/8.png)](https://msdnshared.blob.core.windows.net/media/2015/12/8.png) The Microsoft Dynamics AX **Code Upgrade service** will now help you upgrade to CTP8.

## November 2015 update
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the October release of Lifecycle Services.

### NEW FEATURES

**General**

-   Customersource/Partnersource  Admins for Dynamics AX 2012 can now add new users as Admins in Lifecycle services.
-   Office 365 Admins for Dynamics AX can now make existing O365 users Admins in Lifecycle Services from the **Organization users** tile.
-   You can view the list of newly added users on the LCS **Organizational users** list.[![LCS November release notes 1](./media/lcs-november-release-notes-1-1024x528.jpg)](./media/lcs-november-release-notes-1.jpg)
-   When you submit feedback to LCS, you can view the email that is captured as part of the feedback. You also have an option to change this email. Microsoft will use this email for any follow up questions and clarifications. [![LCS November release notes 2](./media/lcs-november-release-notes-2.jpg)](./media/lcs-november-release-notes-2.jpg)

## October 2015 update
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the October release of Lifecycle Services.

###  NEW FEATURES

** General** You can now manage the **notifications** you receive from LCS by using the notification management UI in LCS.  Starting in October, release all project owners will receive emails from cloud-powered support and localization and translation. [![LCS October release notes 1](./media/lcs-october-release-notes-1.jpg)](./media/lcs-october-release-notes-1.jpg) [![LCS October release notes 2](./media/lcs-october-release-notes-2.jpg)](./media/lcs-october-release-notes-2.jpg) LCS will use a **personal access token** for LCS/VSO project interactions. This will be used for all **LCS/VSO** interaction including work item creation, develop + build machine deployment, etc. All LCS projects that were previously configured will need to be reconfigured with a personal access token. Use the following steps to retrieve and set up your token in LCS.

1.  Create a new LCS admin user in VSO.
2.  Login to VSO using an LCS admin account.
3.  Generate a personal access token for the user account. [![LCS October release notes 3](./media/lcs-october-release-notes-3-1024x325.jpg)](./media/lcs-october-release-notes-3.jpg)
4.  Login to LCS.
5.  Browse to project settings for the LCS project, and click setup VSO.
6.  Enter the Visual Studio Online site URL and the personal access token that you generated above.
7.  Continue through the setup process and select the VSO project you want to use for the above LCS project. [![LCS October release notes 4](./media/lcs-october-release-notes-4-1024x576.jpg)](./media/lcs-october-release-notes-4.jpg)

**Cloud-hosted environments**

1.  Support has been added for the Azure Dv2-series virtual machines. These VMs are based on the latest Intel (Haswell) processor and are on average about 35% faster than D-series instances.  Dv2-series VMs are available in 4 data centers at release and will roll-out to others across the world over the next several months. For more information, see the Azure [Virtual Machines Pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/) page.
2.  You can now deploy topologies within the same Lifecycle Services project to different Azure regions. To do so, create an Azure Connector for each region that you want to use. When deploying a topology, select the Azure Connector for the specific region that you want to deploy to. [![LCS October release notes 5](./media/lcs-october-release-notes-5.jpg)](./media/lcs-october-release-notes-5.jpg)
3.  The Development topology now supports larger development teams.
4.  Several reliability and performance-related updates have been made across all topologies.
5.  To enable a better troubleshooting experience, native Azure errors are now surfaced through our error reporting functionality.
6.  An updated AX 2012 R3 CU9 image is now available.

## September 2015 update
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the September release of Lifecycle Services.

### NEW FEATURES

**General** Incremental updates to the **notification framework** provide you with better control for notifications from LCS. Updated experience for SharePoint and Visual studio online setup including addition of the **Action center** to give you better visibility into setup and configuration of VSO and SharePoint online. [![LCS September release notes 1](./media/lcs-september-release-notes-1-300x293.jpg)](./media/lcs-september-release-notes-1.jpg) Improved **user experience** with updates to the controls. The **Recent projects** section will now show recently used and invited projects instead of recently invited projects. [![LCS September release notes 2](./media/lcs-september-release-notes-2-288x300.jpg)](./media/lcs-september-release-notes-2.jpg) Azure active directory **login** for the newest version of Dynamics AX and Microsoft accounts can now use the "Sign in" button to login to LCS. Starting with the September release, Lifecycle services will no longer support Firefox.

## August 2015 update
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the August release of Lifecycle Services.

### NEW FEATURES

**General**

-   Six **LCS solutions** are live in [Azure marketplace](http://azure.microsoft.com/en-us/marketplace/?term=AX) for Microsoft Dynamics AX 2012.
-   LCS solutions are curated industry/vertical-specific content including but not limited to, business processes, code, and data and bundled with a consistent execution methodology which helps steer towards repeatable & predictable implementations. If you are a partner/ISV and would like to work with Microsoft for creating solutions for the newest version of Dynamics AX, please complete the survey found [here](http://aka.ms/ax7lcssolutions) by August 27th, 2015.
-   Re-engineered **notification framework** is in preview this month. This framework will pave the way to light up enhanced notification experiences in LCS in the coming months. Immediate improvements include additional details such as project name and inviting organization details in the project invite emails.

**Business process modeler** Library uploads in **Business process modeler** to have improved error handling and error reporting in case of failure/error conditions. **Cloud-hosted environments**

-   The ability to set SQL Server disk configuration options has now been extended to all topologies that contain multiple VMs. These options enable you to specify the number of disks and the size of each disk to be deployed.

###  Public Preview Features

In this release, the 'Localization & Translation support' tool tile has been given the shorter tile name, 'Localization and Translation' to support the internationalization of LCS tooling. [![LCS August release notes 1](./media/lcs-august-release-notes-1.jpg)](./media/lcs-august-release-notes-1.jpg) Service now contains:

-   Dynamics Regulatory Alert submission. This was previously located under the Cloud Powered support (CPS) tile.
-   Dynamics ERP Translation solution.

For more information on how you can use these services - see [Dynamics regulatory alert submission](http://blogs.msdn.com/b/lcs/archive/2015/06/29/regulatory-alert-submission.aspx)  and [Dynamics ERP translation solution](http://blogs.msdn.com/b/lcs/archive/2015/06/29/microsoft-dynamics-localization-and-translation-support-on-lifecycle-services.aspx). [![LCS August release notes 2](./media/lcs-august-release-notes-2.jpg)](./media/lcs-august-release-notes-2.jpg) **What's next in LCS - survey** We are always working towards improving your LCS experience and we would like to understand how you use LCS for your projects and what other tools and services you use in conjugation with LCS to meet your ERP project implementation/upgrade needs. The data we receive when you complete this [survey](http://aka.ms/lcssurvery) will help us prioritize the efforts and the investment in LCS for the coming months.

## July 2015 update
The Microsoft Dynamics Lifecycle Services team is happy to announce the immediate availability of the July release of Lifecycle Services.

### ** **NEW FEATURES

**General**

-   You can now submit an ERP translation support request for Microsoft Dynamics AX 2012. Details on how you can use this feature can be found [here](http://blogs.msdn.com/b/lcs/archive/2015/06/29/microsoft-dynamics-localization-and-translation-support-on-lifecycle-services.aspx). (This is a Preview Feature.)
-   You can now deploy Microsoft Dynamics AX 2012 R3 CU9 evaluation version from [Azure marketplace](http://azure.microsoft.com/en-us/marketplace/partners/microsoft/microsoft_dynamics_lcs/).

**Business process modeler** At a parent level, you can now combine all child flow charts to make a consolidated view of all child process lines by clicking **Compose child lines**. [![LCS July release notes 1](./media/lcs-july-release-notes-1-1024x474.jpg)](./media/lcs-july-release-notes-1.jpg) You can revert this change by clicking Clear composed line. ![LCS July release notes 2](./media/lcs-july-release-notes-2-1024x512.jpg) **Cloud-hosted environments**

-   Microsoft Dynamics AX 2012 R3 topologies now default to deploying Dynamics AX 2012 CU9. To deploy prior versions of Dynamics AX, click **Advanced Settings** &gt; **Supported Versions**.
-   Dynamics AX 2012 R3 topologies, excluding Demo, now support SQL Server Disk customizations where \#disks and disk sizes can be customized in **Advanced Settings**.

**Update Experience** The new update experience which was made available during the May update for Dynamics AX 2012 R3 is now available for Microsoft Dynamics AX 2012 R2. In order to use this experience, you must have System diagnostics enabled for your AX 2012 R2 environment and this experience is best designed for customers who are on R2 CU7 or R2 CU8.

## June 2015 update
The Microsoft Dynamics Lifecycle Services team is happy to announce the availability of the June release of Lifecycle Services starting 6/26.

### NEW FEATURES

** General**

-   Upgraded UX and enhanced navigation experience including introduction of direct navigation between services.
-   Organization administrators can now view a list of all projects belonging to that organization. Administrators can also add themselves to any project in that list.
-   You can now submit regulatory alerts to Microsoft directly from LCS. You can find additional details on this feature [here](http://blogs.msdn.com/b/lcs/archive/2015/06/29/regulatory-alert-submission.aspx). (This is a Preview Feature.)

** Business process modeler**

-   You can now create hierarchies that have more than 5 levels.

**Cloud-hosted environments**

-   NetBIOS support has been added. To use these options, click Advanced settings &gt; Customize domain settings when deploying your environment.

<!-- -->

-   Enterprise Portal reliability improvements have been made.

<!-- -->

-   When deleting an environment, deployed resources on Azure are now deleted. Keep the following points in mind:

<!-- -->

-   This new feature applies to all environments, including AX 2012 R3, the newest version of Microsoft Dynamics AX, and CRM environments.

<!-- -->

-   The deletion process has two phases. Warnings and recommendations are made during each phase to ensure you have backed up necessary data.

**Phase 1**:  This phase stops and de-allocates (so there are no usage charges) all VM resources. No other resources, such as networks, VIPS, endpoints, storage, SQL Azure databases, are impacted. If you happen to make a mistake, you can recover after this phase is complete. To do so, click **Start** on the environment. **Phase 2**: This phase deletes all deployed resources. To complete this phase, phase 1 must first be completed, and you must enter the name of the environment that you want to delete.

-   When deploying an environment, you can add the environment to an existing Active Director/virtual network.  Deleting an environment does NOT delete any resource that the Cloud-hosted environment tool did not deploy.

## May 2015 update
The following list provides an overview of the changes to Lifecycle Services. For details, see the May release post on the Lifecycle Services [blog](http://go.microsoft.com/fwlink/?LinkId=615179).

-   A new AX 2012 R3 update experience is now publicly available on the Environments page.
-   AxUtil build validation has been removed from Customization analysis. Customization analysis can now process any model files regardless of the exported AxUtil version.
-    If Cloud-powered support cannot infer the kernel version when creating a VM, a VM with the latest kernel version that’s available will be provisioned.
-   Several new features are available for Cloud-hosted environments.
-   Issue search has received significant performance upgrades, and now displays details that indicate when a fix applies to the application, kernel, or both.

## April 2015 update
The following list provides an overview of the changes to Lifecycle Services. For details, see the April release post on the Lifecycle Services [blog](http://go.microsoft.com/fwlink/?LinkId=615180).

-   Several new features are available for Cloud-hosted environments.
-   Business process modeler has several updates.

## March 2015 update
The following list provides an overview of the changes to Lifecycle Services. For details, see the March release post on the Lifecycle Services [blog](http://go.microsoft.com/fwlink/?LinkId=615181).

-   Several new features have been introduced to Cloud-hosted environments to support customers that want to go live with AX 2012 R3 on Azure with a deployment that achieves the Azure SLA, possesses high-availability characteristics in the core AX tiers (AD, SQL, AOS, CLI, and RDS), and acts predictably in expected deployment scenarios.
-   Visual improvements have been made to the Methodology toolset.
-   We now ship updates on weekends instead of during business days.
-   LCS Solutions have been released in private preview. LCS solutions enable partners to create custom content and solutions for AX 2012 R3. If you are interested in creating a solution, learning more, or joining the private beta, please fill out the form here: [http://aka.ms/LCSSolution](http://aka.ms/LCSSolution).
-   Business Process Modeler now allows exporting to an excel format that can be imported into Task Recorder. To use this feature, you must download this hotfix to Task Recorder: [https://fix.lcs.dynamics.com/en/Issue/Resolved?kb=3003077](https://fix.lcs.dynamics.com/en/Issue/Resolved?kb=3003077)

## February 2015 update
### User interface transition

This release includes the full rollout of the reworked experience for managing projects. This is now the primary interface for all users. It is possible to view the previous user interface by clicking the **Return to classic mode** tile on the dashboard.

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="https://i-technet.sec.s-msft.com/areas/global/content/clear.gif" title="Important" alt="Important" id="alert_caution" class="cl_IC46226" /><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>In the March release, some classic project management features will be removed. Be sure that you migrate any content from your existing projects to the new UI before March.
<ul>
<li>Document link tracking for projects has been replaced with SharePoint integration.</li>
<li>Project plans have been replaced by Project methodology. Project plans, phases, summaries, and advanced user role management will be removed in the first week of March.</li>
</ul></td>
</tr>
</tbody>
</table>

### Preview features

-   The preview of the System diagnostics AX Crash and hang analysis tool helps you find known solutions for AOS crashes or hangs based on the information found in AX dump files.
-   Cloud-powered support provides a public preview that allows a partner to manage incidents for several customers from a new tile on the homepage.

### New features

-   Cloud hosted environments has several new features:
    -   A new developer topology with a separate SQL Server VM
    -   Service accounts can now be customized
    -   Virtual Machine names can now be customized
    -   All topologies now default to D-series virtual machines
-   Business process modeler now allows much better import of library content by dragging and dropping.
-   A new Environments section has been added to the dashboard to better manage your deployed AX systems.
-   New roles have been added to split out managing environments, and performing operational tasks.
    -   Environment manager. Members of this role have access to all tools in Lifecycle Services, can manage cloud-hosted environments and can add other users to the team member role.
-   Operations user. Members of this role have access to the following tools in Lifecycle Services - System diagnostics, Issue search, Cloud-powered support and Updates.

## January 2015 update
### Preview release

The preview release has been updated to include the following features:
-   Methodology tasks can now be ordered
-   Preview management allows users to see and play with available betas and previews.

### New features

-   Infrastructure estimator now estimates D-series Azure resources and provides warnings and statistics when implementations are too large to size.
-   Issue Search now lists Management Reporter 2012 and Connector for Microsoft Dynamics issues.
-   Cloud powered support now automatically installs AX 2012 R3 application hotfixes for environments that require them.
-   System Diagnostics now includes the following rules for SQL Server and database settings.
    -   Priority Boost SQL Server configuration setting has been changed from the default value
    -   Max Degree of Parallelism not set to 1
    -   Max server memory not set to an optimal value
    -   Lightweight pooling is enabled
    -   Max worker threads has been modified
    -   Auto Create Statistics option disabled for the Dynamics AX database
    -   Full recovery model not implemented for Dynamics AX databases
    -   Auto Update Statistics option disabled for Dynamics AX database
    -   Auto Close option enabled for the Dynamics AX database
    -   Auto Shrink option enabled for the Dynamics AX database
    -   Read Committed Snapshot Isolation (RCSI) database option not enabled for the Dynamics AX database
    -   Allow Snapshot Isolation is enabled for the Dynamics AX database
    -   TempDB and Dynamics AX database collations do not match
    -   Dynamics AX data file located on system drive
    -   TempDB files not equal in size
    -   TempDB log file auto growth increment not a fixed size between 100 MB and 500 MB
    -   TempDB log file too small
    -   Dynamics AX log file located on system drive
    -   TempDB data file located on system drive
    -   Dynamics AX database data file auto growth increment not a fixed size between 100 MB and 500 MB
    -   Dynamics AX database log file auto growth increment not a fixed size between 100 MB and 500 MB
    -   Number of TempDB files not optimal
    -   Dynamics AX database log low on free space
    -   Page life expectancy less than 1200 seconds

## December 2014 update
### Preview release

The preview release has been updated to include relaxed validation rules for SharePoint Online integration.
### New features

All services have been updated for CU8
1.  Upgrade analysis can be used for moving from AX 2012 to AX 2012 R3 CU8
2.  Issue search can be used to find known issues for AX 2012 R3 CU8. Search for "CU8 known issue". (The quotation marks are required)
3.  Cloud-Hosted Environments includes the following updates:
    -   The Test environment (previously referred to as the Standard Dev/Test environment) has been updated for AX 2012 R3 CU8. The CU8 version is deployed by default. If you want to deploy the AX 2012 R3 version, click Advanced settings &gt; Supported version during deployment.
    -   CU8 demo data is included on the SQL Server VM disk for easy import.
    -   RemoteApp is supported in Test environments when a Remote Desktop Services instance is deployed. You can select the RemoteApp option during deployment when you click Advanced settings &gt; Customize remote desktop services. For more information about RemoteApp, see http://azure.microsoft.com/en-us/services/remoteapp/.
    -   Azure Basic tier VMs are no longer supported, because they are not compatible with our deployment methods and application needs. Only Standard tier or higher VMs are available for deployment.
        | ![Note](https://i-technet.sec.s-msft.com/areas/global/content/clear.gif "Note")**Note** |
        |-----------------------------------------------------------------------------------------|
        | Note: CU8 Demo and Retail environments are not yet available, but will be coming soon.  |

4.  System Diagnostics contains 8 new rules for General Ledger and Budgeting that help identify data inconsistencies that often cause issues for Management Reporter integrations:
    -   MainAccounts that don’t have a corresponding account category assigned
    -   An invalid Ledger value assigned within a General Journal Entry, Budget Register Entry, or Budget Planning Entry
    -   A child record with no corresponding header record within a General Journal Account Entry, Budget Register Entry, or Budget Planning Entry
    -   Any invalid DataAreaID assigned within a Budget Register Entry

## November 2014 Update
### Preview release

This release includes a reworked experience with several preview features. These include:
-   A new Methodology tool for projects. A starter methodology is provided, called Sure Step Agile. For more information, see [Methodologies (Lifecycle Services, LCS)](methodologies-lcs.md).
    -   You can attach templates, and documents to tasks
    -   You can create your own methodologies
-   SharePoint Online integration for document storage.
-   Visual Studio Online Team Foundation Server integration for tracking tasks and bugs.
-   Reworked project user management, invitation process, and streamlined project types.
-   All tools and services have been moved from InformationSource to the new Downloadable tools section of Lifecycle Services, which is available in the new preview interface, at the far right.

### New features

This release includes the following new features:
-   A reworked sign in page where you can now:
    -   Learn about Lifecycle Services
    -   Find marketing content to share
-   Issue search now supports filtering of product issues by:
    -   Module
    -   Country
    -   Configuration key
    -   Industry

## October 2014 release updates
Updates released in October 2014 included:
-   The Configuration manager tool has been released in beta. It allows you to save configurations, store them locally or in the cloud, and copy a configuration from one system to another. For more information, see [Configuration manager (Lifecycle Services, LCS)](configuration-manager-lcs.md).
-   In Business process modeler, you can now search for business processes and artifacts, and reorder tasks in hierarchies.
-   The Customization analysis service has an improved report that provides a heat map for estimated performance impact, estimated functional impact, rule reliability, estimated effort to fix an issue.
-   The Upgrade analysis tool now includes an impact analysis heat map.
-   We have provided more informative and actionable error messages to handle common scenarios that users may encounter when signing in to Lifecycle Services, such as expired services plans.

## September 2014 release updates
Updates released in September 2014 included:
-   The Cloud-hosted environments tool now has customizable settings for domains, virtual networks, and user accounts.For more information, see [Deploy Microsoft Dynamics AX 2012 R3 on Azure using Lifecycle Services](deploy-2012-r3-azure-lcs.md).
-   The Issue search tool now shows planned and open regulatory features, and includes searchable resources for Regulatory feature updates and Regulatory white papers, registrations, and reports.For more information, see [Issue search (Lifecycle Services, LCS)](issue-search-lcs.md).
-   The Infrastructure estimator tool has become an independent tool that can be accessed outside of the Usage profiler, and now provides sizing for non-production environments (Dev/Test/Training).For more information, see [Infrastructure estimator (Lifecycle Services, LCS)](infrastructure-estimator-lcs.md).
-   The Upgrade analysis tool has new summary information in the report.
-   Support for Safari (v5.1.7) and Firefox (v32) has been added.

## August 2014 release updates
Updates released in August 2014 included:
-   The Business process modeler now only allows libraries to be copied. The previously available Add functionality also copied libraries, so it was removed.
-   The Business process modeler supports uploading Microsoft Visio diagrams into process libraries. For more information, see [Flowcharts in Business process modeler](flowcharts-business-process-modeler.md).
-   The Cloud-hosted environments tool now has:
    -   A new development and testing (5 box) environment.
    -   Several new retail environments.
    -   A choice of the number of virtual machines and their size when you are deploying.

    For more information, see [Deploy Microsoft Dynamics AX 2012 R3 on Azure using Lifecycle Services](deploy-2012-r3-azure-lcs.md).
-   The Issue search tool now includes proactive fixes released by Microsoft.
-   Nearly 300 error messages have been rewritten to be more clear and helpful.

## July 2014 release updates
Updates released in July 2014 included:
-   The Business process modeler now includes a new, discrete manufacturing APQC library.
-   The License sizing estimator generates a report that now shows actual license usage for connected environments.
-   The System diagnostics has been updated to include support for Microsoft SQL Server 2014.
-   The System diagnostics has been updated to include support for connections behind proxies.
-   The Cloud-powered support tool now displays premier support cases.
-   The Cloud-hosted environments tool now enables you to turn Azure virtual machines on or off.
-   The Cloud-hosted environments tool now provides links that enable you to connect to Azure virtual machines (via .rdp files).
-   The session inactivity time-out period has been increased to 12 hours.

## June 2014 release updates
Updates released in June 2014 included:
-   New Retail APQC library available in Business process modeler (APQC Retail Industry)
-   Enhanced data validation has been added to the Usage profiler site and spreadsheet. Error messages on upload now include column name and number, and in the spreadsheet, include color coding.
    | ![Note](https://i-technet.sec.s-msft.com/areas/global/content/clear.gif "Note")**Note** |
    |-----------------------------------------------------------------------------------------|
    | Validation errors in the spreadsheet only appear if macros are enabled.                 |

    New validation features include:
    -   Data type
    -   Mandatory field
    -   Data consistency
-   Selection of multiple filters is now possible in Issue search. You can use multiple filters to more quickly find the results you want.
-   Upgrade analysis now supports minor version (in-place) upgrade from AX 2012 to AX 2012 R3. You can upload a zipped model store file for analysis. For more information, see [Upgrade analysis (Lifecycle Services, LCS)](upgrade-analysis-lcs.md).
-   Consolidated incident list view in cloud powered support now shows all incidents associated with a project, instead of only those incidents filed by the person logged in.
-   Attachments are now supported in cloud powered support.
-   Three new customization analysis rules have been added.

## May 2014 release updates
May 2014 release updates included:
-   Microsoft Azure deployment of Microsoft Dynamics AX 2012 R3: Support for an automated deployment of AX 2012 R3. For more information, see [What's new: Azure deployments of Microsoft Dynamics AX 2012 R3](https://technet.microsoft.com/EN-US/library/dn716026.aspx).
-   Cloud-powered support is a part of Lifecycle Services that enables customers to manage support incidents. It enables you to create a virtual machine in Azure that has the same hotfixes installed as your local environment, reproduce and record the incident on the virtual machine and then submit it to our support team. Support follows up by investigating, and if possible, testing a fix on the virtual machine, and sending it back to you to verify. For more information, see [Cloud-powered support (Lifecycle Services, LCS)](cloud-powered-support-lcs.md).
-   Over 100 new business process models have been added to the APQC library to support supply chain management, financials, and service industries.
-   Updates for AX 2012 R3: The Updates page on Lifecycle Services hosts the update installer for Microsoft Dynamics AX 2012 R3 that is used for cumulative updates, and the group of most recent updates. It also provides access to groups of updates that can be used for slipstream installations. For more information, see [Updates for Microsoft Dynamics AX 2012 R3 (Lifecycle Services, LCS)](update-2012-r3-lcs.md).
-   Issue search now includes regulatory feature updates.
-   The following tools on Lifecycle Services have been updated to support AX 2012 R3:
    -   Business process modeler
    -   Customization analysis
    -   License sizing estimator
    -   Issue search
    -   System diagnostics

## March 2014 release updates
March 2014 release updates included:
-   Issue search: Support for searching for issues by AOT path added.
-   Business process modeler: Support for removing gaps from a diagram, and opening a AX 2012 form from a diagram.
-   Microsoft Dynamics ERP RapidStart Services: Support for creating and opening RapidStart Services projects from the project page.

## January 2014 release updates
January 2014 release updates included:
-   Improved user interface, text, and navigation
-   Server licenses added to License Sizing Estimator
-   Support for AX 2012 R2 CU7 added to the Customization Analysis Tool
-   Importing users and security roles from an existing project added
-   Auto recovery capabilities added to Customization Analysis VMs

[![LCS July release notes 2](./media/lcs-july-release-notes-2-300x150.jpg)](./media/lcs-july-release-notes-2.jpg)[![LCS October release notes 5](./media/lcs-october-release-notes-5-300x131.jpg)](./media/lcs-october-release-notes-5.jpg)

See also
--------

[What’s new or changed](whats-new-changed.md)

