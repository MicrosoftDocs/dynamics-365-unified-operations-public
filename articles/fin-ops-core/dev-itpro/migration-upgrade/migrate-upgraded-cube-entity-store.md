---
title: Migrate upgraded AX 2012 R3 sales cubes to the entity store
description: Learn about how to migrate an upgraded Microsoft Dynamics AX 2012 R3 cube schema to the entity store in a finance and operations application. 
author: MilindaV2
ms.author: johnmichalak
ms.topic: upgrade-and-migration-article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form:
ms.dyn365.ops.version: Platform update 1
ms.assetid: e992cdd8-abe8-42d0-97ad-6165822abbba
---

# Migrate upgraded AX 2012 R3 sales cubes to the entity store

[!include [banner](../includes/banner.md)]

In this tutorial, you migrate an upgraded Microsoft Dynamics AX 2012 R3 cube schema to the entity store in a finance and operations application. You use the sales cube that was included in Dynamics AX 2012 R3 as an example.

The entity store supports near real-time Microsoft Power BI integration scenarios, as shown in the following diagram. For an overview of Power BI integration with entity store, see [Power BI integration with entity store](/archive/blogs/dynamicsaxbi/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update). :::image type="content" source="./media/powerbiarchitecture.png" alt-text="Screenshot of Power BI Architecture diagram.":::

## New Power BI features included in the May 2016 and November 2016 updates

This tutorial requires the Dynamics 365 for Operations May 2016 update or later. You use the following new capabilities in this tutorial:

- Stage an aggregate measurement in the entity store and refresh the data from Dynamics AX. You might prefer this option over in-memory real time aggregate measurements when:
  - You upgrade a Dynamics AX 2012 cube.
  - Your aggregate measurements are large.
  - Data freshness (latency) from a few minutes up to a few hours is acceptable for reporting.
- Use the batch framework to schedule a recurring refresh. For this release, only a full refresh is enabled.
- Create reports using Power BI desktop in a developer/test environment.
- Use the direct query option when creating Power BI content. For example, you can create larger models without relying on OData as the data refresh mechanism.
- Migrate reports from your development environment to a production environment using Lifecycle Services.
- As a partner or an ISV you can distribute Power BI content as part of a Lifecycle Services solution to your customers.
- **If you're using the November update (platform release 1611)** or later, some steps in this document are part of the process to refresh the entity store - you don't need to perform them manually.

## Change upgraded aggregate measurement properties

As part of the code upgrade process, you can migrate analysis services projects from the Application Object Tree (AOT) in Dynamics AX 2012 to the new aggregate measurements metadata format.

1. Launch Visual Studio and create a new project in Application Suite.

    > [!NOTE]
    > You can create a model and include the customized aggregate measurement within that model. For more information, see [Customize through extension and overlayering](../extensibility/customization-overlayering-extensions.md).

1. Open Application Explorer. Go to **Analytics** &gt; **Perspectives** &gt; **Aggregate measurements**. You see a set of aggregate measurements that were upgraded from Dynamics AX 2012 R3, and the measurements that ship in the current version.
1. Select **SalesCube**. Right-click and select **Duplicate in project**.
1. The project now includes an aggregate measurement named **SalesCubeCopy**.
1. Rename this measurement. Select **SalesCubeCopy** in Solution Explorer. Right-click and select **Rename**. Enter **SalesCubeV2** as the new name.
1. Double-click **SalesCubeV2** to launch the Aggregate measurement designer. Notice the structure of the aggregate measurement that was migrated from Dynamics AX 2012.
1. The sales cube in Dynamics AX 2012 encompassed a broad subject area related to Sales. In this case, create a smaller, more focused Power BI model using the metadata that you upgraded. Expand the **Sales Order Lines** measure group and review the list of measures and dimension references.

    > [!NOTE]
    > By using the modeling capabilities, you can quickly make a few enhancements to this model. Suggestions for improvements:
    >
    > - Replace views and tables that you used to model the measure group (and dimensions) with an entity. You can model an entity by using the underlying view and replace the view with the corresponding entity. By using an entity, you can take advantage of upcoming features such as incremental refresh and security.
    > - Remove unwanted dimension references by adding the corresponding field to the attributes node. For example, you can remove the Sizes dimension reference because the **Size** field in the measure group is sufficiently descriptive. This change improves the runtime performance of queries and refreshes times.

1. Select the **SalesCubeV2** root node in the Aggregate measurement designer. Right-click and select **Properties**.
1. During upgrade, the process sets the legacy property flag, **SSASCube**, for aggregate measurements. You need to change this property to one of two supported usage types. Previously, **InMemoryRealTime** was supported as usage for aggregate measurements. **StagedEntityStore** is supported as a new usage type.

    > [!NOTE]
    > Modify the usage property to **InMemoryRealTime** if you plan to use the Aggregate measurement for embedded BI scenarios and Power BI integration. If you're using the Aggregate measurement only for Power BI or Cortana Intelligence Suite integration, select **StagedEntityStore**.

1. Save the project. Right-click the project in Solution Explorer and select **Rebuild**.
1. After the rebuild operation finishes, save the project, and then close Visual Studio. This step completes the development work. You'll author reports as a report developer or a power user.

## Refresh the entity store

As an administrator, you can configure the refresh of the aggregate measurement by using the client.

1. Launch the Dynamics AX client and go to **System Administration** &gt; **Setup** &gt; **Entity Store**. The **Entity Store** form shows a list of aggregate measurements that you can deploy to the entity store.
1. Notice that **sales cube** (which you upgraded from Dynamics AX 2012) isn't available for deployment to the entity store. **SalesCubeV2**, which you created in the previous step, can be deployed to the entity store.
1. Select **SalesCubeV2** from the list, and select the **Refresh** button. The **Refresh** dialog box appears. Expand the **Run in the background** tab.
1. Enter a descriptive name in the **Task description** field. Optionally, you can select the **Recurrence** tab and create a recurring schedule instead of a one-time refresh. Select **OK**.
1. The system creates a batch job to refresh the aggregate measurement in the entity store.

## Authoring a report on Sales by State with Power BI desktop

This step requires that you install the Power BI desktop tool. You can download it from [Microsoft Power BI Desktop](https://www.microsoft.com/download/details.aspx?id=45331).

1. Launch Power BI desktop. You might need to apply updates. A welcome page appears. Select **Get data**.
1. Alternatively, when Power BI desktop launches, on the **Home** tab select **Get Data** &gt; **SQL Server**.
1. In the **SQL Server Database** dialog box, enter the server name and the name of the entity store database. If you deployed a developer environment, you can enter "." as the server name and **AxDW** as the database name. If you're working in a test environment, you need to get these parameters from your system administrator.
1. Select the **DirectQuery** option. In this exercise, you create Power BI reports that execute directly on the entity store. If you had used the **Import** option, Power BI would cache data from the entity store, and you would need to periodically refresh the Power BI model. **Import mode isn't currently supported with reports written by using entity store**. Select **OK**.
1. Next, you see the **Navigator** dialog box. Navigator enables you to select tables and views from the entity store that you want to report on. Enter **Sales** in the search box. The system filters entities that are related to the **SalesCubeV2** aggregate measurement that you previously created.

    > [!NOTE]
    > The entity store stages the aggregate measurements that you create. While entities within each aggregate measurement are prefixed and stored as individual tables, Power BI desktop enables you to combine data from multiple aggregate measurements.

1. You create a report that shows sales by state. Select **SalesCubeV2\_Customer** and **SalesCubeV2\_CustomerInvoices** from Navigator and select **Load**.
1. You notice Power BI designer with **Fields** present in the entities that you chose (on the far right), and available visualization.

### Create a surrogate key that links customers and invoices (applies to Platform versions before November 2016 update)

> [!NOTE]
> The process of creating surrogate keys happens in aggregate measurements staged into the entity store. Power BI Desktop doesn't enable you to relate table joins using multiple fields (also known as, composite keys). The **SalesCubeV2\_Customer** entity doesn't have a surrogate key (such as AX RecID) defined in it. In the next steps, you create a surrogate key that enables relating a customer entity to invoices.

1. Select the ellipsis (...) icon next to the **SalesCubeV2\_CustomerInvoices** entity. Right-click and select **New Column**.
1. Enter the following expression in the **Formula editor** window.

    ```xpp
    FKCustomer = CONCATENATE(CONCATENATE(SalesCubeV2_CustomerInvoices[DATAAREAID], "-"), SalesCubeV2_CustomerInvoices[ORDERACCOUNT])
    ```

    > [!NOTE]
    > When you enter the first few letters of the field name or function, the editor displays a list of candidate fields. This feature is called type-ahead. You can either copy and paste this expression or use the type-ahead feature.

1. When completed, your formula should look similar to the following.

    :::image type="content" source="./media/powerbiformula.png" alt-text="Screenshot of Power BI Formula.":::

1. A new field, **FKCustomer**, appears in the list of fields for the **SalesCubeV2\_CustomerInvoices** table. Because this field relates two tables, you can hide it from end users by right-clicking the field and selecting the **Hide** option.
1. Next, create a similar field in the **SalesCubeV2\_Customer** table. Select the ellipsis (...) icon next to **SalesCubeV2\_Customer** entity. Right-click and select **New Column**.
1. Enter the following expression in the **Formula editor** window.

    ```xpp
    FKCustomer = CONCATENATE(CONCATENATE(SalesCubeV2_Customer[DATAAREAID], "-"), SalesCubeV2_Customer[CUSTOMER])
    ```

1. The field **FKCustomer** appears in the list of fields for the **SalesCubeV2\_Customer** table. Because this field relates two tables, you can hide it from end users by right-clicking the field and selecting the **Hide** option.

### Relate invoices and customers

> [!NOTE]
> You can relate the surrogate keys already created within entity store. If not, relate the surrogate keys that you created manually. Next, create a relationship between **SalesCubeV2\_CustomerInvoices** and **SalesCubeV2\_Customers** entities.

1. Select the **Manage Relationships** button on the Power BI ribbon. You see the **Manage Relationships** dialog box. Select the **New** button.
1. In the **Create Relationship** dialog box, select **SalesCubeV2CustomerInvoices** as the first table in the drop-down list. Scroll to select the **FKCustomer** field as the column to relate to.
1. In the second drop-down list, select **SalesCubeV2Customer** as the table. Scroll to select **FKCustomer** as the column to relate to.
1. Select the **Make this relationship active** option if it isn't already selected. Select **OK** to continue.
1. You notice the newly created relationship in the **Manage Relationships** dialog box. Select the **Close** button.

### Create a Sales by state report

1. To create a report that shows sales by customer group, drag the **CustomerInvoiceAmountAccountingCurrency** field from the **SalesCubeV2\_CustomerIncoices** table and drop it on the Power BI desktop canvas. Next, drag the **CustomerGroupName** field in the **SalesCubeV2\_Customer** table to the same grid.
1. Change the chart type to a doughnut chart. You should see a report similar to the following.

    :::image type="content" source="./media/doughnut-chart.png" alt-text="Screenshot of Power BI Doughnut Chart.":::

1. You can create more visuals by using the Power BI desktop. When you save, you notice that the file has a **PBIX** extension.
1. Save the report to your desktop.
1. At this point, the report is fully functional (with data from your environment) and you can continue to use the Power BI desktop or upload this report to PowerBI.com and continue with data exploration.
1. Next, migrate this report to a production environment by using Lifecycle Services so that you can see this report with production data and share it with other users.

## Publish the report and the model

Publishing a report and model requires uploading the report to Lifecycle Services, migrating the aggregate measurement to your production environment, configuring the client to point to the correct Lifecycle Services library, and publishing your reports in your production environment.

### Upload the report to Lifecycle Services

Microsoft Dynamics Lifecycle Services is the tool used to migrate development artifacts from developer to production environments. In the May 2016 update, Lifecycle Services supports migrating PBIX files (authored by using the entity store) between environments.

1. Open [Lifecycle Services](https://lcs.dynamics.com/) from the developer environment. If you didn't create a project in the Lifecycle Services environment, create a project.
1. Scroll to the right and you see the **Asset Library** icon. Select the icon to open the **Asset Library**.

The asset library enables adding **PowerBI report models** (PBIX files) as implementation artifacts to a project.

1. Select the plus (+) icon to add a new asset.
1. Enter a name and a description. Select **Upload** and then locate the file that you saved in an earlier step.
1. After you successfully upload the file, select **Confirm**. The file is uploaded into Lifecycle Services as an implementation asset. Lifecycle Services supports managing versions and releases for Power BI reports. You can maintain several versions and publish reports to other environments, just as you would for other implementation artifacts. Because you added the PBIX files as an asset within a Lifecycle Services project, environments that you deployed by using that project have access to this report.
1. Optionally, you can publish this report so that all of your projects can access the shared assets. If you're a partner or an ISV, and want to share this report with your customers, share this asset to your global library and enable your customers to import the asset into their respective Lifecycle Services projects. To do this, select the **Save to my library** option.

### Migrate the aggregate measurement to a production environment

1. Migrate the aggregate measurement that you modified in the developer environment to the production environment. Follow the instructions in [Create deployable packages of models](../deployment/create-apply-deployable-package.md).
1. After you successfully publish the model, perform the steps outlined in the **Refresh the entity store** section of this tutorial, so that the entity store is updated with data.

### Configure a Lifecycle Services project

If you didn't already do so, associate your environment with a Lifecycle Services project so that finance and operations apps can consume assets within the project.

1. Launch the client from the instance that you want to use to deploy the Power BI reports. Typically, this instance is the test or a production instance where you want to see a report with a different set of data than what you worked with as a report developer.
1. Open **System Administration** &gt; **Setup** &gt; **System parameters**. Select the **Help** tab. By using the **Lifecycle services help configuration** list box, select the Lifecycle Services project that you uploaded the PBIX file to. Select **Save**.

    > [!NOTE]
    > This form only shows the Lifecycle Services projects that the current user has access to. If an administrator performs this step, the administrator needs access to the project, or the PBIX artifacts need to be imported into a project that the administrator has access to.

### Publish Power BI reports to a production environment

1. Open **System Administration** &gt; **Setup** &gt; **Deploy PowerBI** from the client. You see the file that you uploaded to Lifecycle Services.
1. Select the **Sales Report** file and select the **Deploy Power BI files** option on the menu bar.

    > [!NOTE]
    > You might be asked to consent publishing to the PowerBI.com service. Select the link to provide consent. When consent is complete, go back to the original browser window and select the **Close** button.

1. After you successfully publish the file, the Power BI report appears in your PowerBI.com subscription. The report now points to the entity store in the production environment.

## Continuing with PowerBI.com

As an administrator or a power user, you successfully authored and published a Power BI report to the production environment by using the entity store. You can perform several more steps by using Power BI functionality.

- Optionally, apply record-level security to the dataset to restrict users from seeing data they aren't allowed to view in Power BI.
- Create an organizational content pack and share it among users in a group.
  - You can export datasets, reports, and dashboards from your PowerBI.com instance as a new content pack to a selected group of users.
  - Organizational content packs adhere to any record-level security rules that you defined at the dataset level.
- Users can personalize their workspaces by adding Power BI tiles or reports.

## Additional resources

[Model aggregate data](../analytics/model-aggregate-data.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
