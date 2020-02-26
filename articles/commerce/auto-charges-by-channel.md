---
# required metadata
title: Omni-channel advanced auto charges
description: Dynamics 365 Commerce's advanced auto charges for applying fees for transaction header or lines, based on channel or order creation. For e.g. if you want to apply recycling fees for group of products sold in all stores in California state, USA 
author: gvrmohanreddy
manager: jeffbl
ms.date: 2/12/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2020-04-03
ms.dyn365.ops.version: 10.0.10
---

# Auto charges by channel of order creation

## Overview

You may have scenarios like applying recycling fees for group of products that are sold in all or some of the stores in California state, USA. This topic provides information on how to enable and configure auto-charges by channel of the order creation. This feature is available in Dynamics 365 Commerce in version 10.0.10 or later. 



> [!NOTE]
> Auto charges by channel feature works only when the **advanced auto-charges** feature is enabled. Refer to advanced auto-charges for more details. 



## Auto charges by channel configuration

**Enable auto charges by channel**
A new feature switch called **Enable filter auto charges by channel** is created to enable auto charges by channel feature, and use the following steps to turn it on:
 

	1. Go to **System administrator** > **Workspaces**  > **Feature management**.
	2. Under **Not enabled** list search for  **Enable filter auto charges by channel**.
	3. Click **Enable now** button on the right bottom corner. 
	4. After it's enabled you can find the switch under **All**
	5. Go to **Retail and Commerce** > ** Retail and Commerce IT** > **Distribution schedule** then run **1110 Global configuration** CDX job to propagate the configuration changes. 

> [!WARNING]
> If you decide to disable **Enable filter auto charges by channel** switch after using the feature, you will notice that **Retail channel relation** dropdown disappearing under **Auto charges**. Review all auto-charges rules and make necessary changes to the rules those configured using channel relation, as some auto charges rules may become duplicative to an existing auto-charge that was configured without the channel.  


**Configure organization hierarchy purpose**

A new organization hierarchy purpose called **Retail auto charges** has been created for managing hierarchy for auto charges by channel. Use the following steps to configure hierarchy purpose with a default hierarchy: 
		
	1. Go to **Organization administration** > **Organizations** >  *Organization hierarchy purposes**. 
	2. Select **Retail auto charges** from the list 
	3. Click **+ Add** button under **Assigned hierarchies**. 
	4. Select a hierarchy e.g. **Retail Store by Region** and click **Ok**
	5. Click **Set as default**
	6. Go to **Retail and Commerce** > ** Retail and Commerce IT** > **Distribution schedule**.
	7. Run **1040 Products** , **1070 Channel configuration** , and **1110 Global configuration** CDX jobs. 

![Dynamics 365 Commerce - Auto charges by channel](media/Auto-charges-org-hierarchy-purpose.png)

	
	

## Defining auto charges by channel

After enabling **auto charges by channel feature** switch and configuring **Retail auto charges** organization hierarchy purpose, auto charges by channel can be defined at order header level or line level using following steps:


Go to **Accounts receivable** > **Charges setup** > **Auto charges**  


	1. Define auto-charge either at **header** level or **line** level based on business requirements. 
	2. In the charges header, select **Retail channel code**  e.g. Table or Group.  By default this is set to **All**, which means charge rules are applied for all channels. 
	3. For group, make sure a **Retail channel charges group** is created that you can find under ** Retail and Commerce** > **Channel setup** > **Charges** > ** > Retail channel charge groups**
	4. For Table, you can select a specific channel, e.g. **San Francisco** store under **Retail channel relation** dropdown.  
	5. Go to **Retail and Commerce** > ** Retail and Commerce IT** > **Distribution schedule**.
	6. Run **1040 Products** , **1070 Channel configuration** , and **1110 Global configuration** CDX jobs. 
	

	


![Dynamics 365 Commerce - Auto charges by channel](media/Auto-charges-line-charge-by-channel.png)

##Scenario
The following two scenarios outlines the steps to configure a product with recycling fees when it is sold through San Francisco brick and mortar  channel and behavior of the auto-charges in the POS application.

In this scenario, the organization has defined charges code called **RECYCLE** with the following details: 

![Dynamics 365 Commerce - Auto charges by channel](media/Auto-charges-charge-code.png)




An auto charge is crated at line level where account code is set to **All**, Item code is set to **Table** and Item relation is set to product id 91001 , Mode of delivery code is set to **All**,  Retail channel code is set to **Table**, and Retail channel relation is set to **San Francisco** store. 

Auto-charges line is created where current is set to **USD**, Charges code is set to **RECYCLE**, Category is set to **Fixed** and Charges are set to **$6.25**.

![Dynamics 365 Commerce - Auto charges by channel](media/Auto-charges-recyclingfee-line-fee.png)






A sales order is created in **San Francisco** store channel using Dynamics 365 Commerce's POS application. Product id **91001** is added to the sales orders. Notice **CHARGES** in the lines are with **$6.25**.  Selecting **Transaction options** > **Charges** and then **Manage charges** will show **Recycling fee** charges code and it's description. 


![Dynamics 365 Commerce - Auto charges by channel](media/pos-auto-charges-recyclingfee-line-fee)


