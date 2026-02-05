---
title: Haptic feedback through external wearable devices
description: Learn about how haptic feedback with external wearable devices works with the Warehouse Management mobile app.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 02/05/2026
ms.custom:
  - bap-template
---

# Haptic feedback through external wearable devices

The Warehouse Management mobile can provide haptic feedback through external wearable devices. This capability helps workers stay focused on the task at hand by providing instant, haptic responses without requiring workers to check the mobile device screen. The functionality is hardware-agnostic and supports a growing range of scanning peripherals from multiple manufacturers.

The app can communicate key system responses, such as successful scans or errors, directly through a wearable device using vibration patterns. Workers receive immediate cues while keeping their attention on picking, packing, or movement tasks. Haptic feedback provides the following key benefits:

- **Eyes-on-task productivity** – Workers receive immediate confirmation of a successful action through a tactile pulse, reducing the need to look at the mobile terminal.
- **Immediate error detection** – Distinct vibration patterns notify workers immediately when something is wrong, such as an invalid scan or blocked location.
- **Universal compatibility** – The architecture is hardware-agnostic, ensuring compatibility with a wide range of Bluetooth and tethered scanning hardware.

## How it works

The integration uses the standard configuration features provided by the hardware manufacturer. After pairing a compatible wearable device with the mobile terminal (such as a tablet or handheld), the app recognizes the peripheral and routes feedback signals accordingly. You don't need to configure specific settings within the Warehouse Management mobile app or Supply Chain Management to enable feedback.

## Haptic feedback signals

The app distinguishes between different operational outcomes by sending unique signals to the connected hardware, as outlined in the following table.

| Signal type | Signal description | Signal meaning |
|----|----|----|
| Success | A short, crisp vibration pattern with a green light. | Confirms a successful scan or task completion. |
| Failure or error | A longer or double-pulse vibration pattern with a red light. | Alerts the user to an error, such as an invalid barcode or blocked location. |

## Hardware support

The Warehouse Management mobile app supports any human interface device (HID) or scanning peripheral compatible with the host operating system (Google Android or Microsoft Windows).

Wearable devices from ProGlove are the first to be specifically supported with haptic signaling. The Warehouse Management mobile app automatically recognizes ProGlove devices and routes feedback signals to them through their native setup utility, ProGlove Insight.

The app is built to support a growing ecosystem of smart wearables. Future updates will continue to add support for other hardware partners, freeing you to choose the devices that best fit your operational needs.

## Scenario: hands-free picking

This scenario walks through a typical hands-free picking flow and shows where haptic feedback is triggered during scanning and validation so that workers can confirm success or spot errors without looking at the screen.

1. **Scan** – A worker picks an item and uses a wearable scanner to scan it.
1. **Validate** – The Warehouse Management mobile app processes the scan.
1. **Tactile response** – The app reacts in one of the following ways:
    - If the scanned item matches the expected item ID in the picking list, the wearable vibrates once, and the worker moves to the next pick immediately.
    - If the scanned item doesn't match the expected item ID in the picking list, the wearable pulses twice, notifying the worker to stop and check the screen for instructions.
