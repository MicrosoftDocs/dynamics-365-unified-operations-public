---
title: Store commerce hardware station extensibility for Android devices
description: This article describes how to build out store commerce app for Android with hardware station extensibility.
author: anush6121
ms.author: anvenkat
ms.date: 07/31/2024
ms.topic: how-to
ms.reviewer: v-chrgriffin
ms.search.region: global
ms.search.validFrom: 07/01/2020
ms.custom: 
  - bap-template

---

# Support for Android Hardware station extensibility

Beginning release 10.0.41, Store commerce app for Android will support hardware station extensibility. This allows customers to do the following:
- Allow customers to build extensions to support their various hardware station requirements.
- Allow organizations with fiscal integration requirements to use android mobile devices with fiscal printers.
- Allow customers to create their own APK and publish to google play store or google play for business store.

## Steps to build your store commerce app for Android using store commerce mobile SDK.
  
### Pre-requisites:
  Install the .NET Multi-platform App UI development Visual Studio 2022 workload.
  
### Steps
  -  Navigate to the [LCS Shared Asset Library](https://lcs.dynamics.com/V2/SharedAssetLibrary)
  -  Under the Retail Self-service package, download the latest Store Commerce for Android package, starting with version 10.0.41.
  -  Unzip the Store Commerce for Android package and copy the ```packages``` folder to your repository root.
  -  Modify the nuget.config file to include the packages folder as a package source. In the ```<packageSources>``` node, add: ```<add key="Dynamics365Commerce-Android-Dependencies" value="./packages" />```.
  -  Build the Hardware Station samples solution.
  
  