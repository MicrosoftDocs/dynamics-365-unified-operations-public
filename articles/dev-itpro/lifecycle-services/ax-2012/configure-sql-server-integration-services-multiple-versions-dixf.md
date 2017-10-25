---
# required metadata

title: Configure the version of SSIS used by the AX 2012 Data import/export framework
description: This topic provides information about how to configure the SSIS that is being used by the data import/export framework in Dynamics AX 2012.
author: kfend
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: dynamics-ax-2012 
ms.service:
ms.technology:

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 2012, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 51562
ms.assetid: 02188740-e0d9-4b25-9512-dfd15e68020f
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Configure the version of SSIS used by the AX 2012 Data import/export framework

[!include[banner](../../includes/banner.md)]




This topic only applies to environments that are running Microsoft Dynamics AX 2012 R2 with [KB 3018235](https://mbs2.microsoft.com/Knowledgebase/KBDisplay.aspx?scid=kb;en-us;3018235) installed. KB 3018235 is required to use Data Import/Export Framework for AX 2012 R2 CU7 with SQL Server 2014 Integration Services. If you are in an environment in which two versions of Microsoft SQL Server Integration Services are installed on the same computer, by default, the Data Import/Export Framework Windows service will attach to the oldest version of Integration Services that it can find. SQL Server 2008 Integration Services is the oldest supported version. You can force the Data Import/Export Framework to use another version of Integration Services by using redirecting assembly versions. We strongly recommend that you use Data Import/Export Framework in an environment with only one version of SQL Server Integration Services installed. To see which versions of Integration Services are supported with the Data Import/Export Framework, see the [Microsoft Dynamics AX 2012 System Requirements](http://go.microsoft.com/fwlink/?LinkId=165377).

## Force the Data import/export framework to use a version of Integration Services other than the default
You can force the Data Import/Export Framework to use a version of Integration Services other than the default by [redirecting assembly versions](https://msdn.microsoft.com/en-us/library/7wd6ex19(v=vs.110).aspx).

| Caution:                                                                                                                                                                                                    |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If the assembly version redirection is setup incorrectly, for example, by redirecting to a version of Integration Services that is not installed, the Data Import/Export Framework will not work correctly. |

1.  Locate the installation directory of the Data Import/Export Framework service component.
2.  Open the file **Microsoft.Dynamics.AX.DMF.SSISHelperService.exe.config** in a text editor.
3.  Locate the **&lt;runtime&gt;** element in the file. Inside this element, add the following code.
    -   Code to redirect to SQL Server 2012 Integration Services
            <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.DTSPipelineWrap"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />
                  </dependentAssembly>
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.DTSRuntimeWrap"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />
                  </dependentAssembly>
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.ManagedDTS"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />
                  </dependentAssembly>
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.PipelineHost"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />
                  </dependentAssembly>
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.SQLTask"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />
                  </dependentAssembly>
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.XmlSrc"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />
                  </dependentAssembly>
                </assemblyBinding>

    -   Code to redirect to SQL Server 2014 Integration Services
                <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.DTSPipelineWrap"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="12.0.0.0" />
                  </dependentAssembly>
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.DTSRuntimeWrap"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="12.0.0.0" />
                  </dependentAssembly>
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.ManagedDTS"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="12.0.0.0" />
                  </dependentAssembly>
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.PipelineHost"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="12.0.0.0" />
                  </dependentAssembly>
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.SQLTask"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="12.0.0.0" />
                  </dependentAssembly>
                  <dependentAssembly>
                    <assemblyIdentity name="Microsoft.SqlServer.XmlSrc"
                      publicKeyToken="89845dcd8080cc91" />
                    <bindingRedirect oldVersion="10.0.0.0" newVersion="12.0.0.0" />
                  </dependentAssembly>
                </assemblyBinding>

4.  Save the file.
5.  Restart the Data Import/Export Framework service.
6.  Test that your changes are working as expected.





