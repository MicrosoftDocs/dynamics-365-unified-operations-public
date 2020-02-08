---
# required metadata

title: Copy Variables to chain test cases
description: This topic shows how the Regression Suite Automation Tool can be used to chain test cases, which is the ability of a test to pass values to other tests. 
author: robadawy
manager: AnnBe
ms.date: 08/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21631
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0

---

# Copy Variables to chain test cases

[!include [banner](../../includes/banner.md)]

One of the key features of the Regression Suite Automation Tool is the chaining of test cases, that is, the ability of a test to pass values to other tests. Test cases are executed according to their defined order in the Azure DevOps test plan, which can also be updated in the test tool itself. It is important to correctly order the tests if you want to pass variables from one test case to the other.

To save the value of a variable while recording the test in Task Recorder, right-click the field and select **Task recorder > Copy**, as shown below. This will save the variable in the recording file. This variable can be used in subsequent tests. 
 
![Copy menu item in task recorder](media/task-recorder-copy.png)

When RSAT generates the Excel parameters file, these saved values appear in the **Saved variables** table on the **General** Tab.
 
![Saved variables in Excel](media/saved-variables.png)
 
To reuse these variables during test play back, copy the variable name and use it in place of a parameter value in the data file of another test (or the same test), as shown below. 
 
![Reusing variables in Excel](media/reuse-variables.png)
 
Variables can be used in the same test case where they are defined and can also be passed between tests during the same test run.

## Support for formulas of saved variables

You can create formulas that contain saved (copied) variables. If you have been using an older version of the Regression Suite Automation Tool, you will need to regenerate new Excel parameter files to take advantage of this functionality. Supported operators are **+**, **-**, **/** and **\***. Only numerical variables can be used in the Regression Suite Automation Tool formulas. Strings or dates are not supported. Always specify variable names within double braces **{{varname}}**. For example, **{{var1}} + {{var2}}**.

In the image below, two different variables are used in a formula.
 
![Creating a formula in Excel](media/formulas.png)

## Use variables in message validation

You can also use a saved variable as part of a string in the Message Validation tab. Here is an example that validates that the message `Customer account {{variable name}} already exists.` It appears in the infolog during test execution. `{{variable name}}` is a variable that is copied during the recording.

Saved (Copied) variables can be used within the same test case or across more than one test case in the same test suite.

![message with variable](media/rsat-message-with-variable.png)

