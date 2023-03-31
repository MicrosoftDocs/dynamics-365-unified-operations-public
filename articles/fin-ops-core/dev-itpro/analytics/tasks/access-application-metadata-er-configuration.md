---
title: Access application metadata by using ER configuration
description: The article describes how a Regulatory configuration service user can design a new Electronic reporting model mapping by using the metadata.
author: kfend
ms.date: 06/28/2019
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2019-06-28
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
---
# Access application metadata by using ER configuration

[!include [banner](../../includes/banner.md)]

The following steps explain how a Regulatory configuration service (RCS) user in the System Administrator or Electronic Reporting Developer role can design a new Electronic reporting (ER) model mapping by using the application metadata. Application metadata will be accessed by using an ER metadata configuration that contains a sample set of metadata to access foreign trade transactions. To complete these steps, in RCS you must first complete the steps in the article, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md) procedure. Then complete the steps in the article, [Prepare application metadata to be used in RCS](prepare-application-metadata-rcs.md).

## Prerequisites
1. Go to **All workspaces** > **Electronic reporting**. 
2. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). 

## Import metadata configuration 
1. Click **Metadata configurations**. 
2. Import the ER metadata configuration that contains metadata that has been configured to generate electronic documents for foreign trade business. This ER metadata configuration has been exported as XML file while the steps in the [Prepare application metadata to be used in RCS](prepare-application-metadata-rcs.md) procedure have been completed. 
3. Click **Exchange**. 
4. Click **Load from XML file**. 
5. Click **Browse** and select the 'Foreign trade metadata.xml' file. 
6. Click **OK**. 
7. Close the page. 

## Create data model configuration
1. Click **Reporting configurations**. 
2. Click **Create configuration** to open the drop dialog. 
3. In the **Name** field, type 'Foreign trade model'. 
4. Click **Create configuration**. 
5. Click **Designer**. 
6. Click **New** to open the drop dialog. 
7. In the **Name** field, type 'Root'. 
8. Click **Add**. 
9. Click **New** to open the drop dialog. 
10.    In the **Name** field, type 'Transaction'. 
11.    In the **Item type** field, select **Record list**. 
12.    Click **Add**. 
13.    Click **New** to open the drop dialog. 
14.    In the **Name** field, type 'Commodity code'. 
15.    In the **Item type** field, select **String**. 
16.    Click **Add**. 
17.    Click **New** to open the drop dialog. 
18.    In the **Name** field, type 'Invoiced amount'. 
19.    In the **Item type** field, select **Real**. 
20.    Click **Add**. 
21.    Click **New** to open the drop dialog. 
22.    In the **Name** field, type 'Date'. 
23.    In the **Item type** field, select **Date**. 
24.    Click **Add**. 
25.    Click **Root reference**. 
26.    Click **OK**. 
27.    Click **Save**. 
28.    Close the page. 
29.    Click **Change status**. 
30.    Click **Complete**. 
31.    Click **OK**. 

## Create model mapping configuration 
1. Click **Create configuration** to open the drop dialog. 
2. In the **New** field, enter 'Model Mapping based on data model Foreign trade model'. 
3. In the **Name** field, type 'Foreign trade mapping'. 
4. Click **Create configuration**. 
5. Expand the **Prerequisites** section. 
6. Click **Edit**. 
7. Click **New**. 
8. In the list, mark the selected row. 
9. In the **Prerequisite component type** field, select **Configuration**. 
10.    Select **Foreign trade metadata** configuration. 
11.    Click **Save**. 
12.    We added the reference to the version 1 of the 'Foreign trade metadata' configuration. Application metadata from this configuration will be offered while this model mapping will be designed. 
13.    Close the page. 
14.    Click **Designer**. 
15.    Click **Designer**. 
16.    In the tree, select **Dynamics 365 for Operations\Table records**. 
17.    Click **Add root**. 
18.    In the **Name** field, type 'Intrastat'. 
19.    Select **Intrastat** table records. 
20.    Click **OK**. 

> [!NOTE]
> The only 2 tables were offered as the only 2 tables were added into the set of metadata which is currently in use. 

21.    Click **Bind**. 
22.    In the tree, expand **Intrastat**. 
23.    In the tree, select **Intrastat\AmountMST**. 
24.    In the tree, expand **Transaction = Intrastat**. 
25.    In the tree, select **Transaction = Intrastat\Invoiced amount**. 
26.    Click **Bind**. 
27.    In the tree, select **Intrastat\TransDate**. 
28.    In the tree, select **Transaction = Intrastat\Date**. 
29.    Click **Bind**. 
30.    In the tree, expand **Intrastat\>Relations**. 
31.    In the tree, expand **Intrastat\>Relations\IntrastatCommodity**. 
32.    In the tree, select **Intrastat\>Relations\IntrastatCommodity\Code**. 
33.    In the tree, select **Transaction = Intrastat\Commodity code**. 
34.    Click **Bind**. 
35.    Click **Validate**. 

> [!NOTE]
> We have successfully bound elements of data model with items of data sources that are described by using details of application metadata from the referred ER metadata configuration. 
36.    Click **Save**. 
37.    Close the page. 
38.    Close the page. 
39.    When needed, you can extend the existing set of metadata and then export the new completed version of ER metadata configuration. You can then import it to RCS, and update the prerequisites of the configured model mapping configuration referring to a new version of imported metadata configuration. 

> [!NOTE]
> This way of getting information about application metadata is the only one available for locally deployed applications (when local business data (LBD), or on-premises, deployment model is used).
        


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
