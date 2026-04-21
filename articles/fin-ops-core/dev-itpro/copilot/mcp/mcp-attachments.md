---
title: Attachments for Dynamics 365 ERP agents
description: Guidance for working with attachments to Dynamics 365 ERP records with the Dynamics 365 ERP MCP server
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 4/28/2026

---

# Attachments for Dynamics 365 MCP


## Configure attachments

1. On the **Tools** tab of the agent, select **Add a tool**.
2. In the **Add tool** dialog, select the **Flow** filter, then search for and add the **Add an attachment to a record in ERP** flow.
3. In the **Inputs** section, add the `contentBytes` input:
   - Select the **Add input** action.
   - Select the `contentBytes` input.
   - In the **Fill using** field, select **Custom value**.
   - Click the ellipses button on the **Value** field.
   - In the **Choose a variable** dialog, select the **Formula** tab, and enter the following formula: `First(System.Activity.Attachments).Content`.
   - Select **Insert**.
4. Add the `name` input:
   - Select the **Add input** action.
   - Select the `name` input.
   - In the **Fill using** field, select **Custom value**.
   - Click the ellipses button on the **Value** field.
   - In the **Choose a variable** dialog, select the **Formula** tab, and enter the following formula: `First(System.Activity.Attachments).Name`.
   - Select **Insert**.
5. **Save** the tool.
