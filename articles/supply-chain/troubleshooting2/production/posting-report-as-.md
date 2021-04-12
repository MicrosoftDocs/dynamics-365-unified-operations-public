---
# required metadata

title: Posting - Report as finished journal gives the error "Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status"
description: Posting - Report as finished journal gives the error "Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status"
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProdTableListPage, ProdParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: johanho@microsoft.com

---

# Posting - Report as finished journal gives the error "Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status"

KB Number: 4612891

Posting - Report as finished journal gives the error "Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status. The items are Purchased, Received or Registered."

It happens only when "Error quantity" is populated on the first journal line and "Good quantity" on the last journal line. If the "Error quantity" line is populated on last line in RAF journal , then  there is no error. 


## Resolution
This issue can be resolved by setting the production parameter Increase remain qty with error qty to Yes in the Production control parameters form.


