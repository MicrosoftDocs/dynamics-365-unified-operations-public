---
# required metadata

title: Prepare application-specific metadata for RCS and ER
description: This topic explains how to prepare application-specific metadata for Regulatory configuration service (RCS) and Electronic reporting (ER).
author: NickSelin
ms.date: 04/04/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERWorkspace
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Prepare application-specific metadata for RCS and ER

[!include[banner](../includes/banner.md)]

This topic walks you through examples of the following tasks:

- [Prepare application metadata that can be used in RCS](#prepare-application-metadata-that-can-be-used-in-rcs)
- [Access application metadata by using an ER configuration](#access-application-metadata-by-using-an-er-configuration)
- [Access application metadata by using connected applications](#access-application-metadata-by-using-connected-applications)

## Prepare application metadata that can be used in RCS

The following procedure shows how a user who has the **System Administrator** or **Electronic Reporting Developer** role can create an Electronic reporting (ER) configuration that contains metadata for the application, and that is used to design ER model mapping configurations in Regulatory configuration service (RCS). The sample ER model mapping configuration that is created in this example will be used to access foreign trade transactions.

For this example, you want to use RCS to design an ER solution for the application that will be used to generate electronic documents that contain information from the foreign trade business domain. To specify the mapping between the ER data model and the sources of required data, you must have access to application metadata in RCS. Therefore, as part of the process of designing the ER solution, you must configure a new ER metadata configuration that contains all the metadata that is currently required in order to generate ER reports for the selected business domain.

> [!NOTE]
> In this example, you will create a configuration for the sample company, Litware, Inc. These steps can be performed in any company.

1. Go to **Organization administration \> Workspaces \> Electronic reporting**.
2. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md) procedure. 
3. Select **Metadata configurations**.
4. Select **Create configuration**.
5. In the drop-down dialog box, in the **Name** field, enter a name. For this example, enter **Foreign trade metadata**.
6. Select **Create configuration**.
7. Select **Designer**.
8. Select **Add**.

    > [!NOTE]
    > You can select all metadata either for the whole application, or for selected models or modules. In both cases, be aware that the following metadata will be automatically added: tables of records, enumerations, and extended data types (EDTs). When additional types of metadata are required, they must be manually added.

    You must add some metadata that is related to foreign trade transactions and manually select metadata items.

9. Select **Add data source \> Table records**.
10. Filter on a value of **Intrastat** in the **Name** field.
11. Select the **Intrastat** table record.
12. Select **OK**.

    You must add metadata information about the Intrastat table of records.

13. In the tree, select **Table records Intrastat \> \>Relations \> IntrastatCommodity (Table records EcoResCategory)**.
14. Select **Add metadata**.

    > [!NOTE]
    > Metadata about required relations for the selected table of records must be added manually.

15. Select **Add data source**.
16. Select **Enumeration**.
17. Filter on a value of **IntrastatDirection** in the **Name** field.
18. Select the **IntrastatDirection** enumeration record.
19. Select **OK**.
20. Select **Save**.
21. Close the page.
22. Complete the draft version of the metadata configuration:

    1. Select **Change status \> Complete**.
    2. Select **OK**.
    3. Select the completed version 1.

23. Export the completed version of the metadata configuration from the application as an XML file:

    1. Select **Exchange \> Export as XML file**.
    2. Select **OK**.

The ER metadata configuration that you created is saved as the **Foreign trade metadata.xml** file. You can now import it into RCS, so that it can be used as the source of metadata for the foreign trade business domain. Based on this information, you can specify the mapping between application metadata and the ER data model.

## Access application metadata by using an ER configuration

The following procedure shows how an RCS user who has the **System Administrator** or **Electronic Reporting Developer** role can design a new ER model mapping by using metadata from the application. Application metadata will be accessed by using an ER metadata configuration that contains a sample set of metadata to access foreign trade transactions.

Before you can complete this procedure, you must first complete the following procedures:

- [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md)
- [Prepare application metadata that can be used in RCS](#prepare-application-metadata-that-can-be-used-in-rcs)

1. Go to **All workspaces \> Electronic reporting**.
2. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md) procedure. 
3. Import the ER metadata configuration that contains metadata for the application, and that is configured to generate electronic documents for the foreign trade business domain. You created this ER metadata configuration and exported it as an XML file in the [Prepare application metadata that can be used in RCS](#prepare-application-metadata-that-can-be-used-in-rcs) procedure earlier in this topic.

    1. Select **Metadata configurations**.
    2. Select **Exchange**.
    3. Select **Load from XML file**.
    4. Browse to select the **Foreign trade metadata.xml** file.
    5. Select **OK**.
    6. Close the page.

4. Create a data model configuration:

    1. Select **Reporting configurations**.
    2. Select **Create configuration**.
    3. In the drop-down dialog box, in the **Name** field, enter **Foreign trade model**.
    4. Select **Create configuration**.
    5. Select **Designer**.
    6. Select **New** to open the drop dialog.

        1. In the **Name** field, type **Root**.
        2. Select **Add**.
    
    7. Select **New** to open the drop dialog.

        1. In the **Name** field, type **Transaction**.
        2. In the **Item type** field, select **Record list**.
        3. Select **Add**.
 
    8. Select **New** to open the drop dialog.

        1. In the **Name** field, type **Commodity code**.
        2. In the **Item type** field, select **String**.
        3. Select **Add**.

    9. Select **New** to open the drop dialog.

        1. In the Name field, type **Invoiced amount**.
        2. In the **Item type** field, select **Real**.
        3. Select **Add**.

    10. Select **New** to open the drop dialog.

        1. In the **Name** field, type **Date**.
        2. In the **Item type** field, select **Date**.
        3. Select **Add**.
 
    11. Select **Add \> Root reference**.
    12. Select **OK**.
    13. Select **Save**.
    14. Close the page.
    15. Select **Change status \> Complete**.
    16. Select **OK**.

5. Create a model mapping configuration:

    1. Select **Create configuration**.
    2. In the drop-down dialog box, in the **New** field, enter **Model Mapping based on data model Foreign trade model**.
    3. In the **Name** field, enter **Foreign trade mapping**.
    4. Select **Create configuration**.
    5. On the **Prerequisites** FastTab, select **Edit**.
    6. Select **New**.
    7. In the **Prerequisite component type** field, select **Configuration**.
    8. Select the **Foreign trade metadata** configuration.
    9. Select **Save**. Notice that the reference is added to version 1 of the **Foreign trade metadata** configuration. Application metadata from this configuration will be offered while the model mapping is designed.
    10. Close the page.
    11. Select **Designer**.
    12. Select **Designer**.
    13. In the tree, select **Dynamics 365 for Operations \> Table records**.
    14. Select **Add root**.
    15. In the **Name** field, enter **Intrastat**.
    16. Select **Intrastat** table records.
    17. Select **OK**.

        > [!NOTE]
        > Only two tables are offered, because only two tables were added to the set of metadata that is currently used.

    18. Select **Bind**.
    19. In the tree, select **Intrastat \> AmountMST**.
    20. In the tree, select **Transaction = Intrastat \> Invoiced amount**.
    21. Select **Bind**.
    22. In the tree, select **Intrastat \> TransDate**.
    23. In the tree, select **Transaction = Intrastat \> Date**.
    24. Select **Bind**.
    25. In the tree, select **Intrastat \> \>Relations \> IntrastatCommodity \> Code**.
    26. In the tree, select **Transaction = Intrastat \> Commodity code**.
    27. Select **Bind**.
    28. Select **Validate**.

        > [!NOTE]
        > After validation is completed, you've successfully bound elements of the data model to items of the data sources that are described by using details of the application metadata from the referenced ER metadata configuration.

    29. Select **Save**.

As you require, you can extend the existing set of metadata in the application. You can then export the new completed version of the ER metadata configuration, import it into RCS, and update the prerequisites of the configured model mapping configuration to refer to a new version of the imported metadata configuration.

> [!NOTE]
> This method for getting information about application metadata is the only available method for applications that are locally deployed (that is, when a local business data \[LBD\], or on-premises, deployment model is used for the application).

## Access application metadata by using connected applications

The following procedure shows how an RCS user who has the **System Administrator** or **Electronic Reporting Developer** role can design a new ER model mapping by using metadata of the application. Application metadata will be accessed online by using RCS connected application. A sample ER model mapping will be configured to access foreign trade transactions.

To complete this procedure, you must first complete the [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md) procedure in RCS. If you haven't yet completed the [Access application metadata by using an ER configuration](#access-application-metadata-by-using-an-er-configuration) procedure earlier in this topic, go to [Electronic Reporting Task Guides for Dynamics 365 for Finance and Operations 8.1](https://go.microsoft.com/fwlink/?linkid=2082739) page to download the following ER configuration files in advance and save them locally: **Foreign trade metadata.xml**, **Foreign trade model.xml**, and **Foreign trade mapping.xml**.


### Get required ER configurations

If you've already completed the [Access application metadata by using an ER configuration](#access-application-metadata-by-using-an-er-configuration) procedure earlier in this topic, you already have all the required ER configurations (the foreign trade metadata, model, and mapping configurations) in the current RCS instance. In that case, you can skip this procedure.

1. Go to **All workspaces \> Electronic reporting**.
2. Select **Reporting configurations**.
3. Load the **Foreign trade metadata.xml**, **Foreign trade model.xml**, and **Foreign trade mapping.xml** configuration files repeating the following chain of steps for each of them:

    1. Select **Exchange**.
    2. Select **Load from XML file**.
    3. Select **Browse**, and select a file.
    4. Select **OK**.

### Register the connection with the application

1. Go to **All workspaces \> Electronic reporting**.
2. Select **Connected applications**.
3. Make sure that the configured application is based on Microsoft Azure, and that it is accessible in general to RCS users. The current RCS user must have access to the configured application being registered as a user of this application in a role that gives them privileges to access the application's metadata.
4. Select **New**.
5. In the **Name** field, enter **MyConnectedApp** as the name of the connected application.
6. In the **Application** field, specify the URL of the application.
7. In the **Tenant** field, specify the provider of the application.
8. Select **Save**. 
9. When you check the connection to the configured application, on the **Connect to remote application** page, select the **Select here to connect to selected remote application** link. 
10. Select **Check connection** to validate access to the configured application.
11. Select **Close**.

After you complete this procedure and validation of the connection succeeds, the version and tenant details for the configured application will be updated in the current grid.

### Review the existing model mapping configuration

1. Go to **All workspaces \> Electronic reporting**.
2. Select **Reporting configurations**.
3. In the tree, select **Foreign trade model \> Foreign trade mapping**.
4. Select the **Prerequisites** FasTab.

    > [!NOTE]
    > Currently, this mapping refers to the metadata configuration. Application metadata from this configuration will be offered while this model mapping is designed.

4. Select **Designer**.
5. Select **Designer**.
6. In the tree, select **Dynamics 365 for Operations \> Table records**.
7. Select **Add root**.
8. In the **Table** field, enter or select a value.

    > [!NOTE]
    > Currently, this mapping refers to the metadata configuration. Application metadata from this configuration will be offered while this model mapping is designed.

9. Select **Cancel**.

### Assign the connected application to a model mapping

1. Select **Edit**.
2. In the **Connected application field**, select the **MyConnectedApp** application.

    > [!NOTE]
    > This mapping refers to the metadata of the selected connected application. If a mapping refers to the metadata configuration and the connected application at the same time, the metadata of the connected application will be used.

3. Select **Designer**.
4. Select **Designer**.
5. In the tree, select **Dynamics 365 for Operations \> Table records**.
6. Select **Add root**.
7. In the **Table** field, enter or select a value.

    > [!NOTE]
    > At this point, more than two application tables are offered, because this mapping uses all the metadata of the connected application that has been assigned to it.

8. Select **Cancel**.
9. Select **Validate**.

You've now bound elements of the data model to items of the data sources that are described by using details of the metadata of the connected application that has been assigned to this mapping.

When you must evaluate this model mapping by using the metadata of a different version of the application, register another connected application, assign it to this model mapping, and validate it against the new metadata.

## Additional resources

Alternatively, you can play the **Prepare application metadata that can be used in RCS** task guide in the application as as well as the **Access application metadata by using an ER configuration** and **Access application metadata by using connected applications** task guides in RCS. These task guides can be downloaded from the [Electronic Reporting Task Guides for Dynamics 365 for Finance and Operations 8.1](https://go.microsoft.com/fwlink/?linkid=2082739) page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]