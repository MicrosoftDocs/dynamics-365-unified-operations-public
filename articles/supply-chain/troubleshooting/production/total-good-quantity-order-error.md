--- 
title: Total good quantity error when trying to end an order 
description: When trying to end a production order and report as finished, you may receive a total good quantity error. This page explains why and how to fix the issue. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form: 
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Total good quantity error when trying to end a production order

## Symptoms

When you try to post a report as finished journal on a production order, you receive the following error message:

> Total good quantity reported as finished for the production will be %1. Feedback for the last operation is 0.00 in total.

## Cause

This issue occurs if the quantities that were posted in the last operations were incorrect. For example, if production is started, but the quantity that must be started isn't allocated, the route card journal will be posted without any lines. To confirm the situation, open the production order, and then on the Action Pane, on the **View** tab, select **Route card**.

## Resolution

You can fix this issue by posting additional journals for the operations that the journals weren't correctly posted for. Restart the production order and select to post the additional journals. This action won't start the production order, but it will post the journals. The route card should then show the quantities that were posted, and you should be able to end the production orders successfully.
