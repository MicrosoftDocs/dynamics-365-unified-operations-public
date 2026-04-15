---
title: Upload a configuration into Lifecycle Services
description: This article explains how to create a new Electronic reporting (ER) configuration and upload it into Microsoft Dynamics Lifecycle Services.
author: kfend
ms.date: 04/09/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, ERDataModelDesigner, ERDataModelContentsItemCreationDialog, ERSolutionRepositoryTable, ERSolutionRepositoryCreateDropDialog, ERSolutionImport
---

# Upload a configuration into Lifecycle Services

[!include [banner](../../includes/banner.md)]

This article explains how a user in the System administrator or Electronic reporting developer role can create a new [Electronic reporting (ER) configuration](../general-electronic-reporting.md#Configuration) and upload it into the [project-level Asset library](../../lifecycle-services/asset-library.md) in Microsoft Dynamics Lifecycle Services.

> [!IMPORTANT]
> The use of Lifecycle Services as a storage repository for ER configurations is being [deprecated](../../../../finance/get-started/removed-deprecated-features-finance.md#features-removed-or-deprecated-in-the-finance-10017-release). For more information, see [Regulatory Configuration Service (RCS) – Lifecycle Services storage deprecation](../../../../finance/localizations/rcs-lcs-repo-dep-faq.md).

In this example, you create a configuration and upload it into Lifecycle Services for a sample company named Litware, Inc. You can complete these steps in any company, because ER configurations are shared among companies. To complete these steps, you must first complete the steps in [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). You also need access to Lifecycle Services.

1. Sign in to the application by using one of the following roles:

    - Electronic reporting developer
    - System administrator

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
1. Select **Litware, Inc.**, and mark it as **Active**.
1. Select **Configurations**.

<a name="accessconditions"></a>
> [!NOTE]
> Make sure that the current Dynamics 365 Finance user is a member of the Lifecycle Services project that contains the [Asset library](../../lifecycle-services/asset-library.md#asset-library-support) that is used to import ER configurations.
>
> You can't access an Lifecycle Services project from an ER repository that represents a different domain than the domain that is used in Finance. If you try, an empty list of Lifecycle Services projects is shown, and you can't import ER configurations from the project-level Asset library in Lifecycle Services. To access project-level Asset libraries from an ER repository that is used to import ER configurations, sign in to Finance by using the credentials of a user who belongs to the tenant (domain) that the current Finance instance is provisioned for.

## Create a new data model configuration

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. On **Configurations**, select **Create configuration** to open the drop-down dialog box.

    In this example, you create a configuration that contains a sample data model for electronic documents. You upload this data model configuration into Lifecycle Services later.

1. In the **Name** field, enter **Sample model configuration**.
1. In the **Description** field, enter **Sample model configuration**.
1. Select **Create configuration**.
1. Select **Model designer**.
1. Select **New**.
1. In the **Name** field, enter **Entry point**.
1. Select **Add**.
1. Select **Save**.
1. Close the page.
1. Select **Change status**.
1. Select **Complete**.
1. Select **OK**.
1. Close the page.

## Register a new repository

1. Go to **Organization administration \> Workspaces \> Electronic reporting**.

1. In the **Configuration providers** section, select the **Litware, Inc.** tile.

1. On the **Litware, Inc.** tile, select **Repositories**.

    You can now open the list of repositories for the Litware, Inc. configuration provider.

1. Select **Add** to open the drop-down dialog box.

    You can now add a new repository.

1. In the **Configuration repository enter** field, select **LCS**.
1. Select **Create repository**.
1. In the **Project** field, enter or select a value.

    For this example, select the desired Lifecycle Services project. You must have [access](#accessconditions) to the project.

1. Select **OK**.

    Complete a new repository entry.

1. In the list, mark the selected row.

    For this example, select the **LCS** repository record.

    Note that the current provider marks a registered repository. In other words, only configurations that the provider owns can go in this repository and be uploaded into the selected Lifecycle Services project.

1. Select **Open**.

    You open the repository to view the list of ER configurations. If the selected project isn't yet used for ER configurations sharing, the list is empty.

1. Close the page.
1. Close the page.

## Upload a configuration into Lifecycle Services

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. On **Configurations**, in the configurations tree, select **Sample model configuration**.

    Select a configuration that you created and completed.

1. In the list, find and select the desired record.

    For this example, select the version of the selected configuration that has a status of **Completed**.

1. Select **Change status**.
1. Select **Share**.

    When you publish the configuration in Lifecycle Services, the status changes from **Completed** to **Shared**.

1. Select **OK**.
1. In the list, find and select the desired record.

    For this example, select the configuration version that has a status of **Shared**.

    The status of the selected version changes from **Completed** to **Shared**.

1. Close the page.
1. Select **Repositories**.

    You can now open the list of repositories for the Litware, Inc. configuration provider.

1. Select **Open**.

    For this example, select the **LCS** repository, and open it.

    The selected configuration appears as an asset of the selected Lifecycle Services project.

1. Open Lifecycle Services by going to <https://lcs.dynamics.com>.
1. Open a project that you used earlier for repository registration.
1. Open the Asset library of the project.
1. Select the **GER configuration** asset type.

    The ER configuration that you uploaded appears in the list.

    If providers have access to this Lifecycle Services project, they can import the uploaded Lifecycle Services configuration into another instance.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
