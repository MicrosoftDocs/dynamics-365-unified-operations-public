---
# required metadata

title: Start and stop time recording on a service order 
description: Start and stop time recording on a service order.
author: sorenva
ms.date: 05/07/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAServiceOrderTable
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

# Start and stop time recording on a service order 

[!include [banner](../includes/banner.md)]


Use this procedure to start and stop time recording for a service order for which a service level agreement is defined.

## Start time recording

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Click the **Service order** tab. On the **Action Pane**, in the **Service level agreement** group, click **Start**.

3.  Enter the date and time that the time recording should be started.

## Stop time recording

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Click the **Service order** tab. On the **Action Pane**, in the **Service level agreement** group, click **Stop**.

3.  Enter the date and time that the time recording should be stopped.

4.  Select **Add a revocation reason**, and select a reason code in the **Stage reason code** list to provide a reason for stopping the time recording.


> [!NOTE]
> <P>If <STRONG>Reason code on exceeding time</STRONG> is selected in the <STRONG>Service management parameters</STRONG> form, you must provide a reason code before you can stop the time recording.</P>



## See also

[Start SLA time recording (form)](https://technet.microsoft.com/library/hh242297\(v=ax.60\))

[Stop SLA time recording (form)](https://technet.microsoft.com/library/hh242241\(v=ax.60\))

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]