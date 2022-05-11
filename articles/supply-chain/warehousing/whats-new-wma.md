---
title: What's new or changed in the Warehouse Management mobile app
description: This topic lists the new and changed features for each released version of the Warehouse Management mobile app for Microsoft Dynamics 365 Supply Chain Management.
author: Mirzaab
ms.date: 04/25/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-06-07
ms.dyn365.ops.version: 10.0.21
---

# What's new or changed in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This topic lists new features, fixes, improvements, and known issues for each released version of the Warehouse Management mobile app for Microsoft Dynamics 365 Supply Chain Management.

## Version 2.0.22.0

This version introduces the following new features, fixes, and improvements:

- Fixed several crashing issues.
- Fixed an issue where some characters would not be recognized when scanning or typing on the default page.
- Fixed an issue where typing a backspace on the default page would delete two characters at a time.
- Fixed an issue where the **Sort by** field on the **Work list** page would display an incorrect value that didn't correspond to the actual sorting order of the cards.
- Fixed an issue where an incorrect layout would be shown after resizing the app window while running on Microsoft Windows.
- Fixed an issue where scrolling in a pop-up list could result in some list items remaining hidden or becoming distorted.
- Redesigned the sign-in page to let it display the username and password fields on the same page when running on larger displays.
- Improved the way controls react to fast tapping.
- Added an in-app error log view.
- Added several accessibility improvements (improved narration, fixed missing placeholders on Android, enabled keyboard input for slider controls, and more).

## Version 2.0.20.0

This version introduces the following new features, fixes, and improvements:

- Fixed several crashing issues.
- Fixed an issue where incorrect values would be shown on cards on the **Work list** page.
- Improved the scrolling experience and eliminated scrolling jitter on the **Work list** and **Item inquiry** pages in Android.
- Added an exit button to the sign-in page, which quits the application.

## Version 2.0.19.0

This version introduces the following new features, fixes, and improvements:

- Improved the generic data inquiry flow.
- Improved the jittering issue on **Work list** and **Item inquiry** pages.
- Reduced battery consumption.
- Removed the limit on the number of fields for work cards.
- Adjusted the height of work cards so that all of them have the same size, regardless of the number of fields in each.
- Fixed an issue where space characters in bar codes would be trimmed out.
- Added the **Button style** setting, which lets you swap between slider view and button view on all types of devices.
- Fixed various issues that could cause the app to crash.
- Set focus automatically on the first textbox on custom pages.
- Accessibility improvements related to luminosity, contrast, narration, and missing placeholder texts.

## Version 2.0.17.0

This version introduces the following new features, fixes, and improvements:

- Fixed an issue where bar codes would be scanned incorrectly.
- Fixed the GS1 scanning issue for the camera scanner.
- Fixed the GS1 scanning issue for the bar code scanner on Zebra devices.
- Improved the detour inquiry flow, so selecting a card in a detour now returns to the main flow.
- Added support for a generic data inquiry flow.
- Added a message to tell users about changes to the network connectivity status.
- Aligned storage permissions with the storage privacy policy in Android 10.
- For flows that need it, the quantity spinner now includes a position that lets users submit an empty numeric value.
- Fixed issues with the quantity spinner orientation.
- Fixed an issue where the quantity spinner would jump to the wrong value.
- Fixed an issue where input to the primary page would get lost when being populated from the details page.
- Fixed an issue where placeholder text would be treated as the initially selected value in selection lists.
- The "Submit" button on confirmation steps is now automatically enabled if there are preselected values.
- Fixed the details card to show as many lines as possible for text fields that have multiple lines.
- Fixed the height of the "Submit" and "More actions" buttons, so now they take up less space on the screen.
- Added missing selection list titles.
- Fixed an issue where the back button didn't work.
- Added several keyboard navigation fixes and improvements, including on the following pages:
  - User login
  - Select connection
  - Edit connection
- Fixed scrolling when using keyboard navigation.
- Enhanced accessibility, including the following improvements:
  - Fixed color visibility and contrast.
  - Prevented loss of keyboard focus when pop-up pages are closed.
  - Added error messages to the narration.
  - Increased the size of placeholder values in the step banner.
- Fixed the example of the custom legacy page in demo mode.

## Version 2.0.15.0

This version introduces the following new features, fixes, and improvements:

- Improved performance by fixing a memory leak issue.
- Fixed an issue where some field values didn't update correctly when selected on the detail page.

## Version 2.0.14.0

This version introduces the following new features, fixes, and improvements:

- Fixed an issue that disabled the default Submit button.

## Version 2.0.13.0

This version introduces the following new features, fixes, and improvements:

- Improved scrolling between pages with smoother animation.
- Fixed counter-intuitive responses to swipe motions and occasional screen freezes.
- Improved dark mode text and background color combinations for better readability.
- Fixed an issue where some text could become very small when resizing the app window.
- Fixed an issue that could sometimes crash the app when scanning bar codes.
- Added the possibility to replace a slider with a button.
- Fixed an issue that could cause the app to show the error message, "AADSTS7000215: Invalid client secret is provided."
- Fixed the hint animation showing how to close a page using a swipe-down gesture.
- Added the possibility to close a page using a flick-down gesture.
- Fixed an issue where drop-down list titles weren't shown on the **User settings** page.
- Fixed a localization issue where the app wouldn't recognize a comma (,) as a decimal separator.
- Improved accessibility.
- Fixed the navigation on the **New connection** page to provide improved accessibility.
- Fixed an issue where the soft (onscreen) keyboard wouldn't appear when selecting an input field.
- Fixed an issue that could crash the app if users quickly resized its window.
- Fixed an issue where a fast keypress was sometimes interpreted as a long press.
- Fixed an issue where the app layout could become corrupted because of field customizations made in Supply Chain Management.
- Fixed an issue where item locations weren't displayed properly.
- Fixed an issue related to short picking for the product variant workflow.
- Removed the unnecessary validation of fields containing preset default values.
- Improved performance.
- Added a new setting that allows users to choose how fields are filtered and ordered on the card page.

## Version 2.0.11.0

This version introduces the following new features, fixes, and improvements:

- Added support for promoted fields.
- Added support for hardware keyboard navigation.
- Improved accessibility.
- Enhanced details cards.
- Enhanced detours for menu-item steps.
- Minor user interface improvements.
- Fixed an issue that could cause the app to crash when scanning bar codes.
- Fixed various issues that could cause the system to stop responding.

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
