---
title: Import a configuration from Lifecycle Services
description: This article describes how to import a new version of an Electronic reporting (ER) configuration from Microsoft Dynamics Lifecycle Services (LCS).
author: kfend
ms.date: 06/17/2021
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionRepositoryTable, ERSolutionImport
---

# Import a configuration from Lifecycle Services

[!include [banner](../../includes/banner.md)]

This article explains how a user in the System administrator or Electronic reporting developer role can import a new version of an [Electronic reporting (ER) configuration](../general-electronic-reporting.md#Configuration) from the [project-level Asset library](../../lifecycle-services/asset-library.md) in Microsoft Dynamics Lifecycle Services (LCS).

> [!IMPORTANT]
> The use of LCS as a storage repository for ER configurations is being [deprecated](../../../../finance/get-started/removed-deprecated-features-finance.md#features-removed-or-deprecated-in-the-finance-10017-release). For more information, see [Regulatory Configuration Service (RCS) – Lifecycle Services (LCS) storage deprecation](../../../../finance/localizations/rcs-lcs-repo-dep-faq.md).

In this example, you will select the desired version of the ER configuration and import it for a sample company that is named Litware, Inc. These steps can be completed in any company, because ER configurations are shared among companies. To complete these steps, you must first complete the steps in [Upload a configuration into Lifecycle Services](er-upload-configuration-into-lifecycle-services.md). Access to LCS is also required.

1. Sign in to the application by using one of the following roles:

    - Electronic reporting developer
    - System administrator

2. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
3. Select **Configurations**.

<a name="accessconditions"></a>
> [!NOTE]
> Make sure that the current Dynamics 365 Finance user is a member of the LCS project that contains the Asset library that the user wants to [access](../../lifecycle-services/asset-library.md#asset-library-support) to import ER configurations.
>
> You can't access an LCS project from an ER repository that represents a different domain than the domain that is used in Finance. If you try, an empty list of LCS projects will be shown, and you won't be able to import ER configurations from the project-level Asset library in LCS. To access project-level Asset libraries from an ER repository that is used to import ER configurations, sign in to Finance by using the credentials of a user who belongs to the tenant (domain) that the current Finance instance has been provisioned for.

## Delete a shared version of a data model configuration

1. On the **Configurations** page, in the configurations tree, select **Sample model configuration**.

    You created the first version of a sample data model configuration and published it to LCS when you completed the steps in [Upload a configuration into Lifecycle Services](er-upload-configuration-into-lifecycle-services.md). In this procedure, you will delete that version of the ER configuration. You will then import that version from LCS later in this article.

2. In the list, find and select the desired record.

    For this example, select the version of the configuration that has a status of **Shared**. This status indicates that the configuration has been published to LCS.

3. Select **Change status**.
4. Select **Discontinue**.

    By changing the status of the selected version from **Shared** to **Discontinued**, you make the version available for deletion.

5. Select **OK**.
6. In the list, find and select the desired record.

    For this example, select the version of the configuration that has a status of **Discontinued**.

7. Select **Delete**.
8. Select **Yes**.

    Notice that the only draft version 2 of the selected data model configuration is now available.

9. Close the page.

## Import a shared version of a data model configuration from LCS

1. Go to **Organization administration \> Workspaces \> Electronic reporting**.

2. In the **Configuration providers** section, select the **Litware, Inc.** tile.

3. On the **Litware, Inc.** tile, select **Repositories**.

    You can now open the list of repositories for the Litware, Inc. configuration provider.

4. Select **Open**.

    For this example, select the **LCS** repository, and open it. You must have [access](#accessconditions) to the LCS project and to the Asset library that is accessed by the selected ER repository.

5. In the list, mark the selected row.

    For this example, select the first version of **Sample model configuration** in the version list.

6. Select **Import**.
7. Select **Yes** to confirm the import of the selected version from LCS.

    An informational message confirms that the selected version was successfully imported.

8. Close the page.
9. Close the page.
10. Select **Configurations**.
11. In the tree, select **Sample model configuration**.
12. In the list, find and select the desired record.

    For this example, select the version of the configuration that has a status of **Shared**.

    Notice that shared version 1 of the selected data model configuration is also available now.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
