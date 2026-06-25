---
title: Install business performance planning visuals
description: Learn how to install business performance planning visuals, including prerequisites and a step-by-step process for connecting your data.
author: ShielaSogge
ms.author: romainpham
ms.topic: install-set-up-deploy
ms.date: 06/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Install business performance planning visuals

This article describes how to install business performance planning visuals. To fully use the Business performance planning application, you must also install Microsoft Power BI visuals. For more information about how to install Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

## Prerequisites for the installation of Power BI visuals

1. A Dynamics 365 Finance or Business performance planning environment with Dataverse enabled.
1. Import business performance planning visuals from [Microsoft Marketplace](https://marketplace.microsoft.com). For more information, see [Import visuals](/power-bi/developer/visuals/import-visual).
1. Connect Power BI to your Dataverse environment. For more information, see [Use direct query in Power BI Desktop](/power-bi/connect-data/desktop-use-directquery).
1. To work with the visuals and publish to a Power BI workspace, you need a Power BI license. For more information, see [Licenses and subscriptions for business users](/power-bi/consumer/end-user-license).
1. You must enable authentication for Power BI for the visuals to work. For more information, see [Obtain Microsoft Entra access token](/fabric/admin/organizational-visuals#obtain-microsoft-entra-access-token).
1. When you connect to a cube in Power BI, select SQL Server as the data source.

    > [!NOTE]
    > You must enable the Marketplace Custom Visuals single sign-on (SSO) feature in step 4. If this feature isn't enabled, you receive an **Unable to authenticate to Dataverse service** error.
    > Use the SQL Server connector to ensure the write-back works properly. The Dataverse connector isn't supported for write-back as it doesn't expose the logical names required by Business performance planning.

### Install visuals from Microsoft Marketplace

To install visuals from Microsoft Marketplace, follow these steps:

1. Open Power BI, and select the workspace or report where you want to configure the visual.
1. In the Visualizations pane, select the ellipsis (⋯) > **Get more visuals**.
1. Search for **Business performance planning**.
1. Select the visuals you want to add, such as:

- Matrix planning
- Graphical planning
- Reporting
- Table edit
- Variance
- Copy
- Comments

1. Select **Add**. The visuals appear in the Power BI Visualizations pane.

>[!TIP]
> Always install visuals directly from Microsoft Marketplace to ensure you're using the latest certified version with SSO and write-back support.

## Connect Power BI to your Dataverse data

When you connect to the data in Power BI, select SQL Server as the data source. This selection enables DirectQuery access through the TDS endpoint for real-time write-back.

To select SQL Server as a data source, follow these steps:

1. In Power BI, go to **Get data**, or select **SQL Server** on the ribbon.
1. Enter your server name in the format `orgname.crm.dynamics.com`.

- Don't include `https://`, `www`, or a trailing `/`.
- Example: contoso.crm.dynamics.com
- Don't use <https://www.contoso.crm.dynamics.com/>
- Leave the database name blank (optional).

3. After you select SQL Server as the data source, set the data connectivity mode to **Direct query**.
2. If you're prompted to sign in, on the **Microsoft account** tab, select **Sign in**.
3. At the top of the **Navigator** page, search for your cube.

    > [!NOTE]
    > The names of planning cube tables have the "msdyn\_xpnacube" prefix, and the names of planning dimension tables have the "msdyn\_xpnadim" prefix. If you're unsure of the name of your cube, go to **Business performance planning**, and select the cube to add.

4. After you select the cube, enable the **Load selected tables** option to automatically select any dimension tables that are used in the cube.
1. Review the list of tables to import.

- Power BI might also select system tables such as async operation, process session, or system user.
- These tables aren’t required for planning and should be unticked before loading.
- To confirm what you import, select **Display options** > **Only selected items** in the **Navigator** panel.

8. Select **Load**. This operation might take a few minutes. After it's completed, your data appears in the **Data** view in Power BI.

>[!NOTE]
> If you're unsure of your cube name, go to **Business performance planning** in Dynamics 365 Finance, select the cube, and copy the write-back table name from the cube properties.

### Recommendations for transform data

- The names of planning cube tables have the "msdyn\_xpnacube" prefix, and the names of planning dimension tables have the "msdyn\_xpnadim" prefix. Use these prefixes to search for the cube or dimensions when you connect via SQL Server and Direct Query.
- After you select the cube on the **Navigator** page, select **Select related tables** to automatically load data relationships between the cube and the dimension into Power BI.

- After the data loads, select **Transform data** in Power BI to review and optimize your model.

- Import only the columns you need - To improve performance and simplify modeling, import only the columns that you use for your drivers and relationships.
        - From the cube table (msdyn_xpnacube_) - Keep only driver columns following the pattern: msdyn_\<drivername>\. For example, msdyn_Amount, msdyn_Quantity.
        - Keep only the dimension link columns used to relate the cube to each dimension: msdyn_xpnadim_\<dimensionname>\. For example: msdyn_xpnadim_Accountname, msdyn_xpnadim_CostCentername.
        - Don't select columns named msdyn_xpnadim_\<dimensionname>\ without the name suffix — these are internal Dataverse ID columns, not the values stored in your dimension table.
        - From each dimension table (msdyn_xpnadim_*) - Keep the following key columns: - msdyn_name: the primary ID of the dimension, used to link to the cube table.
        - Additional descriptive columns following the pattern msdyn_\<dimensionname>\ (for example, msdyn_AccountCategory, msdyn_CostCenterGroup).

- Validate relationships
Ensure Power BI automatically creates relationships between: - msdyn_xpnadim_\<dimensionname>\name (in the cube table), and - msdyn_name (in the corresponding dimension table).
If not, create these relationships manually in **Model** view.

- Performance tip
Reducing unused columns and removing unnecessary system tables significantly improves model performance, especially in DirectQuery mode, and ensures faster refreshes and write-back operations.

### Configure the visual

To configure the Business performance planning visual, follow these steps:

1. Drag a Business performance planning visual (for example, Matrix planning) onto your report canvas.
1. Select the visual and open the **Format visual** pane.
1. Expand the **API details** section and enter:

- **API base URL** - The environment URL where Business performance planning is installed.
- Example: <https://contoso.crm.dynamics.com>
- **Cube name** - The name of your planning cube (optional if preconfigured).

1. **Save** and refresh the report. When configured correctly, the visual connects automatically and displays your cube data.

> [!NOTE]
> The **Format visual** pane appears only when a Business performance planning visual is selected on the report canvas.

### Recommendations

- Always use DirectQuery for real-time write-back and allocation.
- When connecting to a cube, use **Select related tables** to load all dimension relationships and unselect unnecessary system tables.
- Enable the Marketplace Custom Visuals SSO feature to prevent authentication errors.
- Use table prefixes for easier identification:
msdyn_xpnacube_ for cube tables
msdyn_xpnadim_ for dimension tables

### Troubleshooting Dataverse and Power BI connection issues

When you connect Power BI to Dataverse or configure the Business performance planning visuals, you might encounter common connectivity or authentication issues.

- Incorrect server address when using the SQL Server connector: Entering the server name with https://, www, or a trailing / causes a connection failure.
Example error:
Microsoft SQL: A network-related or instance-specific error occurred while establishing a connection to SQL Server.
The server wasn't found or wasn't accessible (provider: Named Pipes Provider, error: 40 – Couldn't open a connection to SQL Server).

Resolution: - Enter only orgname.crm.dynamics.com.

- Remove https://, www, and /.
- Verify that the TDS endpoint is enabled for your environment.

- Expired Power BI authentication token: If the visuals load but the **Edit** button is disabled or greyed out, your authentication token might have expired.

Error message: User doesn't have permission to edit data.
Resolution:

1. Refresh your Power BI session or sign out and back in.
1. Close and reopen the report in Power BI Desktop.
1. If the issue persists: Recreate the visual from scratch, or temporarily switch the visual to a native Power BI Matrix, copy it, then switch the copy back to a Matrix planning visual.
This process resets cached metadata and authentication bindings.

- Incorrect API URL or cube name: If data loads but write-back or edit functions fail, verify the API URL and Cube name in the visual’s advanced settings.
Resolution: - Confirm the API base URL matches your environment (for example, <https://contoso.crm.dynamics.com/api/data/v9.2/>).
- Verify the cube name matches exactly (case-sensitive).
- If the issue persists, recreate the visual or use the switch–copy–restore method described earlier.

- Network or firewall restrictions: If connection attempts consistently fail: - Ensure outbound TCP traffic to ports 1433 and 5558 is allowed.
- Confirm that your network or VPN allows access to:
        - *.crm.dynamics.com
        -*.powerbi.com - In Power BI, verify that the dataset gateway allows DirectQuery connections.

> [!TIP]
> Most setup issues are resolved by validating three key settings:
>
> 1. Server name syntax (no www or /)
> 1. Active Power BI token (reauthenticate if expired)
> 1. Correct API URL and cube name in the visual configuration
