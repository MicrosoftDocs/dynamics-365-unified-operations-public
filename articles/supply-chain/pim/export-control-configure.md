---
title: Enable and configure advanced export management
description: Learn how to enable and configure advanced export management in Microsoft Dynamics 365 Supply Chain Management, including prerequisites.
author: sgmsft
ms.author: shwgarg
ms.topic: how-to
ms.date: 02/15/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: COOExportControlParameters
---

# Enable and configure advanced export management

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

## Prerequisites

Before you can use advanced export management, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.36 or later.
- The feature that's named *Advanced export management configuration* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- Your Supply Chain Management environment must be [linked to a Dataverse environment](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md).

## Install the export control app

Follow these steps to install the export control app.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. Go to **Environments**, and select your environment.
1. On the page for the selected environment, in the **Resources** section, select **Dynamics 365 apps**.
1. In the list of apps, select **Dynamics 365 Export Control**.
1. Follow the on-screen instructions to install the app.

## Authentication and authorization

To perform export control checks, the system uses application user calls. Therefore, the checks can be performed regardless of which user is working with the document in Supply Chain Management. Supply Chain Management users don't have to be added to Dataverse, and they don't have to be given extra permissions. To support the service-to-service (S2S) authentication, a Microsoft Entra application must be created for each environment. You must not share or reuse the Microsoft Entra applications across environments.

### Register a new Microsoft Entra application in the Azure portal

Follow these steps to create a new Microsoft Entra application.

1. Sign in to the [Azure portal](https://portal.azure.com).
1. Go to **Microsoft Entra ID\> App registrations**.
1. Select **New registration**.
1. On the **Register an application** page, enter the following information:

    - **Name** – Enter a unique name.
    - **Supported account types** – Select *Any Microsoft Entra directory* (single or multi-tenant).
    - **Redirect URI** – Leave the field blank.

1. Select **Register**.
1. The page that appears shows details about the new app. Copy the **Application (client) ID** value to a temporary text file, because you'll need it later.
1. In the **Manage** list, select **Certificates & secrets**.
1. On the **Certificates & secrets** page, select **New client secret**.
1. In the **Add a client secret** dialog box, enter a description and an expiration date, and then select **Add**.
1. You're returned to the **Certificates & secrets** page, which now includes a row that contains details about your new client secret. Copy the value in the **Value** column to a temporary text file, because you'll need it later, and it will be hidden the next time that you open this page.

### Grant the application permissions in Power Platform admin center

Follow these steps to grant the application permissions in Power Platform admin center.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. Go to **Environments**, and select your environment.
1. On the page for the selected environment, in the **Access** section, under **Users**, select **See all**.
1. On the **Users** page, select the **app users list** link.
1. On the **Application users** page, on the toolbar, select **New app user**.
1. In the **Create a new app user** dialog box, select **Add an app**.
1. In the **Add an app from Microsoft Entra** dialog box, in the search field, paste the application (client) ID of your new app. (You should have copied this ID when you registered the app in the Azure portal.) Then select your app in the list or results, and select **Add**.
1. You're returned to the **Create a new app user** dialog box. Select your business unit, and then select **Edit security roles**.
1. In the **Add security roles** dialog box, in the **Role** list, select *Export control application*. Then select **Save** to apply the role.
1. Select **Create** to create the new app user.

## Enable the functionality and configure the application in Supply Chain Management

Follow these steps to enable the functionality and configure the application in Supply Chain Management.

1. Sign in to Supply Chain Management.
1. Go to **Product information management \> Setup \> Product compliance \> Country of Origin \> Advanced export management configuration**.
1. On the **General** tab, review and set the following fields:
    - **Linked Dataverse environment URL** – This read-only field shows the URL of the Dataverse environment that's linked to your Supply Chain Management environment. Your advanced export management jurisdictions, codes, restrictions, exceptions, and licenses are defined in this Dataverse environment.
    - **Application ID** – Paste the application (client) ID of your new app. (You should have copied this ID when you registered the app in the Azure portal.)
    - **Application secret** – Paste the client secret of your new app. (You should have copied this secret when you registered the app in the Azure portal.)

    As you enter values into these fields, the system checks whether it can use them to connect to Dataverse and whether the required solution is installed there. The three checkboxes under the **Status** heading will automatically update to show a checkmark as each test passes. If one or more tests fail, make sure that the advanced export management solution is successfully installed, and that the specified Microsoft Entra application has the *Export control application* security role in Dataverse. When all three boxes show a check, continue to the next step.

1. The following settings appear after all of the tests have passed. Set each option as required.
    - **Advanced export management functionality enabled** – Set this option to *Yes* to turn on advanced export management functionality in your system.
    - **Validate data in Dataverse** – Set this option to *Yes* to ensure that the system checks all sales orders and shipments against the export rules that are defined in the Dataverse app. The check confirms whether your company is allowed to sell or ship each item on an order, according to the rules that are established for the relevant jurisdiction.
    - **Track sales order check history** – Set this option to *Yes* to keep a log of the order check history. Set it to *No* if you don't need this log.

1. Select **Synchronize country/region list** to copy the existing list of country/region codes from Supply Chain Management to the Dataverse solution. This list is used when rules are defined. Each time that you change the country/region code list, you must return to the **Advanced export management configuration** page and select **Synchronize country/region list** again to sync the changes. The language of the user who selects this button is used to sync the names of the countries/regions.

## Configure jurisdictions for each legal entity

You must configure the set of jurisdictions that are available for each legal entity (company). For companies where no jurisdictions are enabled, advanced export management features aren't available on sales orders, items, or products. Instead, simpler [dual-use goods](dual-use.md) functionality is provided. If at least one jurisdiction is enabled for a legal entity, the dual-use goods functionality is hidden on pages in that legal entity, and advanced export management functionality is shown instead.

Follow these steps to configure the jurisdictions for a legal entity.

1. Sign in to Supply Chain Management.
1. Use the company picker to select the legal entity that you want to configure.
1. Go to **Product information management \> Setup \> Product compliance \> Country of Origin \> Advanced export management configuration**.
1. On the **Jurisdictions in use in this company** tab, the grid shows the jurisdictions that are enabled for the current legal entity. Initially, the grid is blank. Use the buttons on the toolbar to add or remove jurisdictions as you require.

    [<img src="media/export-control-jurisdictions-in-use.png" alt="Jurisdictions in use." title="Jurisdictions in use" width="720" />](media/export-control-jurisdictions-in-use.png#lightbox)

1. For each jurisdiction, choose whether that jurisdiction is active and choose whether to skip sales order and/or sales quotation checks for that jurisdiction.

1. On the Action Pane, select **Save**.
