---
# required metadata

title: Record entry points in Dynamics AX Enterprise Portal
description: You can record business process flows in Enterprise Portal for Microsoft Dynamics AX by using event traces. You can then view the business process flows in the Security Development Tool.
author: kfend
manager: AnnBe
ms.date: 2017-04-04
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
ms.search.scope: AX 2012 R3 CU8
# ms.tgt_pltfrm: 
ms.custom: 74812
ms.assetid: 72a6964d-e8b6-4c3a-8b74-bd6550711f2a
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: AX 2012 R3 CU8

---

# Record entry points in Dynamics AX Enterprise Portal

You can record business process flows in Enterprise Portal for Microsoft Dynamics AX by using event traces. You can then view the business process flows in the Security Development Tool.

| **Note**                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| This is pre-release documentation of a preliminary nature and is subject to change at any time without notice. Microsoft cannot guarantee the accuracy of any information provided herein. |

## Collect event traces for Enterprise Portal entry points by using Windows Performance Monitor
1.  On a computer that is running the instance of Enterprise Portal that you want to collect event traces from, open Windows Performance Monitor. In the navigation pane, under **Data Collector Sets**, right-click **User Defined**, select **New**, and then click **Data Collector Set**.
2.  Enter a unique name for the new data collector set. Select **Create from a template**, and then click **Next.**
3.  Click **Browse**, and then select the EP **EntryPointTracingTemplate.xml** template that was installed together with the Security Development Tool. Click **Next**.
4.  Enter the address of the root directory where you want to save the data, or click **Browse** to search for a directory. Click **Next**.
5.  Click **Finish**.
6.  Select the new data collector set, and then click **Start**.
7.  Navigate to the Enterprise Portal site, and execute your business scenario.
8.  Stop the data collector set.
9.  Convert the trace log to XML format.
    1.  Open **Windows Event Viewer**.
    2.  Right-click the **Applications and Service Logs** node, and then select **Open Saved Log**.
    3.  Select the output file that you created in step 4. Output files have the .etl extension.
    4.  When you are prompted, click **Yes** to create a new copy of the event log.
    5.  Enter a unique name for the log, and then click **OK**. The log is displayed in the **Saved Logs** node.
    6.  Right-click the saved log, and then select **Save All Events As**.
    7.  In the **Save as type** field, select **Xml (XML File) (\*.xml)**, and then enter a unique name for the file. You do not have to include display information.

## Load the trace file
1.  On the ribbon of the main form, click **Load trace file**.
2.  Select the .xml file that was created by using the Enterprise Portal event traces. A new window opens that displays all entry points that have been recorded.

    | **Tip**                                                                                                                                                                                 |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Sort the entry points by the System user role access level column, and then remove all entry points for which the access level of the System User role is anything other than NoAccess. |

3.  To update the level of access for the recorded entry points, select multiple rows in the list, and then click **Mark as recorded**. You are returned to the main form, and the entry points are marked as recorded. From the main form, you can use the **Set entry point permissio**ns function to update the access level. When you have finished, you can switch back to the window that displays the trace data for the Enterprise Portal entry point by clicking **Go to the Enterprise Portal trace data window**.



