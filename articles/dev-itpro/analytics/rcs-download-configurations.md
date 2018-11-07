---
# required metadata

title: Import Electronic reporting (ER) configurations from Regulatory Configuration Services (RCS)
description: This topic provides information about importing electronic reporting configurations from Regulatory Configuration Services. 
author: NickSelin
manager: AnnBe
ms.date: 11/07/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERSolutionRepositoryTable
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Import Electronic reporting (ER) configurations from Regulatory Configuration Services (RCS)

[!include [banner](../includes/banner.md)]

You can use Regulatory Configuration Services (RCS) to design Electronic reporting (ER) configurations. The ER tool provides access to the list of configurations that have been configured in each instance of RCS that has been provisioned for your company. By using this feature, you can import configurations that you configured in an RCS instance into the current Finance and Operations instance. Once imported, the configurations can be used for handling incoming documents or for generation of outgoing electronic documents.

To learn more about this feature, complete the example in this topic or play the task guide, ER Import configurations from RCS (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process), which walks through how the ER configurations can be imported from RCS instance into the current Finance and Operations instance.


## Example: Import an ER configuration from RCS

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can import a new version of an Electronic reporting (ER) configuration from Microsoft Regulatory Configuration Service (RCS). In this example, you will select the desired version of the ER configuration that has been configured in RCS instance and import it into the current Finance and Operations instance for sample company, Litware, Inc. These steps can be performed in any company as ER configurations are shared among companies. To complete these steps, you must first complete the steps in the “Create a configuration provider and mark it as active” procedure. For completion of these steps, it is also required to have access to RCS instance containing at least one ER configuration in either “Completed” or “Shared” status.

1. Go to **Organization administration > Workspaces > Electronic reporting**. 
2. Make sure that the configuration provider for the sample company **Litware, Inc.** is available and marked as **Active**. If you don’t see this configuration provider, complete the steps in the procedure [Create a configuration provider and mark it as active](er-configuration-provider-mark-it-active-2016-11.md). 
3. If you have no RCS environment provisioned to your company, click **Regulatory service – Configuration** in the **External Links** section and follow the instructions to provision an RCS environment. 
4. Click **Electronic reporting parameters** in the **Related links** section. 
5. Expand the **RCS** tab. 
6. If RCS environment has been already provisioned to your company, use presented on the page URLs to access it. 
7. Close the page. 

### Register a new ER repository 
1. In the list, mark the selected row. 
   - Select Litware, Inc. provider. 

2. Click Repositories. 

3. Click Add to open the drop dialog. 

4. In the Configuration repository type field, enter 'RCS'. 

5. Click Create repository. 

6. In the RCS environment display name field, enter or select a value. Select the desired RCS instance. Note that you can have several of them. 

7. Click OK. 

### Import ER configurations from RCS based repository 

1. Click Show filters. 

2. Apply the following filter: Enter a filter value of "RCS" on the "Name" field using the "begins with" filter operator. 

3. When you open the selected repository, on the “Connect to Regulatory Configuration Service” page click “Click here to connect to Regulatory Configuration Service” link. 

4. Click Open. 

5. Click Close. 

6. Select the desired version of ER configuration and click ‘Import’ to bring it in the current Finance and Operations instance.

## Additional resource
- [Electronic reporting overview](general-electronic-reporting.md)
