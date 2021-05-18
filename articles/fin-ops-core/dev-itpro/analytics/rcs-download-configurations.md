---
# required metadata

title: Import Electronic reporting (ER) configurations from Regulatory Configuration Services (RCS)
description: This topic provides information about how to import Electronic reporting (ER) configurations from Regulatory Configuration Services (RCS).
author: NickSelin
ms.date: 04/29/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERSolutionRepositoryTable
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
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

You can use Regulatory Configuration Services (RCS) to design Electronic reporting (ER) configurations. The ER tool provides access to the list of configurations that have been configured in each instance of RCS that has been provisioned for your company. You can use this feature to import configurations that you configured in an RCS instance into the current instance. After configurations are imported, they can be used to handle incoming documents or generate outgoing electronic documents.

To learn more about this feature, complete the example in this topic. Alternatively, download and play the [ER Import configurations from RCS](https://download.microsoft.com/download/0/4/e/04e13839-e423-442b-a6c2-dd35b1045c2d/Dynamics%20365%20for%20Finance%20and%20Operations%208.1%20Electronic%20reporting%20task%20guides.zip) task guide, which is part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process. It walks you through the process of importing ER configurations from an RCS instance into the current instance.

## Example: Import an ER configuration from RCS

This example shows how a user in the System Administrator or Electronic Reporting Developer role can import a new version of an ER configuration from RCS. In this example, you select the desired version of the ER configuration that has been configured in an RCS instance, and you import that version into the current instance for a sample company that is named Litware, Inc. These steps can be completed in any company, because ER configurations are shared among companies.

To complete the steps in this example, you must first complete the steps in [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md). You must also have access to an RCS instance that contains at least one ER configuration that has a status of either **Completed** or **Shared**.

1. Go to **Organization administration \> Workspaces \> Electronic reporting**.
2. On the **Localization configurations** page, in the **Configuration providers** section, make sure that the configuration provider for the Litware, Inc. sample company is listed, and that it's marked as **Active**. If you don't see this configuration provider, follow the steps in [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).
3. If no RCS environment has been provisioned for your company, in the **External Links** section, select **Regulatory services – Configuration**. Then follow the instructions to provision an RCS environment.
4. In the **Related links** section, select **Electronic reporting parameters**.
5. On the **Electronic reporting parameters** page, select the **RCS** tab.
6. Use the URLs on this tab to access the RCS environment has been provisioned for your company.
7. Close the **Electronic reporting parameters** page.

### Register a new ER repository

1. On the **Localization configurations** page, select the **Litware, Inc.** configuration provider in the list.
2. Select **Repositories**.
3. Select **Add** to open the drop-down dialog box.
4. Select **RCS** as the configuration repository type, and then select **Create repository**.
6. In the **RCS environment display name** field, select the desired RCS instance. Note that you can have several instances.
7. Select **OK**.

### Import ER configurations from an RCS-based repository

1. On the **Configuration repositories** page, select the **Show filters** button on the left side of the window.
2. For the **Name** filter, select **begins with** as the filter operator, and then enter **RCS** as the filter value.
3. Select the repository, and open it.
3. On the **Connect to Regulatory Configuration Services** page, select the **Click here to connect to Regulatory Configuration Services** link.
4. Select **Open**.
5. Select **Close**.
6. Select the desired version of the ER configuration, and then select **Import** to import that version.

## Additional resource

- [Electronic reporting (ER) overview](general-electronic-reporting.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
