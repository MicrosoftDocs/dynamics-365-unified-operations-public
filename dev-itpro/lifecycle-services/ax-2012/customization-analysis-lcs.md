---
# required metadata

title: Customization analysis
description: In Microsoft Dynamics Lifecycle Services, Customization analysis offers Microsoft Dynamics AX 2012 customers an automated tool that validates the customer’s model files against Microsoft Dynamics AX best-practice rules for tables, classes, forms, and enums. It then generates reports, including a summary report display on the site, a detailed Microsoft Excel report that lists all issues, and a developer report that the developer can load in the Microsoft Dynamics AX development environment. 
author: RobinARH
manager: AnnBe
ms.date: 2015-12-05 23 - 24 - 44
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
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 19021
ms.assetid: 58b1acbc-2288-4417-8dcf-c6239a66730a
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.dyn365.intro: 
ms.dyn365.version: 2012

---

# Customization analysis

In Microsoft Dynamics Lifecycle Services, Customization analysis offers Microsoft Dynamics AX 2012 customers an automated tool that validates the customer’s model files against Microsoft Dynamics AX best-practice rules for tables, classes, forms, and enums. It then generates reports, including a summary report display on the site, a detailed Microsoft Excel report that lists all issues, and a developer report that the developer can load in the Microsoft Dynamics AX development environment. 

Prerequisites
-------------

You must have Microsoft Dynamics AX 2012 model files to be analyzed. For more information about model files, see [How to: Export and Import a Model](http://msdn.microsoft.com/library/c2449a03-7574-4b9d-8518-9005b560209f(AX.60).aspx).

## Getting started
To use Customization analysis, you must upload model files and then evaluate the reports to determine what changes you want to make.

### Upload model files

1.  [Go to Lifecycle Services](https://lcs.dynamics.com).
2.  Open a project, and then click the **Customization analysis** tile.
3.  Click **Add**, and then, on the **Customization analysis: Create job** page, enter a name, the appropriate version of Microsoft Dynamics AX, and the appropriate build.
4.  Click **Create**.
5.  Click **Add files**, browse to the model that you want to analyze, and click **Upload**. You can upload multiple model files to analyze.
6.  Click **Analyze Code**. The site processes the files, and then generates reports. During processing, status indicators update. **Note:** You can leave the page while processing continues. Processing may take 10 minutes or longer.

### Evaluate reports

Customization analysis checks your model files against the Microsoft Dynamics AX best-practice rules for tables, classes, forms, and enums. It then generates detailed reports of instances where your code deviates from those rules. After processing is complete, you can select the reports that you would like to review. Customization analysis provides the following types of reports:

1.  An HTML Customization Analysis report that you can view in a browser.
2.  An Excel file that you can use to review the errors that are generated.To view this report, click **View**, and then open the file.
3.  An HTML developer report that you can open in a Microsoft Dynamics AX developer environment.To view this report in the Microsoft Dynamics AX development environment, perform the following steps:
    1.  Click **View**.The file will open in a browser window.
    2.  Save the report to a computer in your development environment.
    3.  In the **Compiler output** window, click **Import**, and select the file to open it.
    4.  You can double-click any line within the report to open the object and line with the reported issue.

### Remove a customization job

To remove a job from the list of customizations for a project, hover over the job name, then click the box to the left, and click the **Remove** button.

See also
--------

[Best Practices for Microsoft Dynamics AX Development](http://msdn.microsoft.com/library/833e44ff-d89a-459a-84be-0cc5da57ee90(AX.60).aspx)

