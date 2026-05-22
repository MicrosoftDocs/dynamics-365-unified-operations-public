---
title: Import a configuration from Lifecycle Services
description: This article describes how to import a new version of an Electronic reporting (ER) configuration from Microsoft Dynamics Lifecycle Services.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionRepositoryTable, ERSolutionImport
---

# Import a configuration from Lifecycle Services

[!include [banner](../../includes/banner.md)]

This article explains how a user in the System administrator or Electronic reporting developer role can import a new version of an [Electronic reporting (ER) configuration](../general-electronic-reporting.md#Configuration) from the [project-level Asset library](../../lifecycle-services/asset-library.md) in Microsoft Dynamics Lifecycle Services.

> [!IMPORTANT]
> The use of Lifecycle Services as a storage repository for ER configurations is being [deprecated](../../../../finance/get-started/removed-deprecated-features-finance.md#features-removed-or-deprecated-in-the-finance-10017-release). For more information, see [Regulatory Configuration Service (RCS) – Lifecycle Services storage deprecation](../../../../finance/localizations/rcs-lcs-repo-dep-faq.md).

In this example, you select the desired version of the ER configuration and import it for a sample company named Litware, Inc. You can complete these steps in any company, because ER configurations are shared among companies. To complete these steps, you must first complete the steps in [Upload a configuration into Lifecycle Services](er-upload-configuration-into-lifecycle-services.md). You also need access to Lifecycle Services.

1. Sign in to the application by using one of the following roles:

    - Electronic reporting developer
    - System administrator

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
1. Select **Configurations**.

<a name="accessconditions"></a>
> [!NOTE]
> Make sure that the current Dynamics 365 Finance user is a member of the Lifecycle Services project that contains the Asset library that you want to [access](../../lifecycle-services/asset-library.md#asset-library-support) to import ER configurations.
>
> You can't access an Lifecycle Services project from an ER repository that represents a different domain than the domain that is used in Finance. If you try, an empty list of Lifecycle Services projects is shown, and you can't import ER configurations from the project-level Asset library in Lifecycle Services. To access project-level Asset libraries from an ER repository that is used to import ER configurations, sign in to Finance by using the credentials of a user who belongs to the tenant (domain) that the current Finance instance is provisioned for.

## Delete a shared version of a data model configuration

1. On **Configurations**, in the configurations tree, select **Sample model configuration**.

    You created the first version of a sample data model configuration and published it to Lifecycle Services when you completed the steps in [Upload a configuration into Lifecycle Services](er-upload-configuration-into-lifecycle-services.md). In this procedure, you delete that version of the ER configuration. You can import that version from Lifecycle Services later in this article.

1. In the list, find and select the desired record.

    For this example, select the version of the configuration that has a status of **Shared**. This status indicates that the configuration is published to Lifecycle Services.

1. Select **Change status**.
1. Select **Discontinue**.

    When you change the status of the selected version from **Shared** to **Discontinued**, you make the version available for deletion.

1. Select **OK**.
1. In the list, find and select the desired record.

    For this example, select the version of the configuration that has a status of **Discontinued**.

1. Select **Delete**.
1. Select **Yes**.

    The only draft version 2 of the selected data model configuration is now available.

1. Close the page.

## Import a shared version of a data model configuration from Lifecycle Services

1. Go to **Organization administration \> Workspaces \> Electronic reporting**.

1. In the **Configuration providers** section, select the **Litware, Inc.** tile.

1. On the **Litware, Inc.** tile, select **Repositories**.

    You can now open the list of repositories for the Litware, Inc. configuration provider.

1. Select **Open**.

    For this example, select the **Lifecycle Services** repository, and open it. You must have [access](#accessconditions) to the Lifecycle Services project and to the Asset library that the selected ER repository accesses.

1. In the list, select the row.

    For this example, select the first version of **Sample model configuration** in the version list.

1. Select **Import**.
1. Select **Yes** to confirm the import of the selected version from Lifecycle Services.

    An informational message confirms that the selected version was successfully imported.

1. Close the page.
1. Close the page.
1. Select **Configurations**.
1. In the tree, select **Sample model configuration**.
1. In the list, find and select the desired record.

    For this example, select the version of the configuration that has a status of **Shared**.

    Notice that shared version 1 of the selected data model configuration is also available now.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
