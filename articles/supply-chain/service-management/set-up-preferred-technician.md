---
# required metadata

title: Set up a preferred technician   
description: You can select any worker as a preferred technician for a service agreement or service order. 
author: sorenva
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAAgreementTable, SMADispatchBoard
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


# Set up a preferred technician 

[!include [banner](../includes/banner.md)]


You can select any worker as a preferred technician for a service agreement or service order. However, it is a good idea to add the worker to the appropriate dispatch team so that the worker is included on the **Dispatch board**.

## Assign employee to a dispatch team

1.  Click **Human resources** \> **Common** \> **Workers** \> **Workers**. Double-click a worker to open the worker details page. On the **Action Pane**, click **Setup** \>**Dispatch team** to open the **Dispatch workers** form.

2.  In the **Dispatch team** field, select the team to assign the worker to.

## Assign a preferred technician to a service agreement

1.  Click **Service management** \> **Common** \> **Service agreements** \> **Service agreements**. Double-click a service agreement to open the details form.

2.  On the **General** tab, select the **Preferred technician** field, and then select a member of the appropriate dispatch team as the preferred technician for the service agreement.

## Assign a preferred technician to a service order

1.  Click **Service management** \> **Periodic** \> **Dispatch board**.
    

    > [!NOTE]
    > <P>In the <STRONG>Dispatch board</STRONG> form, specify a date range for dispatch activities to view. Also, specify whether to display closed activities and whether to limit the dispatch activity list to teams that you belong to or are authorized to monitor. Click <STRONG>OK</STRONG> to open the <STRONG>Dispatch board</STRONG>.</P>



2.  Select the line of the service activity to modify.

3.  On the **Related** tab, use the **Worker** list to assign a member of the appropriate dispatch team as the preferred technician for the service call.

## See also

[Develop and establish service agreements overview](service-agreements.md)

[Create service orders manually](create-service-orders-manually.md)

[Service agreements (form)](https://technet.microsoft.com/library/aa617823\(v=ax.60\))
  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]