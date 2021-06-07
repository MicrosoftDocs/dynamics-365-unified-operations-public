---
title: What's new or changed in Warehouse management app
description: What's new or changed in Warehouse management app
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

# What's new or changed in Warehouse management app

[!include [banner](../includes/banner.md)]

## 2.0.4.0 - General Availability release

- If there are two labels with data that are exactly the same on details card, one will be hidden
- Removed user setting to allow special characters, now on by default and can be disabled with flight
- If submit button is disabled, now shows as disabled in compact arm-held view
- Changed sequencing logic of controls to ensure more smooth scaling across devices, reducing need to adjust font/button scaling
- Default color theme changed to "Dark" when app is first opened 
- Added missing icon for disabled submit button in ribbon view
- Timeout exception will bring you to connection page
- Fixed issue on Windows where menus were unresponsive after resizing window
- If no submit button (OK, Yes, Accept, Done, Finished), submit button will be disabled. 
- Stability fixes
- Fix for CVE-2021-26701

### Known issues
- There is currently a problem with devices using Android 4.4, and you might experience issues using the app on this Android version. The issues are being investigated.


## 2.0.5.0
### Fixed issues

	- Submit button incorrectly enables depending on window size.
	- Slider can't proceed on smaller screens when button size is larger.
	- Four button overly being cut.
	- Keyboard does not support delete button.
	- Brightness issue when keyboard pressed.
	- Various demo data issues.
	- Details page issue for numeric fields.
	- Disappearing on screen keyboard on some devices.
	- Various UI bugs including background color, positioning, etc.
	- Improved UI with Russian language.
	- Fixed various crashes.
	- Calculator re-opening problem.
	- [Android] Android 4.4 crash on start-up. 
	- Client secret not hidden in connection settings setup.
	
### New Features:
	- Long press any text to see it fully.
	- [Android] Reduced minimum scaling to 50%.
	- Improved error message when missing storage permission.
	- New control sequences on certain flows.
  


## 2.0.6.0
### Fixed issues:
	- Demo mode should now have all labels in the device language.
	- Reduce (Hopefully eliminate)  chances of getting the "red screen of death" (Cannot find a suitable view for the specified size)
	- Increase minimum height of work cards (for cases where 3 or fewer fields are configured  to display on work list)
	- Improve margins (fade out) at bottom of details card
	- Gracefully handle invalid XML symbols in XML (for example, be able to display item name with &#x1A; (substitution non-printable symbol)
	- Graceful HTTP error handling (error codes like 503 or similar) when submitting next server request
	- Don't display options list for combo box control automatically, if we also are showing an error
	- Prevent crashing of the app due to DisplayOrientation in UserSettings
	- Display product image on Self-Service environments (lower resolution version); 
		○ File management service does not support Self-service environments for us to display full-sized images;
	- Fix issue with 0 qty short pick
	- Fix crash when multiple identical fields are displayed in details card


### Known (and important) issues :
	- Scanning with USB gun on Windows does not produce consistent results (mixing up scanned symbols)
	- App gets slower over time (especially with work list)
	- [Windows] A couple crashes when navigating with mouse / typing stuff in
