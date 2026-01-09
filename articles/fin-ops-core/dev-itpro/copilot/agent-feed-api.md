---
title: Agent Feed developer documentation (preview)
description: This article describes how to use Agent Feed in Dynamics 365 Finance and Operations (FnO) to create, update, read, and customize feed items surfaced in Immersive Home.
author: cabeln
ms.author: cabeln
ms.topic: how-to
ms.date: 01/09/2026
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Agent Feed developer documentation

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The guidance applies to FnO version 10.0.47, available in public preview by January 26, 2026. 

This article describes how to use Agent Feed in Dynamics 365 Finance and Operations (FnO) to create, update, read, and customize feed items surfaced in Immersive Home.
Agent Feed enables ERP agents to post actionable feed items through Dataverse Custom APIs, store them natively in FnO, and render them as cards that respect security, ranking, and personalization.

## Overview

Agent Feed provides a platform capability that allows agents and applications to surface contextual work items to users in Immersive Home. Feed items are created by agents, ranked using AI-assisted logic, secured using FnO menu items, and rendered through configurable card providers.

## How to use Agent Feed

### Enable FnO features

In Finance and Operations Feature management, enable the following:

- Immersive Home
- (Preview) Agent Feed for Immersive Home
- (Preview) Custom API Generation

These features are required for both feed rendering and agent‑driven integration.

