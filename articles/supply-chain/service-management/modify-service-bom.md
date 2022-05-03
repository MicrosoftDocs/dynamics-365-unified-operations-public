---
# required metadata

title: Modify a Service BOM 
description: Modify a Service BOM. 
author: sorenva
ms.date: 05/03/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAAgreementTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---


# Modify a Service BOM 

[!include [banner](../includes/banner.md)]


You can record the history of an element in a service BOM. Every time that you update a BOM line, a history line is created in the **History** pane. The history line shows the current state of the BOM line.

## Update a service BOM element

1.  Click **Service management** \> **Common** \> **Service agreements** \> **Service agreements**.

2.  Click **Edit** to open the **Service agreements** details form.

3.  On the **Action Pane**, click **Service objects** to open the **Service objects** form.

4.  Select the object to update a BOM line for, and then click **Designer**.

5.  In the **Designer** form, select the BOM line to update, and then click **Edit BOM line**.
    
    > [!NOTE]
    > <P>On the <STRONG>Setup</STRONG> tab, select the <STRONG>Edit when adding</STRONG> check box if you want the <STRONG>Edit BOM line</STRONG> form to open when you drag a line into the service BOM.</P>

6.  In the **Quantity** field, enter the quantity.

7.  If you want to create a service order line for the replacement item, which can then be invoiced, select the **Create service order line** check box.

8.  Click **OK** to close the form.

## Delete a service BOM line

1.  Click **Service management** \> **Common** \> **Service agreements** \> **Service agreements**.

2.  Click **Edit** to open the **Service agreements** details form.

3.  On the **Action Pane**, click **Service objects** to open the **Service objects** form.

4.  Select the object to delete a service BOM line from, and then click **Designer**.

5.  In the **Designer** form, select the BOM line to delete, and then click **Delete BOM line**.

## See also

[Template BOMs](template-boms.md)

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]