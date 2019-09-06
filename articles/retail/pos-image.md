# required metadata



title: POS client image handling implementation guidance

description: This topic is intended for people who implement functionality that is related to POS client image management in a retail environment. It gives implementation tips and guidance that you should consider as you plan your implementation.

author: cbittner

manager: 

ms.date: 07/30/2019

ms.topic: article

ms.prod: 

ms.service: dynamics-365-retail

ms.technology: 



# optional metadata



ms.search.form: 

# ROBOTS: 

audience: IT Pro

# ms.devlang: 

ms.reviewer: 

ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 

ms.custom: 

ms.assetid: 

ms.search.region: global

ms.search.industry: Retail

ms.author: cbittner

ms.search.validFrom: 2017-10-31

ms.dyn365.ops.version: Retail July 2017 update

---



# POS client image handling implementation guidance



[!include [banner](includes/banner.md)]



This topic is intended for people who implement functionality that is related to POS client image management in a retail environment. It gives implementation tips and guidance that you should consider as you plan your implementation.



## Overview

This implementation guidance applies to both POS client applications (CPOS and MPOS) and provides some general guidance on good practice of image file size handling. It also applies to the different image types (e.g. Welcome Screen, category and product images) that can be used to enrich store user experience and support customer focused scenarios like up- and cross selling and clientelling.



## Implementation considerations

This section describes some aspects that you should consider as you plan to use images in your POS client applications. It is recommended to prepare appropriate image file sizes for the respective purpose of use to have good user experience and positive impact regarding responsiveness of the POS client UI and performance while loading the different kind of images.



- **Hardware screens and displays** – The POS devices, respectively the screens and displays that are used will pre-determine reasonable image sizes (length and width). You should size the image as close to your intended screen size as possible.



- **Implementation example: Welcome Screen**  

For a common 18.5” POS display with a 1366 x 768 pixel resolution and a screen layout similar to Contoso demo data, having a welcome screen image covering two-thirds of the canvas, the image being used shouldn’t have much higher resolution regarding length and width of the screen. (911 x 512 pixel would be sufficient)

•	Resolution – Another important parameter to consider is the DPI (dots per inch) or for screen resolution PPI (pixel per inch). Since the POS client images will not be printed the DPI setting to render images appropriate for web is a good guideline.  

For high resolution devices, take OS scaling into account and use the effective resolution, rather than the actual pixels. Contoso demo image files are typically rendered to 96 dpi. 



Selecting fairly high resolution for length and width but keeping a low dpi setting will still result in reasonable small file sizes.



Contoso demo data e.g. for product and category images uses 500 x 500 pixel or 580 x 580 pixel      



- **File types** – Image files can be used in *.png or *.jpg type. In most cases *.jpg are even a little smaller in size.

© 2019 GitHub, Inc.
Terms
Privacy
Security
Status
Help

Contact GitH
