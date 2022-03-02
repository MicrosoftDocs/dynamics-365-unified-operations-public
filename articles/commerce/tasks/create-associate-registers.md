--- 
# required metadata 
 
title: Create and associate registers
description: This procedure demonstrates how to create a point of sale (POS) register. 
author: BrianShook
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: RetailTerminalTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create and associate registers

[!include [banner](../includes/banner.md)]

This procedure demonstrates how to create a point of sale (POS) register. This procedure uses the demo data company USRT.

1. Go to Retail and Commerce > Channel setup > POS setup > Registers.
2. Click New.
3. In the Register number field, type an ID for the new register.
    * The register ID typically includes codes that help map the register to the store to which it belongs, and the location within the store.  
4. In the Name field, type a descriptive name for the register..
5. In the Store number field, enter or select a value.
6. In the Hardware profile field, enter or select a value.
    * Hardware profiles are used to specify the peripherals that will be connected to the register, such as cash drawer and receipt printer.  
7. In the Visual profile field, enter or select a value.
    * Visual profiles are used to specify the images used in the POS background and login page as well as themes for the POS.  
8. In the EFT POS register number field, type a value.
    * The EFT POS register number is used to inform the payment processor which payment terminal is sending authorization requests. This value is often called the "Terminal ID" or "TID". The TID can generally be found on a sticker on the payment device.  
9. Click Save.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]