---
title: Create a template BOM   
description: Learn how to create a template BOM by using a variety of methods with processes for creating BOM templates either manually or based on other template BOMs. 
author: ChristianRytt
ms.author: crytt
ms.topic: article
ms.date: 05/01/2018
ms.custom:
ms.reviewer: kamaybac
ms.search.form: SMATemplateBOMTable
---

# Create a template BOM   

[!include [banner](../includes/banner.md)]


You can create a template BOM by using any of the following methods. For all methods, the **From date** and **To date** fields are optional and for information only.

## Create a template BOM manually

1.  Go to **Service management** \> **Setup** \> **Service objects** \> **Template BOMs**.

2.  Select **New** to open the **Create template BOM** form.

3.  Under **Copy BOM lines from reference**, select the **Manual** option.

4.  In the **Item number** field, enter an item of the type **BOM**.

5.  In the **Name** field, enter a name for the template.

6.  In the **From date** and **To date** fields, enter a date interval in which the template BOM is active.

7.  Select **OK**.

A new, blank template BOM is created.

## Create a template BOM based on another template BOM

1.  Select **Service management** \> **Setup** \> **Service objects** \> **Template BOMs**.

2.  Select **New** to open the **Create template BOM** form.

3.  Under **Copy BOM lines from reference**, select the **Template BOM** option.

4.  In the **Reference number** field, select an existing template BOM to copy to your new template BOM.

5.  In the **Name** field, enter a name for the template.

6.  In the **From date** and **To date** fields, enter a date interval in which the template BOM is active.

7.  Select **OK**.

A new template BOM is created by using lines that correspond to the lines in the original template BOM.

## Create a template BOM based on an item BOM

1.  Select **Service management** \> **Setup** \> **Service objects** \> **Template BOMs**.

2.  Select **New** to open the **Create template BOM** form.

3.  Under **Copy BOM lines from reference**, select **BOM**.

4.  In the **Reference number** field, select a BOM version. An item of the type BOM is copied to the **Item number**.

5.  In the **Name** field, enter a name for the template.

6.  In the **From date** and **To date** fields, enter a date interval in which the template BOM is active.

7.  Select **OK**.

A new template BOM is created by using lines that correspond to the lines of the BOM listed in **Bills of materials**.

## Create a template BOM based on a production BOM

1.  Select **Service management** \> **Setup** \> **Service objects** \> **Template BOMs**.

2.  Select **New** to open the **Create template BOM** form.

3.  Under **Copy BOM lines from reference**, select **Production**.

4.  In the **Reference number** field, select a production BOM.

5.  In the **Name** field, enter a name for the template.

6.  In the **From date** and **To date** fields, enter a date interval in which the template BOM is active.

7.  Select **OK**.

A new template BOM is created by using lines that correspond to the lines of the BOM listed in **BOM**.

## Related information

[Template BOMs](template-boms.md)

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]