---
# required metadata

title: Customize tax configurations for master data lookup
description: This topic explains how to customize tax configurations to extend master data lookup functionality.
author: kai-cloud
ms.date: 05/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: pashao
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18
---

# Customize tax configurations for master data lookup

[!include [banner](../includes/banner.md)]

Complete the steps in this topic to customize tax configurations to extend master data lookup functionality.

**1 Set entity you want to use by following the Enabling virtual entities] step in**  https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference

**2 Create customized data model configuration**

- Choose data model configuration named **Tax Data Model - Europe**.
- Click **Create configuration**. 
- Choose "Taxable document model derived from Name: Tax Data Model - Europe, Microsoft". 
- In **Name** field, type in **Customization data model**.
- Click **Create configuration.**

[![pic1](./media/pic1.png)](./media/pic1.png)

**3 Create customized reference models**

- Choose the newly-created Customization data model.
- Click Designer.
- Change view to reference model

[![pic2](./media/pic2.png)](./media/pic2.png)

- Create the customized reference model. See [link to how to create reference model]. Customized model is root model. Customized entity is Record list. Customized field is string field you want to use in lookup. You can add more on demand.

[![pic3](./media/pic3.png)](./media/pic3.png)

- Change view to taxable document

[![pic4](./media/pic4.png)](./media/pic4.png)

- Choose the attribute you want to bind the customized reference model. Take **Customized attribute** as an example, click **Select reference model**, choose **Customized model**, click **OK**. The reference model name will be in the **Natural key** field.

[![pic5](./media/pic5.png)](./media/pic5.png)

- Save the configuration and complete.

**4 Create customized model mapping configuration**

- Choose model mapping configuration named **Dataverse model mapping**. Set **Default for model mapping** as **No**.
- Click **Create configuration**.
- Choose Taxable document model mapping derived from Name: Dataverse Model Mapping, Microsoft.
- In **Name** field, type in **Customization     model mapping**.
- In **Target model** field, choose the     newly-created data model **Customization data model**.
- Click **Create configuration**.

[![pic6](./media/pic6.png)](./media/pic6.png)

- The model mapping configuration will show up as

[![pic7](./media/pic7.png)](./media/pic7.png)

- Choose the **Customization model mapping** and set **Connected application** as the one you created above.

  Set **Default for model mapping** as **Yes**.

**5 Create customized model mappings**

- Choose the newly-created **Customization model mapping**. 
- Click Designer.
- Choose the newly-created **Customization Model**

[![pic8](./media/pic8.png)](./media/pic8.png)

**6 Map model mapping to Dataverse entity**

- In model mapping designer, choose Customization Model and click Designer.
- In **data source types**, choose Dataverse Table.
- In **data sources**, click **+Add root**.
- In **Name** field, type in Customized Dataverse.
- In **Name** field, choose an entity.
- Click **OK**.

[![pic9](./media/pic9.png)](./media/pic9.png)

- Choose **Customized Dataverse** and **Customized entity**, click **Bind**.

[![pic10](./media/pic10.png)](./media/pic10.png)

- Choose a field under **Customized Dataverse** and **Customized field**, click **Bind**.

[![pic11](./media/pic11.png)](./media/pic11.png)

- Click **save** and complete **Customization model mapping**

**7 Create customized tax configuration**

- Choose **Tax Configuration - Europe** and click Create configuration**.
- Choose Tax service configuration derived from Name: Tax Configuration - Europe, Microsoft
- In **Name** field, type in Customization configuration.
- Click **Create configuration**.

[![pic12](./media/pic12.png)](./media/pic12.png)

- Choose newly-created Customization configuration** and click **Designer**.
- In **Data model** field, choose **Customization data model**
- In **Data model version** field, choose the corresponding one.

[![pic13](./media/pic13.png)](./media/pic13.png)

- Complete the configuration.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
