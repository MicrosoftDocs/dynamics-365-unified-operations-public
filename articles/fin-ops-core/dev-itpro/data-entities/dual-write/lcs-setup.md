---
title: Dual-write setup from Lifecycle Services
description: Learn how to set up a dual-write connection from Microsoft Dynamics 365 Lifecycle Services, including prerequisites and the setup process.
author: laneswenka
ms.author: laswenka
ms.topic: how-to
ms.date: 02/23/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application User, IT Pro
ms.search.region: global
ms.search.validFrom: 2020-01-06
---


# Dual-write setup from Lifecycle Services

[!include [banner](../../includes/banner.md)]



This article explains how to enable dual-write from Microsoft Dynamics 365 Lifecycle Services.

## Prerequisites

Customers must complete the Power Platform integration as described in the following topics:

- If you don't yet use Microsoft Power Platform and want to expand your finance and operations environments by adding platform capabilities, see [Connect finance and operations apps with a new Microsoft Dataverse instance](../../power-platform/environment-lifecycle-connect-finops-new-dv.md).
- If you already have Dataverse and Power Platform environments, and want to connect them to finance and operations environments, see [Connect finance and operations apps with an existing Microsoft Dataverse instance](../../power-platform/environment-lifecycle-connect-finops-existing-dv.md).

## Set up dual-write for new or existing Dataverse environments

Follow these steps to set up dual-write from Lifecycle Services **Environment Details** page:

1. On the **Environment Details** page, expand the **Power Platform Integration** section.

2. Select the **Dual-write application** button.

    ![Power Platform Integration.](media/powerplat_integration_step2.png)

3. Review the terms and conditions, and then select **Configure**.

4. Select **OK** to continue.

5. You can monitor the progress by periodically refreshing the environment details page. Setup typically takes 30 minutes or less.  

6. When the setup is complete, a message informs you if the process was successful or if there was a failure. If the setup failed, then a related error message is displayed. You must fix any errors before moving to the next step.

7. Select **Link to Power Platform environment** to create a link between Dataverse and the current environment's databases. It typically takes less than 5 minutes to create the link.

    :::image type="content" source="media/powerplat_integration_step3.png" alt-text="Link to Power Platform environment.":::

8. When the linking is complete, a hyperlink is displayed. Use the link to sign in to the dual-write administration area in the finance and operations environment. From there, you can set up entity mappings.

## Configure app user for one-box environments
Certificates in your Microsoft Entra tenant are no longer installed in new one-box development environments by default. To enable dual-write on a one-box environment, you must grant the application user configured for the environment with a role and permissions for dual-write. To configure these permissions:
1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
2. Select your environment where you're configuring dual-write, and select **Settings** on the environment details page.
3. On the **Users + permissions** list, select **Application users**.
4. Select the **New app user** action.
5. On the **Create a new app user** pane:
   - Select the **Add an app** action, and select the new application previously registered for your environment following the [Set up a new application and certification registration](../../dev-tools/secure-developer-vm.md#set-up-a-new-application-and-certificate-registration).
   - In the **Business unit** drop-down list, select the root business unit for the environment.
   - In the **Security roles** text box, select a security role with create, read, update, and delete permissions on Dataverse tables used for dual-write, such as the **System Administrator** role.
   - Select **Create**.
6. Enable the "DualWriteUnoAuthenticationFnoToCds" flight:
   - Open SQL Server Management Studio and connect to the "AXDB" on your one-box environment.
   - Run the following SQL script to enable the "DualWriteUnoAuthenticationFnoToCds" flight:

    ```sql
    DECLARE @flightName NVARCHAR(100) = 'DualWriteUnoAuthenticationFnoToCds';
    IF NOT EXISTS (SELECT TOP 1 1 FROM SysFlighting WHERE flightName = @flightName)
    INSERT INTO SYSFLIGHTING(FLIGHTNAME, ENABLED, FLIGHTSERVICEID, PARTITION)
    SELECT @flightName, 1, 12719367, RECID FROM DBO.[PARTITIONS];
    ELSE
    UPDATE SysFlighting SET enabled = 1, flightServiceId = 12719367 WHERE flightName = @flightName;
    ```

    - Restart the Application Object Server (AOS) service.

> [!NOTE]
> If permissions for the application user are not configured for your one-box environment, you may receive the following error message during dual-write sync operations:
> "0x80072560 response message: The user is not a member of the organization".

## Troubleshooting

### Linking mismatch

It's possible that your dual-write environment is linked to a Dataverse instance while Lifecycle Services isn't set up for Power Platform integration. This linking mismatch can cause unexpected behavior. It's recommended that Lifecycle Services environment details match what you are connected to in dual-write so the same connection can be used by business events, virtual tables, and add-ins.

If your environment has a linking mismatch, Lifecycle Services shows a warning on your environment details page that resembles the following example: "Microsoft has detected that your environment is linked via Dual-write to a different destination than specified in Power Platform Integration, which isn't recommended."

:::image type="content" source="media/powerplat_integration_mismatchLink.png" alt-text="Power Platform integration link mismatched.":::

If you receive this warning, try one of the following solutions:

- If your Lifecycle Services environment hasn't ever been set up for Power Platform integration, you can connect to the Dataverse instance that is configured in dual-write by following the instructions in this article.
- If your Lifecycle Services environment is already set up for Power Platform integration, you should reset your dual-write connection to the one specified by Lifecycle Services using the [Reset dual-write connections](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/reset).

In the past a manual support ticket option was available, but that was before option 1 above existed. Microsoft no longer supports manual relinking requests via Support tickets.

### Incorrect permissions on service principal

It's possible to receive the following error while linking the finance and operations environment to the Dataverse environment in Lifecycle Services:

| Error code | Error message |
| --- | --- |
| DW9003 | Failed to connect to CRM. Ensure that the service principal has the correct permissions to access CRM.|
| DW9003 | Failed to connect to AX. Ensure that the service principal has the correct permissions to access AX. | 

This error indicates that the application users created for dual-write to access data on the target platforms haven't been configured with the appropriate permissions. To resolve this error, ensure the application users are configured correctly following the guidance in [System requirements and prerequisites](./requirements-and-prerequisites.md).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

