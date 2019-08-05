---
# required metadata

title: Fault management
description: This topic explains fault management in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/27/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Fault management


In **Asset Management**, you can manage faults detected on assets by describing symptoms, areas, and fault types. The fault designer allows you to set up symptoms, areas, and fault types on asset types. Also, fault causes and suggestions to remedy faults can be registered on a work order.

The sequence of registration and management of faults is: First, you create a list of fault symptoms, fault areas, and fault types that may occur on your asset types. Next step is setting up symptoms, fault areas, and fault types in the Fault Designer. To understand the distinction between fault symptoms, fault areas, and fault types, here are a few examples:

**Fault symptoms:**

- Unbalanced voltages  

- Short circuit  

- Noise  

- Leak  

- Vibrations  


**Fault areas:**

- Electrical  

- Mechanical  

- Hydraulic  

- Pneumatic  


**Fault types:**

- Faulty main stator winding  

- Faulty diode  

- Dirty windings  

- Defective generator  

- Defective sensor  


## Create fault symptom

Create a list of symptoms to be used in the fault designer.  

1. Click **Asset management** > **Setup** > **Fault** > **Fault symptoms**.  

2. Click **New** to create a new record.  

3. Insert a name for the symptom in the **Fault symptom** field.

4. Insert a description in the **Description** field.

5. Click **Save**.


## Create fault area

Create a list of areas or locations to be used in the fault designer.

1. Click **Asset management** > **Setup** > **Fault** > **Fault areas**.

2. Click **New** to create a new record.

3. Insert a name for the area in the **Fault area** field.

4. Insert a description in the **Description** field.

5. Click **Save**.


## Create fault type

Create a list of fault types to be used in the fault designer.

1. Click **Asset management** > **Setup** > **Fault** > **Fault types**.

2. Click **New** to create a new record.

3. Insert a name for the type in the **Fault type** field.

4. Insert a description in the **Description** field.

5. Click **Save**.


## Set up fault designer

In Fault designer, you set up fault data on asset types.

1. Click **Asset management** > **Setup** > **Fault** > **Fault designer**.

2. In the left-hand side of the form, select the asset type for which you want to set up a fault record.

3. On the **Fault symptom** FastTab, click **Add line**, and select a symptom in the **Fault symptom** field.

4. On the **Fault area** FastTab, click **Add line**, and select an area in the **Fault area** field.

5. On the **Fault type** FastTab, click **Add line**, and select a type in the **Fault type** field.

6. Click the **Create fault combinations** button to quickly create combinations of all existing fault symptoms, areas, and types to the selected asset type. This function is useful if you have created many combinations. If you do not want to use all combinations on the asset type, it is easier to delete the lines that are not relevant than to create new lines manually.

7. Click the **Copy from asset type** button to copy the specific setup of fault symptoms, areas, and types from one asset type to another asset type.

8. Click **Save** to save the changes.


![Figure 1](media/21-setup-for-work-orders.png)


## Create fault cause

Create a list of known fault causes, which can be added to a work order or a maintenance request.

1. Click **Asset management** > **Setup** > **Fault** > **Fault causes**.

2. Click **New** to create a new record.

3. Insert a name for the fault cause in the **Fault cause** field.

4. Insert a description in the **Description** field.

5. Click **Save**.


## Create fault remedy

Create a list of suggestions for remedy and repair, which can be added to a work order or a maintenance request.

1. Click **Asset management** > **Setup** > **Fault** > **Fault remedies**.

2. Click **New** to create a new record.

3. Insert a name for the remedy in the **Fault remedy** field.

4. Insert a description in the **Description** field.

5. Click **Save**.


>[!NOTE]
>If required, you can change or update the names of your fault symptoms, areas, types, causes, and remedies. The name changes are automatically reflected in the related fault registrations.

