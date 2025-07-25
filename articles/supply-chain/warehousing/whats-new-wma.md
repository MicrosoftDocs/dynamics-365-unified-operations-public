---
title: What's new or changed in the Warehouse Management mobile app
description: This article lists the new and changed features for each released version of the Warehouse Management app for Microsoft Dynamics 365 Supply Chain Management.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: whats-new
ms.date: 07/23/2025
ms.custom:
  - bap-template
  - sfi-ropc-nochange
---

# What's new or changed in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

This article lists new features, fixes, improvements, and known issues for each released version of the Warehouse Management mobile app for Microsoft Dynamics 365 Supply Chain Management.

## Version 4.0.3.0

This is the second preview release of Warehouse Management mobile app version 4.

If you have any feedback about the preview version of this app, please send us email at [D365WMA-feedback@microsoft.com](mailto:D365WMA-feedback@microsoft.com).

### Preview release

This app is in preview. By installing this preview app, you are confirming that you have read and understand the [preview feature terms and conditions](https://go.microsoft.com/fwlink/?linkid=2173149).

### What's new in version 4.0.3.0

Version 4 introduces many new features and improvements that will enhance your warehouse management experience. For details, see [Migrate the Warehouse Management mobile app from V3 to V4](warehouse-app-migrating-from-v3-v4.md).

Version 4.0.3.0 adds the following fixes and improvements:

- Improved the sign-in process.
- Added a sign-in hint page.
- Added an automatic sign-in function.
- Improved the performance of the quantity spinner.
- Fixed an issue that could sometimes occur when changing between different users.

## Version 4.0.2.0

This is the first preview release of Warehouse Management mobile app version 4.

If you have any feedback about the preview version of this app, please send us email at [D365WMA-feedback@microsoft.com](mailto:D365WMA-feedback@microsoft.com).

### Preview release

This app is in preview. By installing this preview app, you are confirming that you have read and understand the [preview feature terms and conditions](https://go.microsoft.com/fwlink/?linkid=2173149).

### What's new in version 4

Version 4 introduces many new features and improvements that will enhance your warehouse management experience. For details, see [Migrate the Warehouse Management mobile app from V3 to V4](warehouse-app-migrating-from-v3-v4.md).

## Version 3.0.8.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Enabled seamless data migration between versions to ensure a smooth transition from version 3.x to version 4. For example, devices now preserve their connection settings so admins won't need to reenter them after migrating.
- Added a feature that lets workers know that version 4 is or will soon be available and how to migrate easily.

## Version 3.0.7.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Improved security.

## Version 3.0.6.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Fixed an issue that affected the connection on Android devices.

## Version 3.0.5.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Fixed an issue that affected the wireless network connection monitor.

## Version 3.0.4.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Fixed an issue that affected the wireless network connection monitor.
- Fixed an issue that could occur when changing color themes.
- Improved security and performance.

## Version 3.0.3.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.  
- Improved authentication stability and sign-in experience.
- Improved speed when changing between pages.  
- Improved connection stability and performance.
- Fixed decimal formats to better match the selected user culture.  
- Improved accessibility on the workload screen.

## Version 3.0.0.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.
- User-based authentication (device code or username/password) is now required. Support for service-based authentication methods (certificate and client secret) has been removed. You must update the connection settings on all devices that are still using service-based authentication.
- The Copilot button is now shown at the top of most pages (instead of as an entry on the **Main Menu** page) and has been relabeled to **Workload** because it opens the Copilot-generated workload summary.
- The **Settings** button is now shown as a gear icon at the right side of the title bar on most pages (instead of as an entry on the **Main Menu** page).
- Fixed an issue that could cause the app to freeze.

## Version 2.3.7.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.

## Version 2.3.6.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.
- Fixed an issue that could prevent the app from connecting to Copilot.
- Fixed a crash that could occur on Android 11 devices shortly after starting up the app.

## Version 2.3.4.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.
- Added a new and improved user interface for the Copilot screen.
- On devices that are still set up to use a deprecated authentication method, the app now shows a warning to tell users that the app will soon stop working if the connection settings aren't changed.
- Fixed a crash that could occur on Android devices when restarting the app after a long pause.

## Version 2.3.3.0

### New features introduced in version 2.3.3.0

This version of the Warehouse Management mobile app introduces the following new features:

- Simplified authentication setup by providing an option that doesn't require that you register or maintain your own Microsoft Entra ID application.
- Added intent scanning for Android, which improves scanner integration on devices that support it.

### New fixes and improvements in version 2.3.3.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.
- Fixed an issue that striped non-GS1 symbology values when scanning.

## Version 2.3.2.0

### New features introduced in version 2.3.2.0

This version of the Warehouse Management mobile app introduces the following new features: 

- Added a welcome screen copilot, which provides essential information and helpful tips.
- Added a sound and vibration alert to tell workers when they are scanning too quickly for the system to keep up and therefore need to redo their last scan.
- Reduced whitespace on details cards by 35%.

### New fixes and improvements in version 2.3.2.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.
- Fixed an issue that prevented action buttons from respecting the **Button position** user setting.

## Version 2.2.1.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- For Android devices, Android version 5.0 or higher is now strictly required.
- Improved support for the SOTI MobiControl Mobile Device Management (MDM) system. The managed configuration for the uploaded Warehouse Management APK file is now visible in MobiControl, and it's possible to include a connections JSON string.
- Improved performance for large action lists.
- Enhanced validation of authentication secrets on the **Edit connection** page.
- Fixed an issue on certain Honeywell devices, which was related to using the enter key.
- You can now set the minimum server timeout to one minute.

## Version 2.1.26.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:  

- Increased stability.
- Fixed an issue where non-GS1 barcodes didn't scan correctly on inquiry pages.
- Fixed an issue where connection configurations that used a user-based authentication method could be saved even if values were wrong or missing.

## Version 2.1.25.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:  

- Improved username and password authentication. Now, if the domain name is present in the connection configuration, then you can sign in using only the alias part of the Microsoft Entra ID account username (rather than a complete email address). The app will retrieve the domain name from the connection configuration. You can still sign in using the full email address as the username if you prefer.
- Fixed an issue where a selected value wasn't respected when moving back and forth within detours.
- Fixed an issue where the page would sometimes be rendered incorrectly when the device was in landscape mode and the user had selected to never show the *quantity spinner*.
- The app now moves back to the **Select connection** page if the device code expires (after 15 minutes of inactivity) instead of showing an ambiguous error message.
- Fixed an issue that would prevent the app from being installed on Windows when the package was downloaded from Microsoft App Center.
- Added several accessibility improvements.

## Version 2.1.23.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:  

- Increased stability.
- Added the username/password authentication method.
- Added support for single sign-on (SSO) when using username/password authentication.
- Added support for assigning a default mobile device user for each worker account, which enables automatic sign-in for workers.
- Added a pop-up message to confirm successful sign-out from Microsoft Entra.
- Improved support for Active Directory Federation Services (AD FS), thereby enabling device code flow, username/password, and SSO authentication in Dynamics 365 Finance + Operations (on-premises) environments.
- Fixed a bug that prevented the app from saving manually entered connection settings after previously importing those settings from a file.
- Added support for the new "back" gesture in Android 13.
- White space on the details card now scales better with text zoom.
- Added several accessibility improvements.

## Version 2.1.20.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.
- Fixed an issue with icons not working for Turkish localizations.
- Added temporary support for Windows 10.0.17763.
- Fixed an issue that prevented client telemetry from being sent.

## Version 2.1.19.0

### New features introduced in version 2.1.19.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.
- The wireless network connection screen is now correctly hidden in all contexts.
- Fields on the details card are now sorted by priority.
- The empty confirmation label on the details card is now hidden.
- Translations have been updated.
- Telemetry is now available in China.
- The app can now scan the pipe character (|) correctly as a separator.
- New icons are now provided for action buttons.
- The worklist and inquiry cards now have full text accessibility pop-ups.
- Pressing the escape key while entering vendor batches no longer causes the app to crash.
- The about screen now shows the latest version correctly.  
- The app no longer crashes on Android devices that lack of a preinstalled browser.

## Version 2.1.17.0

### New features introduced in version 2.1.17.0

This version of the Warehouse Management mobile app introduces the following new features:  

- Support for multi-level detour.
- Support for password fields on the custom page.
- A warning message about the deprecation of the certificate and the client's secret.
- Updated and improved the **About** page.

### New fixes and improvements in version 2.1.17.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.
- Fixed the bug that prevented the wireless network connection screen from being hidden.
- Resolved the bug causing accessibility tooltips to appear on Windows unexpectedly.  
- Fixed issues related to configuration mode.
- Resolved the bug that prevents hiding the step instructions screen.
- Corrected a localization bug on the calculator screen, which caused inconsistencies between commas and dots on some locales.

## Version 2.1.15.0

### New features introduced in version 2.1.15.0

This version of the Warehouse Management mobile app introduces the following new features:  

- Wireless network connection strength indicator: Indicates the strength of the wireless network connection and adds a new throttling algorithm to ensure connectivity in unstable networks. It's also possible to log wireless network connection strength measurements among the telemetry data collected in Application Insights.
- Configuration mode: Intended for developers and advanced users, configuration mode provides a deeper understanding of how the app works. It can display and edit the XML code used to build and customize the user interface. For more information about this XML code, see [Inspect details of active Warehouse Management mobile app sessions](work-user-sessions.md).

### New fixes and improvements in version 2.1.15.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:

- Increased stability.
- Fixed an issue that prevented iOS users from signing in using the Device Code authentication method.
- Updated the terms and conditions to address legal compliance issues.
- Updated translations to provide an improved experience for international users.
- Updated labels in all languages to reflect the change from Azure Active Directory to Microsoft Entra ID.
- Updated the receive-returns icon to match the new blind receiving flow, which enhances visual consistency.
- Fixed a bug that opened multiple screens for entering quantity after a scan button was selected from an error dialog.
- Fixed the switching behavior when changing from the default page design to a custom design while running the *Short pick with manual relocation* workflow.
- Fixed a crash issue that could occur when sorting the **Work list** page.

## Version 2.1.14.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:  

- Increased stability.
- Fixed an issue that prevented text from being pasted into the **Work list** page search bar when running on Microsoft Windows.
- Fixed an issue that caused the **Work list** page to sort data incorrectly for some cultures.
- Fixed an issue that caused the default page design to switch to a custom design when a button wasn't placed as the last control.
- Fixed an issue that caused the app to focus on the wrong page element, thereby opening a details page and preventing further scanning.
- Fixed an issue that affected the way submit buttons work when certain accessibility features were enabled.
- Fixed an issue that prevented connections from being removed.
- Added [telemetry](application-insights-monitor-usage-performance.md) that enables the app to log failures to connect to Application Insights.
- Improved localization for some languages.

## Version 2.1.12.0

### New authentication method added in version 2.1.12.0

The Warehouse Management mobile app can now use *device code flow* authentication to connect to Supply Chain Management. This new authentication method simplifies the authentication process because it doesn't require users to manage certificates or client secrets. Learn more in [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md).

### New fixes and improvements in version 2.1.12.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:  

- Fixed an issue that prevented quantity values from being displayed when the quantity spinner was hidden. Now, when the spinner is hidden, the quantity is displayed as read-only, and users can scan or use the numpad to change it.
- The decimal separator shown by the mobile app now matches the culture (language) specified for the user account that the app is using to sign in to Supply Chain Management rather than the culture set for the local device.
- Fixed an issue where the read-only quantity spinner would display an incorrect value after the page was resized.
- Fixed an issue where the compact (small) quantity spinner would initially show an incorrect value.
- Added the ability to collect telemetry data about the wireless network connection strength seen at locations where the app is used (for use with [Application Insights](application-insights-warehousing.md)).
- Added several accessibility improvements.

## Version 2.1.9.0

This version of the Warehouse Management mobile app introduces the following new features, fixes, and improvements:

- Increased stability.
- Improved narration and keyboard navigation for better accessibility.
- The minimum timeout is now three minutes (down from five minutes).
- Added a new color for highlighted fields (available across all themes).
- Improved error message descriptions on the **New Connection** page.
- Fixed an issue that could sometimes result in truncated labels on inquiry cards.
- Increased text margins on the **Details** page to make labels easier to read.

## Version 2.1.6.0

This version of the Warehouse Management mobile app introduces the following new features, fixes, and improvements:

- Added a new setting that lets workers specify the visibility and type of quantity spinner. Workers can choose to hide the spinner; always show the compact, non-scrolling spinner; or let the app select automatically.
- Added a search function to inquiry pages. Workers can now scan or type to search in all the fields and titles on the page.
- On custom pages, the app now focuses on the first non-filled text box instead of the first text box.
- Added a close button on all dialog pop-up pages.
- Added a back button on the **Settings**, **Alphanumeric** input, and **Numpad** pages.
- Fixed an issue where the camera scanner would read an extra unprintable character at the end of specific Code 128 barcodes.
- Improved narration and keyboard navigation for better accessibility.

## Version 2.1.1.0  

### New features introduced in version 2.1.1.0

This version of the Warehouse Management mobile app introduces the following new features:  

- The app is now available for iOS devices.
- This version is compliant with regulations for European Union Data Boundary (EUDB) and sovereign clouds.

### New fixes and improvements in version 2.1.1.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:  

- Increased stability for installations deployed using Microsoft Intune.
- Fixed an issue where the app couldn't connect to the server when running on Android 4.4.
- Fixed an issue where the default sorting option of the **Work list** page would overwrite the sorting query specified on the server.

## Version 2.0.42.0

This version introduces the following new features, fixes, and improvements:

- The user settings and input-helper dialogs now include a back button in the toolbar.
- You can now use a pull-down gesture to close the user settings and photo dialogs.
- Fixed an issue that could occur when confirming a quantity using a unit of measure that is named similarly to the next unit of measure in its sequence group. Previously, this could result in the app assuming the wrong unit of measure, but now it correctly identifies each unit in the sequence.

## Version 2.0.41.0  

### New features introduced in version 2.0.41.0

This version of the Warehouse Management mobile app introduces the following new features:  

- The app is now available for devices running on x86 Android platforms.
- The app now supports managed configuration with Microsoft Intune and other mobile device management (MDM) solutions.
- Although the app isn't available in app stores in China, customers can now download the app from Microsoft App Center and use it together with Dynamics 365 Supply Chain Management environments operated by 21Vianet in China.

### New fixes and improvements in version 2.0.41.0

This version of the Warehouse Management mobile app introduces the following fixes and improvements:  

- Increased stability.
- The **Edit connection** page now includes a **Cancel** button.
- Fixed an issue on the **Alphanumeric input** page. Bar codes are now trimmed correctly when entered on this page.
- Fixed a layout issue on the **Inquiry** page. Inquiry cards now use the correct layout after the device's orientation changes.
- Fixed a sorting issue on the **Work list** page. Work cards are now sorted in the correct direction (ascending or descending) when using the default sorting option.
- Fixed a display issue on the **Edit scanned IDs** dialog pop-up page. The page now displays correctly.
- Fixed a layout issue on the **Login** page. The page now shows its fields correctly after the device's orientation changes.

## Version 2.0.40.0

This version introduces the following new features, fixes, and improvements:

- Increased stability.

## Version 2.0.39.0

This version introduces the following new features, fixes, and improvements:

- Increased stability.
- The fields of the **Custom** page are no longer sorted automatically based on their priority and subpriority settings.  
- The app now uses the priority and subpriority settings for each field to identify the primary field for a page. The primary field is shown in the step header.
- Fixed an issue where the soft keyboard wouldn't hide on Android.
- Fixed an issue where the quantity spinner showed an incorrect correct value on opening in the *movement* flow.
- Fixed an issue where the read-only quantity spinner value wasn't centered correctly.
- Fixed an issue where web pages wouldn't open from the **About** page.
- The *Auto* color theme now takes its default appearance (light or dark) based on the global theme set in the mobile device's operating system.

## Version 2.0.37.0

This version introduces the following new features, fixes, and improvements:

- Added a user setting that lets workers choose where the app displays product photos (in both cards and step headers, only in step headers, or not at all).
- Improved the details card screen layout by reducing the size of the step banner and quantity input spinner, which leaves more room for other content.
- Improved the user interface when running on a Honeywell Thor device.
- Improved full-screen mode (only applies to devices with a hardware keyboard).
- Improved results when sorting details cards and custom pages by priority or subpriority (DataPriority or DisplaySubPriority).
- Added support for more languages.
- Improved stability.
- Improved several images and icons.

## Version 2.0.35.0

This version introduces the following new features, fixes, and improvements:

- Fixed an issue on Android where the application would crash if the **Work List** page was opened when no cards were to be shown.

## Version 2.0.34.0

This version introduces the following new features, fixes, and improvements:

- Improved stability.
- Improved performance.
- Improved the screen layout to allow more space for the details card.
- Added a search function to the **Work List** page. Workers can now scan or type to search in all the fields and titles on the page.
- The list of available connections is now sorted alphabetically.
- Fixed an issue where duplicate cards were shown for items that have multiple inventory statuses at the same location.
- Fixed an issue where the **Large Selection List** page didn't scroll to show the preselected item.
- Fixed the search bar colors on the **Large Selection List** page.
- Fixed an issue where the default button defined in the XML wasn't used as the submit button.
- Fixed an issue where the buttons in the multi-scan and fast validation flows didn't update when new IDs were scanned.
- Added support for more languages.

## Version 2.0.32.0

This version introduces the following new features, fixes, and improvements:

- Improved stability.

## Version 2.0.31.0

This version introduces the following new features, fixes, and improvements:

- Enhanced performance and stability.
- Improved user interface that makes it faster and easier to work with long selection lists. Workers can now search for a list item by name rather than scroll through the full list.
- Fixed an issue where pre-entered values didn't get overwritten when scanning by character.

## Version 2.0.30.0

This version introduces the following new features, fixes, and improvements:

- Improved stability.

## Version 2.0.28.0

This version introduces the following new features, fixes, and improvements:

- Improved stability.
- Introduced the ability to continue scanning even while an error dialog is shown on the screen.
- Added support for ASCII 10 in bar codes.
- Improved the usability of step instruction dialogs.
- Fixed an issue where a blank screen could sometimes be shown.
- Fixed an issue where work lists didn't scroll correctly when running on Microsoft Windows.

## Version 2.0.25.0

This version introduces the following new features, fixes, and improvements:

- Increased performance.
- Increased stability.
- Improved the **Inquiry** page to support longer texts in subheaders.
- Introduced the ability to immediately cancel a flow with a single tap or click (when **Cancel** is the only action available under **More actions**).
- Fixed an issue where focus could sometimes be lost between entry controls on the **Edit connection** page and custom pages.
- Fixed an issue where buttons could sometimes become irresponsive and remain shown as selected when included in a scrolling view.
- Fixed an issue where the wrong layout could sometimes be used on the main page.

## Version 2.0.24.0

This version introduces the following new features, fixes, and improvements:

- Improved scanner pages to enable the scan option on **Details** pages.
- Improved gestures, such as touch/tap screen.
- Improved performance issues for Android.
- Fixed placement of multiple headers to allow more cards to display on the **Inquiry** page.
- Improved scrolling so less distance for scrolling pagination is enabled.
- Added long press to display more text on the **Inquiry** page.
- Fixed missing device ID information for Android.
- Increased stability.
- Optimized the sign-in layout.
- Added swipe-right gesture to close dialog pop-up pages on the number pad, **Details** page, and input pages.

## Version 2.0.22.0

This version introduces the following new features, fixes, and improvements:

- Fixed several crashing issues.
- Fixed an issue where some characters wouldn't be recognized when scanning or typing on the default page.
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
    - User sign in
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

- On some devices, you'll get the following error message when you start the app or begin a task: "Cannot find a suitable view for the specified size." If you see this error message on any of your devices, you must downgrade the Warehouse Management mobile app to version 2.0.6.0 on that device and wait to upgrade until the next version of the app is released.

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
- A change to the sequencing logic for controls ensures smoother scaling across devices. Therefore, there's less need to adjust the scaling of fonts or buttons.
- The default color theme has been changed to *Dark*.
- The missing icon for the disabled submit button has been added in ribbon view.
- Time-out exceptions now take you to the connection page instead of showing an in-line error.
- If no submit action is available (such as **OK**, **Yes**, **Accept**, **Done**, or **Finished**), the submit button will be disabled.
- App stability has been improved.
- There's a fix for security vulnerability [CVE-2021-26701](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-26701).
- **Windows version:** An issue on Windows, where menus were unresponsive after the window was resized, has been fixed.

### Known issue in version 2.0.4.0

The following known issue exists in this version:

- This version has an issue with devices that use Android 4.4. You might experience issues when you use the app on this Android version.
