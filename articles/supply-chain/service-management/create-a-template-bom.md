---
title: Create a template BOM
TOCTitle: Create a template BOM
ms:assetid: 9c996197-facf-4df5-8c38-ac3cc1623226
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa571695(v=AX.60)
ms:contentKeyID: 36058733
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg231370(v=ax.60)/toc.json
---

# Create a template BOM 




You can create a template BOM by using any of the following methods. For all methods, the **From date** and **To date** fields are optional and for information only.

## Create a template BOM manually

1.  Click **Service management** \> **Setup** \> **Service objects** \> **Template BOMs**.

2.  Press CTRL+N to open the **Create template BOM** form.

3.  Under **Copy BOM lines from reference**, select the **Manual** option.

4.  In the **Item number** field, enter an item of the type **BOM**.

5.  In the **Name** field, enter a name for the template.

6.  In the **From date** and **To date** fields, enter a date interval in which the template BOM is active.

7.  Click **OK**.

A new, blank template BOM is created.

## Create a template BOM based on another template BOM

1.  Click **Service management** \> **Setup** \> **Service objects** \> **Template BOMs**.

2.  Press CTRL+N to open the **Create template BOM** form.

3.  Under **Copy BOM lines from reference**, select the **Template BOM** option.

4.  In the **Reference number** field, select an existing template BOM to copy to your new template BOM.

5.  In the **Name** field, enter a name for the template.

6.  In the **From date** and **To date** fields, enter a date interval in which the template BOM is active.

7.  Click **OK**.

A new template BOM is created by using lines that correspond to the lines in the original template BOM.

## Create a template BOM based on an item BOM

1.  Click **Service management** \> **Setup** \> **Service objects** \> **Template BOMs**.

2.  Press CTRL+N to open the **Create template BOM** form.

3.  Under **Copy BOM lines from reference**, select **BOM**.

4.  In the **Reference number** field, select a BOM version. An item of the type BOM is copied to the **Item number**.

5.  In the **Name** field, enter a name for the template.

6.  In the **From date** and **To date** fields, enter a date interval in which the template BOM is active.

7.  Click **OK**.

A new template BOM is created by using lines that correspond to the lines of the BOM listed in **Bills of materials**.

## Create a template BOM based on a production BOM

1.  Click **Service management** \> **Setup** \> **Service objects** \> **Template BOMs**.

2.  Press CTRL+N to open the **Create template BOM** form.

3.  Under **Copy BOM lines from reference**, select **Production**.

4.  In the **Reference number** field, select a production BOM.

5.  In the **Name** field, enter a name for the template.

6.  In the **From date** and **To date** fields, enter a date interval in which the template BOM is active.

7.  Click **OK**.

A new template BOM is created by using lines that correspond to the lines of the BOM listed in **BOM**.

## See also

[About template BOMs](about-template-boms.md)

  


