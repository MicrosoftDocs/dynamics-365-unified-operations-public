---
title: What's new or changed in the Warehouse Management mobile app
description: This topic lists the new and changed features for each released version of the Warehouse Management mobile app for Microsoft Dynamics 365 Supply Chain Management.
author: MarkusFogelberg
ms.date: 09/09/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mafoge
ms.search.validFrom: 2021-06-07
ms.dyn365.ops.version: 10.0.21
---

# What's new or changed in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This topic lists new features, fixes, improvements, and known issues for each released version of the Warehouse Management mobile app for Microsoft Dynamics 365 Supply Chain Management.

## Version 2.0.10.0

This version introduces the following new features, fixes, and improvements:

- Added animation when swiping through lists and pages.
- Text now wraps correctly on the connection error page.
- Combo boxes without default values now display correctly.
- Information in the subheader area is now shown only on the full details page.
- Empty input fields are no longer shown on the details card.
- Confirmation values are no longer duplicated on the details card.
- Fixed various issues that caused the system to stop responding.

## Version 2.0.9.0

This version fixes an issue where the app could stop responding if users page up from the top of a list.

## Version 2.0.8.0

This version introduces the following new features, fixes, and improvements:

- Added support for the [step instructions feature](mobile-app-titles-instructions.md) that was introduced in Supply Chain Management version 10.0.21.
- Added hint animation to show users that they can close overlays by swiping down.
- Added support for function keys on action lists and menus. Users can hold down any function key for three seconds to get a list of available commands.
- Fixed an issue that caused the following error message to be shown on some devices: "Cannot find a suitable view for the specified size."
- Fixed an issue where full-screen mode didn't always work when the on-screen keyboard is used.
- Fixed an issue where page swiping didn't work on Windows devices.
- Fixed various issues that caused the system to stop responding.

## Version 2.0.7.0

### New features, fixes, and improvements in version 2.0.7.0

- Added a section to the **About** page that checks latest released version of the app.
- Made it easier to flick and swipe between pages.
- Changed the icon for the ascending/descending button on the work list.
- Reduced the margins on the **Details** card to allow it to fit more information.
- Applied various performance improvements to reduce the issue of the app becoming slower over time.
- If there are more controls than fit on the screen, resulting in paging, the spinner control no longer scrolls the same way as the page.
- Prioritize showing the last scanned value over showing the task title, so if they overlap the task title will be truncated.
- Fixed various issues that caused the system to stop responding.
- Text in various places is no longer cut off in some languages.
- The app now runs in full-screen mode by default.
- Fixed an issue that would occasionally cause scans to be ignored on main page with certain devices.

### Known issues in version 2.0.7.0

- On some devices, you will get the following error message when you start the app or begin a task: "Cannot find a suitable view for the specified size." If you see this error message on any of your devices, you must downgrade the Warehouse Management mobile app to version 2.0.6.0 on that device and wait to upgrade until the next version of the app is released.

## Version 2.0.6.0

### New features, fixes, and improvements in version 2.0.6.0

This version introduces the following new features, fixes, and improvements:

- Demo mode now shows all labels in the device language.
- You're less likely to receive the following error message: "Cannot find a suitable view for the specified size."
- The minimum height for work cards has been increased (for cases where three or fewer fields are configured to appear in the work list).
- Margins (fade out) at the bottom of details cards have been improved.
- Invalid symbols in XML files that are exchanged with the server are now handled gracefully. (For example, non-printable characters are now handled gracefully and no longer cause the app to stop responding.)
- HTTP errors (such as "error 503") when a server request is submitted are now handled gracefully.
- While an error is being shown, the options list is no longer automatically shown for combo box controls.
- The app no longer stops responding because of the display orientation that is selected in user settings.
- Product images are now shown in self-service environments. (This change applies to low-resolution versions only. The file management service doesn't support full-sized images in self-service environments.)
- An issue that involved zero-quantity short picks has been fixed.
- The app no longer stops responding when a details card shows multiple identical fields.

### Known issues in version 2.0.6.0

The following known issues exist in this version:

- The app (especially the work list) becomes slower over time.
- **Windows version:** When a USB gun is used for scanning on Windows, inconsistent results cause scanned symbols to be mixed up.

## Version 2.0.5.0

This version introduces the following new features, fixes, and improvements:

- The client secret is no longer hidden in the connection settings setup.
- You can now long-press on any text to see it fully.
- The error message when storage permissions are missing has been improved.
- New control sequences have been added for some flows.
- The submit button no longer incorrectly becomes available because of the window size.
- Sliders can now proceed on smaller screens when larger button sizes are used.
- The four-button overlay is no longer cut off.
- The keyboard now supports the delete button.
- A brightness issue that could occur when the keyboard is pressed has been fixed.
- Various demo data issues have been fixed.
- An issue that affected numeric fields on the details page has been fixed.
- The screen keyboard no longer occasionally disappears on some devices.
- Various user interface (UI) bugs have been fixed, such as bugs that affected the background color and positioning.
- The Russian-language UI has been improved.
- Various issues that caused the system to stop responding have been fixed.
- An issue that was related to reopening the calculator has been fixed.
- **Android version:** An issue that caused Android 4.4 to stop responding on startup has been fixed.
- **Android version:** Minimum scaling has been reduced to 50 percent.

## Version 2.0.4.0

Version 2.0.4.0 was the first generally available release of the Warehouse Management mobile app.

### New features, fixes, and improvements in version 2.0.4.0

This version introduces the following new features, fixes, and improvements that weren't available in the preview version:

- If a details card includes two labels that have identical data, one of the labels is hidden.
- Special characters are now shown by default, and the option to hide them has been removed from user settings.
- Disabled submit buttons are now shown as unavailable in compact arm-held view.
- A change to the sequencing logic for controls ensures smoother scaling across devices. Therefore, there is less need to adjust the scaling of fonts or buttons.
- The default color theme has been changed to *Dark*.
- The missing icon for the disabled submit button has been added in ribbon view.
- Time-out exceptions now take you to the connection page instead of showing an in-line error.
- If no submit action is available (such as **OK**, **Yes**, **Accept**, **Done**, or **Finished**), the submit button will be disabled.
- App stability has been improved.
- There is a fix for security vulnerability [CVE-2021-26701](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-26701).
- **Windows version:** An issue on Windows, where menus were unresponsive after the window was resized, has been fixed.

### Known issue in version 2.0.4.0

The following known issue exists in this version:

- This version has an issue with devices that use Android 4.4. You might experience issues when you use the app on this Android version.
