---
title: Initialize company data
description: This topic explains how to initialize data with company information before you enable a dual-write connection.
author: RamaKrishnamoorthy 
ms.date: 12/01/2020
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2020-12-01
ms.dyn365.ops.version: AX 7.0.0
---

# Initialize company data

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]



If you have an existing Microsoft Dataverse instance or Finance and Operations app instance that has business data, you might want to enable a dual-write connection against it. In this case, you must initialize the Dataverse data or Finance and Operations app data with company information before you enable dual-write. This initialization process is sometimes referred to as *bootstrapping*.

This topic includes sample scenarios that explain how to use [Azure Data Factory](/azure/data-factory/introduction) to initialize data in Dataverse tables for dual-write. It doesn't cover all tables, error handling scenarios, or lookups. Use this topic and template as a reference to set up your own Azure Data Factory pipeline to import data into Dataverse or update data in Dataverse.

## High-level scenario

Consider the **Customers** table in a Finance and Operations app, and the **Account** table in Dataverse.

- Use initial write to copy reference and dependent tables, such as **Company**, **Customer groups**, and **Terms of payment**, from the Finance and Operations app to Dataverse.
- Use the Data management framework to export data from the Finance and Operations app in comma-separated values (CSV) format. For example, set up an export project in Data management to export customers from each company by using the **DataAreaId** field in the Finance and Operations app. This process is a one-time manual process.
- Use Azure Blob Storage to store the CSV files for lookup and transformation. Upload the CSV file for your Finance and Operations customers into Azure Blob Storage.
- Use Azure Data Factory to initialize data in Dataverse.

The following illustration shows the workflow.

:::image type="content" source="media/boot-process-flow.png" alt-text="High-level flow.":::

This scenario is based on the following assumptions:

- The source data is in the Finance and Operations app.
- If an account exists in Dataverse, but it doesn't exist in the Finance and Operations app, it won't be initialized as part of this flow. Use DIXF or [initial sync](initial-sync-guidance.md) functionality based on the amount of data stored in Dataverse.
- All account records in the customer engagement apps have a natural key (account number) that matches the Finance and Operations natural key (**CustomerAccount**). 
- Rows have a one-to-one (1:1) mapping across the apps.

> [!NOTE]
> In both Finance and Operations apps and Dataverse, When a customer record is created, Party record gets created implicitly. 

## Prerequisites

- **Azure subscription** – You have **contributor access** to an existing Azure subscription. If you don't have an Azure subscription, create a [free Azure account](https://azure.microsoft.com/free/) before you begin.
- **Azure storage account** – You have an Azure storage account. If you don't have a storage account, follow the steps in [Create an Azure storage account](/azure/storage/common/storage-account-create?tabs=azure-portal#create-a-storage-account) to create one.
- **Azure data factory** – Create an Azure Data Factory resource by following the steps in [Create a data factory](/azure/data-factory/tutorial-copy-data-portal#create-a-data-factory).
- **Finance and Operations app** – Use the Data management framework to export the data in CSV format. For more information, see [Data management overview](../data-entities-data-packages.md). In this template, customers are exported by using the **CustCustomerV3Entity** table.
- **Dynamics 365 Dataverse** – Use the credentials for the Dataverse admin user to initialize the data.
- **Dual-write** – Dual-write solutions are installed, and reference data is copied by using initial write.

## Deployment steps

### Set up an Azure storage account

If you don't have an Azure storage account, follow these steps in [Create an Azure storage account](/azure/storage/common/storage-account-create?tabs=azure-portal#create-a-storage-account) to create one. In your storage account, create one container that is named **ce-data**. This container will store all data files. You can change the container in your datasets and pipelines as you require. Go to **Access keys**, and copy the **Connection string** value, as shown in the following illustration. This value is required when you import the Azure Data Factory template.

:::image type="content" source="media/boot-storage-account.png" alt-text="Setting up access keys.":::

### Deploy an Azure Data Factory template

1. Make a note of the name of the Azure data factory that you created.
2. Make a note of the connection string for the Azure storage account.
3. Make a note of the service URI of the Dataverse instance, and the admin user name and password.

    The following table shows the parameters that are required.

    | Parameter name | Description | Example value |
    |---|---|---|
    | Factory name | The name of your data factory | *BootstrapDataverseDataADF* |
    | Bootstrap blob storage account Linked Service\_connection String | The connection string for blob storage | The value that you copied when you created the storage account |
    | Bootstrap Dynamics 365 Linked Service\_service Uri | The URI of the Dataverse instance | `https://contosod365.crm4.dynamics.com` |
    | Bootstrap Dynamics 365 Linked Service\_properties\_type Properties\_username | The Dynamics 365 admin user's user ID | `<adminservice@contoso.onmicrosoft.com>` |
    | Bootstrap Dynamics 365 Linked Service\_password | The Dynamics 365 admin user's password | _\*\*\*\*\*\*\*\*_ | 

4. Download the [Azure Resource Manager (ARM) template file](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/blob/master/Dual-write/Bootstrapping/arm_template.json) to your local directory.
5. In the Azure portal, go to [Custom deployment](https://ms.portal.azure.com/#create/Microsoft.Template).
6. Select **Build your own template in the editor**.
7. Select **Load file**, and find and select the ARM template file that you downloaded earlier. Then select **Save**.
8. Provide the required parameters, select **Review**, and then select **Create**.

    :::image type="content" source="media/boot-custom-deployment.png" alt-text="Customizing a template.":::

9. After deployment, you will see **Pipelines**, **Datasets**, and **Data flows** sections in the list pane.

    :::image type="content" source="media/boot-pipeline.png" alt-text="Pipelines, Datasets, and Data flows":::

## Run the process

1. In the Finance and Operations app, use the Data management framework to export data in CSV format. For more information, see [Data management overview](../data-entities-data-packages.md). In this template, customer data was exported from the **CustCustomerV3Entity** table. Set up **CustCustomerV3Entity**, and remove the **FullPrimaryAddress** field map from the mapping. Add the **DataAreaId** field to the CSV file. Rename the exported file **01-CustomersV3Export-Customers V3.csv**, and upload it to the Azure storage account that you named **ce-data**.

    :::image type="content" source="media/boot-customer-file.png" alt-text="Finance and Operations customer file.":::

2. Download the [sample customer file](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/blob/master/Dual-write/Bootstrapping/01-CustomersV3Export-Customers%20V3.csv).

3. Run **BootstrapAccountsPipeline** from Azure Data Factory.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
