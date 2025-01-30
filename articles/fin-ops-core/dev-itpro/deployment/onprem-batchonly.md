---
title: Configure batch-only and interactive-only AOS nodes in on-premises deployments
description: Learn how to configure your environment so that you can deploy batch-only and interactive-only AOS nodes for new and existing deployments.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/19/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-04-30
ms.dyn365.ops.version: Platform update 36 
ms.service: dynamics-365-op
---

# Configure Batch-only and Interactive-only AOS nodes in on-premises deployments

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> This feature is supported starting in application update 10.0.12, Platform update 36.

This article explains how to configure your environment so that you can deploy batch-only and interactive-only Application Object Server (AOS) nodes.

To make this feature available, Microsoft has introduced two new Microsoft Azure Service Fabric node types. For batch-only AOS nodes, the new node type is **BatchOnlyAOSNodeType**. For interactive-only AOS nodes, the new node type is **InteractiveOnlyAOSNodeType**.

> [!NOTE]
> The traditional deployment option, where an AOS node is interactive and is running batch jobs, is still supported and isn't affected by these changes.

## Sizing

For sandbox environments, we recommend that you have at least two nodes of each type.

For production environments, there should be at least three nodes of each type.

## New deployments

1. When you're describing your configuration as explained in [Set up and deploy on-premises environments](./setup-deploy-on-premises-latest.md#describeconfig), edit the **configtemplate.xml** file to enable the new node types. When you are done, the template should resemble the following example.

```xml
<NodeType name="AOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="true">
    <VMList>
        <VM name="aos1" ipAddress="" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
        <VM name="aos2" ipAddress="" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
        <VM name="aos3" ipAddress="" faultDomain="fd:/fd0" updateDomain="ud2" hasSSIS="false" />
    </VMList>
</NodeType>
<NodeType name="InteractiveOnlyAOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="false">
    <VMList>
        <VM name="LBDE05FS1AOS01" ipAddress="192.168.5.51" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
        <VM name="LBDE05FS1AOS02" ipAddress="192.168.5.52" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
        <VM name="LBDE05FS1AOS03" ipAddress="192.168.5.53" faultDomain="fd:/fd0" updateDomain="ud2" hasSSIS="false" />
    </VMList>
</NodeType>
<NodeType name="BatchOnlyAOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="false">
    <VMList>
        <VM name="LBDE05FS1AOS04" ipAddress="192.168.5.54" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
        <VM name="LBDE05FS1AOS05" ipAddress="192.168.5.55" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
        <VM name="LBDE05FS1AOS06" ipAddress="192.168.5.56" faultDomain="fd:/fd0" updateDomain="ud2" hasSSIS="false" />
    </VMList>
</NodeType>
```

2. Follow the remaining instructions in [Set up and deploy on-premises environments](./setup-deploy-on-premises-latest.md#describeconfig) in the usual way.

## Existing deployments

1. Follow the instructions in [Remove a node](.\onprem-add-remove-node.md#remove-a-node) to remove all nodes you need to remove.

1. Follow the instructions in [Add a node](.\onprem-add-remove-node.md#add-a-node) to add the new nodes.

1. Once all of the nodes are added back in, from LCS use the Update Settings button without changing any settings to trigger an environment refresh. Alternatively you could also apply the latest hotfix.

     > [!IMPORTANT]
    > This step causes downtime so be sure that your environment can be unavailable for some time. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
