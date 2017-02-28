---
# required metadata

title: Migrate code for an LCS solution
description: The first step in completing your solution package is to upgrade your code using the best practices in <strong>Migrate and Create Dynamics AX Solutions</strong> in LCS. For more details on code migration, refer to this <a href="http - //ax.help.dynamics.com/en/wiki/technical-concepts-guide/#code-migration">page</a>.  After this step is complete, you must run the Customization Analysis report. This report analyzes your customization and extension models, and runs a predefined set of best practice rules. 
author: kfend
manager: AnnBe
ms.date: 2016-10-03 22 - 50 - 41
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
ms.search.scope: Lifecycle Services
# ms.tgt_pltfrm: 
ms.custom: 196993
ms.assetid: aa01254e-4c18-43e4-81a1-0ef42a27871d
ms.search.region: Global
# ms.search.industry: 
ms.author: omarc
ms.dyn365.ops.intro: 
ms.dyn365.ops.version: 

---

# Migrate code for an LCS solution

The first step in completing your solution package is to upgrade your code using the best practices in <strong>Migrate and Create Dynamics AX Solutions</strong> in LCS. For more details on code migration, refer to this <a href="http - //ax.help.dynamics.com/en/wiki/technical-concepts-guide/#code-migration">page</a>.  After this step is complete, you must run the Customization Analysis report. This report analyzes your customization and extension models, and runs a predefined set of best practice rules. 

To generate the Customization Analysis report (CAR), run the following command on a Microsoft Dynamics AX development environment.

    xppbp.exe -metadata=<local packages folder> -all -model=<ModelName> -xmlLog=C:BPCheckLogcd.xml -module=<PackageName> -car=<reportlocation>

Here's an example of how this command might look.

    xppbp.exe -metadata=C:Packages -all -model=MyAppSuiteCustomizations -xmlLog=C:tempBPCheckLogcd.xml -module=ApplicationSuite -car=c:tempCAReport.xlsx

The xppbp.exe file is located in *c:packagesbin* or *I:AosServicePackagesLocalDirectorybin)*. Any warnings or errors that appear on the **Issues** tab of the report must be resolved. A copy of the CAR report must be submitted to Microsoft prior to your validation meeting. For more information, see the Dynamics AX Help wiki topic, [Customization Analysis Report](customization-analysis-report.md) or refer to the [Dynamics Community blog](http://community.dynamics.com/ax/b/newdynamicsax/archive/2016/03/21/customization-analysis-report-exceptions-and-known-issues) for issues and exceptions.

See also
--------

[LCS Solutions for AppSource home page](lcs-solutions-app-source.md)

[Technical Concepts Guide for code migration](developer-landing-page.md#code-migration)

