---
title: About service level agreements
TOCTitle: About service level agreements
ms:assetid: 05290d56-0616-4517-aa20-ec6bc86258d6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg230663(v=AX.60)
ms:contentKeyID: 37832489
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg242492(v=ax.60)/toc.json
f1_keywords:
- sla
- service agreement
- service level
---

# About service level agreements 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

A service level agreement (SLA) is an agreement between a service company and a service customer. In an SLA, the customer agrees to a minimum response time based on when the service company records the issue and when the issue is resolved.

An SLA enforces a standard level of service that is offered to customers, and also makes it transparent to a service company when a service job should be completed.

Any number of SLAs can be created to offer service customers different levels of service.

## Create a service level agreement

1.  Click **Service management** \> **Setup** \> **Service agreements** \> **Service level agreements**.

2.  Type a name for the service level agreement in the **Service level agreement** field.

3.  Type the time that you want to allow for completion of service calls that are attached to the service level agreement. Then select a calendar if you want to base the service level agreement on a specific calendar.

## Apply a service level agreement

The SLA is applied directly to a service agreement.

Service orders that you create manually and attach to a service agreement that has an SLA are measured against that SLA.

Service orders that you create automatically are not attached to an SLA.

## Apply the service level agreement to the service agreement

1.  Click **Service management** \> **Common** \> **Service agreements** \> **Service agreements**. Select the service agreement that you want to apply the SLA to, and then click **Edit** on the **Action Pane**.

2.  In the **Service level agreement** field, select the SLA that you want to assign.

## Apply the service level agreement to the service agreement group

1.  Click **Service management** \> **Setup** \> **Service agreements** \> **Service agreement groups**.

2.  In the **Service level agreement** field, select the SLA that you want to assign.

## Track time on a service order against an SLA

When you create a new service order for a service agreement that an SLA is assigned to, the time interval for the delivery of the service is initiated, and the system starts to track the delivery time. Additionally, you can set the following options:

  - You can start and stop time recording on the service order to register the total amount of time that is spent on service orders.

  - You can monitor compliance with the time interval that is set in the service level agreement.

  - You can define reason codes that must be set if the time interval of the service level agreement is exceeded.

## See also

[View compliance with service level agreements](view-compliance-with-service-level-agreements.md)

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

