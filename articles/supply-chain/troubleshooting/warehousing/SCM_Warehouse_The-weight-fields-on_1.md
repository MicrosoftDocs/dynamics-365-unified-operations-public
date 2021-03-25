---
# required metadata

title: The weight fields on load lines do not match the weight fields on load
description: The weight fields on load lines do not match the weight fields on load
author: SmithaNataraj
manager: tfehr
ms.date: 3/9/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSShipmentDetails_WHSBillOfLadingGenerate
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: hja@microsoft.com

---

# The weight fields on load lines do not match the weight fields on load

Error code: WHSShipConfirm

The system displays the following error message:

> The weight fields on load lines do not match the weight fields on load %1. Run the Warehouse load weight consistency check to recalculate the weight fields.

## Symptoms
The **Net weight** and **Tara weight** are set to zero on the load line. The weight fields are not zero on the weight measurements on the product. When weight fields are not set on the load line, any corrections of the quantity on the load line might result in incorrect weight calculation on the load. This might be the case if the weight on the product have been changed since the load line was created.




## Resolution
When a load line is created, the weight fields from the product will be defaulted on the load line. If the weight is zero, it can be recalculated using the **Warehouse load weight consistency check**.

1) Open **System administration > Periodic tasks > Database > Consistency check**.
2) Expand the **Warehouse management** section.
3) Select the **Warehouse load weight consistency check** and ensure that the check mark is set.
4) Select …
5) Select **Dialog**
6) Specify the values for which the consistency should run:
	- For a specific Load and/or Item
	- Set **Always recalculate weight on loads** and **Allow overwrite of weight on load lines** to *Yes*.
7) Select **OK** to close the dialog.
8) Ensure that Check/Fix is set correctly.
9) Select …
10) Select **Execute**

The weight will be recalculated based on the criteria selected. Click the **Message details** link to see the result of the executed consistency check.



