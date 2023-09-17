---
title: Upload a configuration into Lifecycle Services
description: This article explains how to create a new Electronic reporting (ER) configuration and upload it into Microsoft Dynamics Lifecycle Services (LCS).
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
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, ERDataModelDesigner, ERDataModelContentsItemCreationDialog, ERSolutionRepositoryTable, ERSolutionRepositoryCreateDropDialog, ERSolutionImport
---
# Upload a configuration into Lifecycle Services

[!include [banner](../../includes/banner.md)]

This article explains how a user in the System administrator or Electronic reporting developer role can create a new [Electronic reporting (ER) configuration](../general-electronic-reporting.md#Configuration) and upload it into the [project-level Asset library](../../lifecycle-services/asset-library.md) in Microsoft Dynamics Lifecycle Services (LCS).

> [!IMPORTANT]
> The use of LCS as a storage repository for ER configurations is being [deprecated](../../../../finance/get-started/removed-deprecated-features-finance.md#features-removed-or-deprecated-in-the-finance-10017-release). For more information, see [Regulatory Configuration Service (RCS) – Lifecycle Services (LCS) storage deprecation](../../../../finance/localizations/rcs-lcs-repo-dep-faq.md).

In this example, you will create a configuration and upload it into LCS for a sample company that is named Litware, Inc. These steps can be completed in any company, because ER configurations are shared among companies. To complete these steps, you must first complete the steps in [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). Access to LCS is also required.

1. Sign in to the application by using one of the following roles:

    - Electronic reporting developer
    - System administrator

2. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
3. Select **Litware, Inc.**, and mark it as **Active**.
4. Select **Configurations**.

<a name="accessconditions"></a>
> [!NOTE]
> Make sure that the current Dynamics 365 Finance user is a member of the LCS project that contains the [Asset library](../../lifecycle-services/asset-library.md#asset-library-support) that is used to import ER configurations.
>
> You can't access an LCS project from an ER repository that represents a different domain than the domain that is used in Finance. If you try, an empty list of LCS projects will be shown, and you won't be able to import ER configurations from the project-level Asset library in LCS. To access project-level Asset libraries from an ER repository that is used to import ER configurations, sign in to Finance by using the credentials of a user who belongs to the tenant (domain) that the current Finance instance has been provisioned for.

## Create a new data model configuration

1. Go to **Organization administration \> Electronic reporting \> Configurations**.
2. On the **Configurations** page, select **Create configuration** to open the drop-down dialog box.

    In this example, you will create a configuration that contains a sample data model for electronic documents. This data model configuration will be uploaded into LCS later.

3. In the **Name** field, enter **Sample model configuration**.
4. In the **Description** field, enter **Sample model configuration**.
5. Select **Create configuration**.
6. Select **Model designer**.
7. Select **New**.
8. In the **Name** field, enter **Entry point**.
9. Select **Add**.
10. Select **Save**.
11. Close the page.
12. Select **Change status**.
13. Select **Complete**.
14. Select **OK**.
15. Close the page.

## Register a new repository

1. Go to **Organization administration \> Workspaces \> Electronic reporting**.

2. In the **Configuration providers** section, select the **Litware, Inc.** tile.

3. On the **Litware, Inc.** tile, select **Repositories**.

    You can now open the list of repositories for the Litware, Inc. configuration provider.

4. Select **Add** to open the drop-down dialog box.

    You can now add a new repository.

5. In the **Configuration repository enter** field, select **LCS**.
6. Select **Create repository**.
7. In the **Project** field, enter or select a value.

    For this example, select the desired LCS project. You must have [access](#accessconditions) to the project.

8. Select **OK**.

    Complete a new repository entry.

9. In the list, mark the selected row.

    For this example, select the **LCS** repository record.

    Note that a registered repository is marked by the current provider. In other words, only configurations that are owned by that provider can be put in this repository and therefore uploaded into the selected LCS project.

10. Select **Open**.

    You open the repository to view the list of ER configurations. If the selected project hasn't yet been used for ER configurations sharing, the list will be empty.

11. Close the page.
12. Close the page.

## Upload a configuration into LCS

1. Go to **Organization administration \> Electronic reporting \> Configurations**.
2. On the **Configurations** page, in the configurations tree, select **Sample model configuration**.

    You must select a created configuration that has been already completed.

3. In the list, find and select the desired record.

    For this example, select the version of the selected configuration that has a status of **Completed**.

4. Select **Change status**.
5. Select **Share**.

    The status of the configuration is changed from **Completed** to **Shared** when the configuration is published in LCS.

6. Select **OK**.
7. In the list, find and select the desired record.

    For this example, select the configuration version that has a status of **Shared**.

    Note that the status of the selected version was changed from **Completed** to **Shared**.

8. Close the page.
9. Select **Repositories**.

    You can now open the list of repositories for the Litware, Inc. configuration provider.

10. Select **Open**.

    For this example, select the **LCS** repository, and open it.

    Notice that the selected configuration is shown as an asset of the selected LCS project.

11. Open LCS by going to <https://lcs.dynamics.com>.
12. Open a project that was used earlier for repository registration.
13. Open the Asset library of the project.
14. Select the **GER configuration** asset type.

    The ER configuration that you uploaded should be listed.

    Note that the uploaded LCS configuration can be imported into another instance if providers have access to this LCS project.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
