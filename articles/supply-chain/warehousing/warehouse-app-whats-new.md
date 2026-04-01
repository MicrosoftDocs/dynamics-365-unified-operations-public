---
title: What's new or changed in the Warehouse Management mobile app
description: This article lists the new and changed features for each released version of the Warehouse Management app for Microsoft Dynamics 365 Supply Chain Management.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: whats-new
ms.date: 02/13/2026
ms.custom:
  - bap-template
  - sfi-ropc-nochange
---

# What's new or changed in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This article lists new features, fixes, improvements, and known issues for each released version of the Warehouse Management mobile app for Microsoft Dynamics 365 Supply Chain Management. It lists changes for each version released since the general availability (GA) release of version 4. Notes for older versions are available in [Warehouse Management mobile app release notes archive](warehouse-app-whats-new-archive.md).

## Release notes for version 4.0.39.0

This update includes critical fixes for authentication workflows, significant battery life optimizations, and expanded hardware support across Android, iOS, and Windows.

### New features

- **Scrollable details card** – Added the option to turn on scrolling for details cards so workers can view more information on one screen without collapsing sections. The scrollable details card is designed for larger screens; on smaller devices, the feature might not work as expected. On smaller screens, switching to landscape mode might reduce the available space, which could affect scrolling behavior.

### Improvements

- **Battery consumption** – Optimized background processes and resource management, resulting in an approximate 9% reduction in battery usage during standard operation.
- **Authentication and connectivity** – Resolved a caching issue where the application incorrectly reused legacy connection data. This fix prevents missing connections and the need to restart the app manually.
- **MDM detection** – Improved mobile device management (MDM) detection resilience by extending the polling interval for policy checks.
- **Telemetry** – Corrected a reporting error in connection-performance telemetry. Connection speed and latency data are now accurately measured and logged.
- **Device compatibility** – Relaxed hardware and software requirements to enable installation on a broader range of legacy and modern devices.
- **Windows navigation** – Added support for the Esc key on Windows to facilitate quicker navigation and menu exits.
- **Legacy pages** – Implemented targeted performance enhancements for legacy UI pages to reduce load times and input lag.

### Fixes

- **Entra brokered authentication** – Resolved a critical issue on Android that prevented Microsoft Entra brokered authentication from completing successfully.
- **iOS scanning** – Fixed a focus-management glitch where success notifications (toast messages) prevented the scanner from immediately returning to a ready state on iOS devices.
- **iOS UI layout** – Corrected a layout issue on the **Edit connection** page where the system keyboard obscured action buttons at the bottom of the screen on iOS devices.
- **Step banner** – Fixed a bug where the step banner displayed a generic *Scan or enter here* placeholder instead of the context-specific value defined in the step.
- **Stability** – Resolved an issue within the animation library that caused intermittent application crashes, particularly on older hardware.
- **Blind cycle counting** – Fixed a logic error that caused duplicate error messages to be displayed consecutively.

## Version 4.0.38.0

Version 4.0.38.0 adds the following fixes and improvements:

- Fixed an issue that caused pages to render incorrectly when users navigated from the **Item inquiry** page to a custom page.
- Fixed an issue where the **Back** button didn't clear previously selected data when navigating between **Item inquiry** pages.
- Fixed an issue where some [mobile mass deployment (MDM) solutions](warehouse-app-intune-user-based.md) couldn't push connection settings (such as those specified in the **ConnectionsJson** field in Microsoft Intune) to the app.
- Fixed an issue where browser shortcuts appeared when users scanned a value.
- Improved the diagnostic file collection flow. Users can now share or save the diagnostic file in a local folder, which is useful when using kiosk mode.
- Fixed an issue where users couldn't scan a license plate on the **Confirm** page when running *Movement* flows. Only the last character of the barcode was shown.
- Fixed an issue in the *Movement* flow where a previous value could be shown in the step banner on the wrong step.
- Fixed a visual issue where **Work list** tile headers that contained special characters weren't displayed correctly.

## Version 4.0.37.0

Version 4.0.37.0 adds the following fixes and improvements:

- Fixed an issue when the domain name is present in the connection configuration, user had to enter complete email address.

## Version 4.0.36.0

Version 4.0.36.0 includes the following fixes and improvements:

- Fixed an issue that caused fields on the **Custom legacy** page to display incorrectly.
- Added support for on-premises environments on iOS.
- Fixed an issue where duplicate names in the XML caused connection failures.
- Fixed an issue where the Copilot summary didn't refresh.
- Fixed an issue where popup list item names were parsed incorrectly, causing an error.
- Fixed an issue where spinner values reset incorrectly after an error occurred.
- Fixed an issue where sending multiple requests caused an application error.
- Improved error messages to provide better clarity for users.
- Improved authentication for on-premises environments on Windows. If you experience problems with a previously working on-premises authentication on Windows, edit the connection and set broker No.
- Fixed an issue where the pull-to-refresh gesture on the work list page didn't refresh correctly.  

## Version 4.0.35.0

Version 4.0.35.0 includes the following fixes and improvements:

- Fixed an issue in the Sales picking flow where the corresponding quantity value was selected incorrectly.
  
## Version 4.0.34.0

Version 4.0.34.0 includes the following fixes and improvements:

- Fixed an issue that caused installation failure on Windows devices when using a mobile mass deployment (MDM) solution.

## Version 4.0.33.0

Version 4.0.33.0 includes the following fixes and improvements:

- Corrected the requirements listed on the Google Play store, which previously stated that near-field communication (NFC) and camera hardware were required. You can install and use the app on devices that don't include these features.
- Resolved a calculator issue that caused a process-guide error when users selected the submit button.

## Version 4.0.32.0

Version 4.0.32.0 includes the following fixes and improvements:

- Aligned authentication with Warehouse Management mobile app version 4.0.29.
- Fixed an issue that caused some apps to crash in the previous version.

## Version 4.0.31.0

Version 4.0.31.0 includes the following fixes and improvements:

- Fixed an issue that caused some apps to crash in the previous version.
- Added options to check Wi-Fi status, export HAR files, and view logs.
- The app now sends meaningful Wi-Fi telemetry data to Application Insights.
- Fixed several critical crash scenarios, including a gesture-related crash on older devices.
- Fixed an issue where the *Confirm location* placeholder wasn't visible when scanning with the device camera.
- Fixed a visual issue where the focus indicator on work list cards was invisible in light mode.
- Added a **Diagnostics** button to the main menu to improve accessibility.
- Fixed an issue where losing the internet connection redirected users to the sign-in page instead of the page where the connection was lost.
- Resolved an authentication issue that required users to sign in a second time.

## Version 4.0.30.0

Version 4.0.30.0 includes the following fixes and improvements:

- Fixed an authentication problem on on-premises Windows installations.
- Improved transitions when navigating between pages.
- Fixed an issue where the work list search field wasn't cleared after refreshing the page.
- Fixed an issue where step instructions didn't remember the *Do not show again* selection when two menu items had the same name.
- Improved Wi-Fi diagnostics through better request handling and clearer error reporting.
- Fixed a concurrency-related problem that could cause sign-out failures.
- Fixed an issue on custom legacy pages where fields could appear in the wrong order or show incorrect values after edits.
- Added a loading spinner for long-running sign-out operations.

## Version 4.0.29.0

Version 4.0.29.0 includes the following fixes and improvements:

- Fixed an authentication failure that occurred when multiple connections used the same client ID. The failure showed an incorrect redirect URL.
- Fixed an issue that affected deployment of the app to iOS devices when using a mobile mass deployment (MDM) solution.
- Improved support for [Microsoft Entra Conditional Access](warehouse-app-conditional-access-enable.md).
- Added support for ProGlove devices.
- Added support for [haptic feedback through external wearable devices](warehouse-app-haptic-feedback.md).

## Version 4.0.28.0

Version 4.0.28.0 includes the following fixes and improvements:

- Fixed an issue where pulling down to refresh didn't update the work list cards.
- Enabled brokered authentication for Android, iOS, and Windows, which supports features such as [Microsoft Entra Conditional Access](warehouse-app-conditional-access-enable.md).
- Added an option on Android to use a new redirect URI, which is required for [Microsoft Entra Conditional Access](warehouse-app-conditional-access-enable.md).
- Improved camera-based barcode scanning by adding camera zoom and augmented-reality assisted barcode focusing.
- Fixed problems with hardware keyboard detection.
- Added support for keycode mapping.
- Fixed an issue that prevented nonnumerical placeholders from appearing in the step banner.
- Fixed an issue affecting image setup for product and master variants.
- Corrected case-sensitive redirect URI matching on Android.
- Fixed an issue where entering a large digit in the calculator caused the delete button to move offscreen.
- Improved localization across the app.

## Version 4.0.27.0

Version 4.0.27.0 includes the following fixes and improvements:

- Fixed an issue where pressing Enter on the scanner hardware keyboard didn't submit the value.
- Fixed a bug that added an extra pipe character when submitting a value.
- Fixed an issue where entering a long digit in the calculator caused the backspace to move unexpectedly.
- Implemented security enhancements.
- Fixed a problem where the device token expired one hour after signing in with device code authentication.
- Improved hardware keyboard functionality.
- Fixed an issue where resizing the screen in Windows changed the order of footer action buttons.
- Added the connection name to the worker sign-in page for better usability.
- Fixed an iOS issue where the calculator appeared unexpectedly during the sales picking flow.
- Fixed a crash that occurred when scrolling through a work list with many cards.
- Fixed an issue where signing out as a default user required re-entering the device code for authentication.

## Version 4.0.26.0

Version 4.0.26.0 includes the following fixes and improvements:

- Fixed an issue where old values weren't removed after scanning items from a work list.
- Fixed a bug that caused the page to auto-submit when a worker pressed the physical scan button on a device during a summary step.
- Fixed mobile mass deployment (MDM) property retrieval to handle case differences in `connection.json` files.
- Enhanced Windows security.

## Version 4.0.25.0

Version 4.0.25.0 includes the following fixes and improvements:

- Resolved a rendering issue on the **Item Inquiry** page.
- Fixed a server request timeout that occurred after the quantity spinner component reset incorrectly when navigating between pages.
- Stopped the quantity spinner from flickering when it landed between two values.
- Enhanced diagnostic tools for improved troubleshooting.
- Improved translation quality across the app.
- Refined device code error messages for greater clarity.
- Fixed a synchronization issue between the calculator and quantity spinner when using a comma as the decimal separator.

## Version 4.0.24.0

Version 4.0.24.0 of the Warehouse Management mobile app is the first general availability (GA) release of version 4 for all supported platforms (Microsoft Windows, Google Android, and Apple iOS) in all supported regions. Version 4 introduces many new features and improvements that enhance your warehouse management experience. Learn more at [Migrate the Warehouse Management mobile app from V3 to V4](warehouse-app-migrating-from-v3-v4.md).
