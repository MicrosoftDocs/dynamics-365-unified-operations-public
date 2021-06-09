---
title: What's new or changed in Warehouse Management mobile app
description: This topic lists the new and changed features introduced with each released version of the Warehouse Management mobile app for Dynamics 365 Supply Chain Management
author: ivanv-microsoft
ms.date: 06/07/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ivanv
ms.search.validFrom: 2021-06-07
ms.dyn365.ops.version: 10.0.21
---

# What's new or changed in Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This topic lists new features, fixes, improvements, and known issues for each released version of the Warehouse Management mobile app for Dynamics 365 Supply Chain Management.

## Version 2.0.6.0

### New features, fixes, and improvements in version 2.0.6.0

This version introduces the following new features, fixes, and improvements:

- Demo mode now displays all labels in the device language
- You are less likely to see the error *Cannot find a suitable view for the specified size*
- Increased minimum height of work cards (for cases where three or fewer fields are configured to display on the work list)
- Improved margins (fade out) at the bottom of details cards.
- Graceful handling of invalid symbols in XML files exchanged with the server (for example, non-printable characters are now handled gracefully without crashing the app)
- Graceful handling of HTTP errors (such as "error 503") when submitting a server request
- When an error is being shown, the options list is no longer automatically displayed for combo box controls
- The app no longer crashes as a result of the display orientation selected in user settings
- Product images are now displayed on self-service environments (low-resolution versions only; the file management service doesn't support full-sized images in self-service environments)
- Fixed an issue with zero-quantity short picks
- The app no longer crashes when multiple identical fields are displayed by the details card

### Known issues in version 2.0.6.0

The following known issues exist in this version:

- The app gets slower over time (especially the work list)
- \[Windows\]: Inconsistent results when scanning with a USB gun on Windows, resulting in mixed up scanned symbols

## Version 2.0.5.0

This version introduces the following new features, fixes, and improvements:

- Client secret is no longer hidden in the connection settings setup
- You can now long-press on any text to see it fully
- Improved error message when missing storage permission
- New control sequences for certain flows
- Submit button no longer becomes enabled incorrectly as a result of the window size
- Sliders can now proceed on smaller screens when using larger button sizes
- The four button overlay is no longer cut off
- Keyboard now supports the delete button
- Fixed a brightness issue that could occur when the keyboard is pressed
- Fixed various demo data issues
- Fixed an issue affecting numeric fields on the details page
- The screen keyboard no longer disappears occasionally on some devices
- Fixed various UI bugs including background color, positioning, and more
- Improved Russian language UI
- Fixed various crashes
- Fixed a problem related to reopening the calculator
- \[Android\]: Fixed Android 4.4 crash on start-up
- \[Android\]: Reduced minimum scaling to 50%

## Version 2.0.4.0

Version 2.0.4.0 was the first generally available release of the Warehouse Management mobile app.

### New features, fixes, and improvements in version 2.0.4.0

This version introduces the following new features, fixes, and improvements compared to the preview version:

- If a details card includes two labels with identical data, one will be hidden
- Special characters are now shown by default, and the user-settings option to hide them has been removed
- Disabled submit buttons are now shown as disabled in compact arm-held view
- Changed sequencing logic of controls to ensure smoother scaling across devices, reducing the need to adjust the scaling of fonts or buttons
- Default color theme changed to *Dark*
- Added the missing icon for the disabled submit button in ribbon view
- Timeout exceptions now bring you to the connection page instead of displaying an in-line error
- If no submit action is available (such as OK, Yes, Accept, Done, Finished), the submit button will be disabled
- Improved app stability
- Fix for security vulnerability [CVE-2021-26701](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-26701)
- \[Windows\]: Fixed issue on Windows where menus were unresponsive after resizing the window

### Known issue in version 2.0.4.0

The following known issue exists in this version:

- This version has a problem with devices using Android 4.4, and you might experience issues using the app on this Android version.
