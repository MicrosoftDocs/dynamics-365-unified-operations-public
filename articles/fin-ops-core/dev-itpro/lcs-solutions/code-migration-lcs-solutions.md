---
# required metadata

title: Migrate code for Finance and Operations apps solutions
description: This topic describes how to upgrade and analyze your code in Microsoft Dynamics Lifecycle Services (LCS).
author: kfend
ms.date: 06/13/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 196993
ms.assetid: aa01254e-4c18-43e4-81a1-0ef42a27871d
ms.search.region: Global
# ms.search.industry: 
ms.author: omarc

---

# Migrate code for Finance and Operations apps solutions

[!include[banner](../includes/banner.md)]

To complete your solution package, the first step is to upgrade your code by using the best practices in **Migrate and Create Finance and Operations Apps Solutions** in Microsoft Dynamics Lifecycle Services (LCS). After that step is completed, you must run the Customization Analysis Report (CAR). This report analyzes your customization and extension models, and runs a predefined set of best practice rules. 

To generate the CAR, run the following command on a development environment.

```Console
xppbp.exe -metadata=<local packages folder> -all -model=<ModelName> -xmlLog=C:\BPCheckLogcd.xml -module=<PackageName> -car=<reportlocation>
```

Here is an example of this command.

```Console
xppbp.exe -metadata=C:\Packages -all -model=MyAppSuiteCustomizations -xmlLog=C:\temp\BPCheckLogcd.xml -module=ApplicationSuite -car=c:\temp\CAReport.xlsx
```

The xppbp.exe file is located in c:\\packages\\bin or I:\\AosService\\Packages\\LocalDirectory\\bin. You must resolve any warnings or errors that appear on the **Issues** tab of the report. You must then submit a copy of the CAR to Microsoft before your validation meeting. For more information, see [Customization Analysis Report (CAR)](../dev-tools/customization-analysis-report.md). For information about issues and exceptions, see the [Customization Analysis Report: Exceptions and known issues](https://community.dynamics.com/ax/b/newdynamicsax/archive/2016/03/21/customization-analysis-report-exceptions-and-known-issues) post on the Dynamics 365 Community blog.

## Extensibility
In Microsoft Dynamics 365 for Finance and Operations version 8.0 (April 2018), all product models are sealed. Therefore, only extension-based customizations are currently supported. For more information about extensibility, see [Extensibility](../extensibility/extensibility-home-page.md).

The first step in completing your solution package is to upgrade your code using the best practices in <strong>Migrate and Create Finance and Operations Apps Solutions</strong> in LCS. After this step is complete, you must run the Customization Analysis report. This report analyzes your customization and extension models, and runs a predefined set of best practice rules. 

To generate the Customization Analysis report (CAR), run the following command on a development environment.

```Console
xppbp.exe -metadata=<local packages folder> -all -model=<ModelName> -xmlLog=C:\BPCheckLogcd.xml -module=<PackageName> -car=<reportlocation>
```

Here's an example of how this command might look.

```Console
xppbp.exe -metadata=C:\Packages -all -model=MyAppSuiteCustomizations -xmlLog=C:\temp\BPCheckLogcd.xml -module=ApplicationSuite -car=c:\temp\CAReport.xlsx
```

The xppbp.exe file is located in *c:\packages\bin* or *I:\AosService\Packages\LocalDirectory\bin)*. Any warnings or errors that appear on the **Issues** tab of the report must be resolved. A copy of the CAR report must be submitted to Microsoft prior to your validation meeting. For more information, see [Customization Analysis Report (CAR)](../dev-tools/customization-analysis-report.md) or refer to the [Dynamics Community blog](https://community.dynamics.com/ax/b/newdynamicsax/archive/2016/03/21/customization-analysis-report-exceptions-and-known-issues) for issues and exceptions.

## Additional resources
[Requirements for publishing apps on AppSource](lcs-solutions-app-source.md)

[Develop and customize home page](../dev-tools/developer-home-page.md#code-migration)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
