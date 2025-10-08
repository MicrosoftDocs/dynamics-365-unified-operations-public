---
title: Customize the Copilot zero prompt experience
description: Learn how to customize the zero prompt experience for Copilot for finance and operations apps.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 10/07/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Customize the zero prompt experience (preview)

[!include [banner](../includes/banner.md)]

The zero prompt experience helps makers enhance user engagement and streamline interactions by presenting the user with customized prompt options to select at the start of the Copilot chat session. By presenting a zero prompt experience adaptive card at the beginning of the chat session, the user receives relevant information and options without the need for more prompts and iterations. The zero prompt experience can be context aware, shown selectively for targeted pages.

The zero prompts are a set of prompts that, when selected, either submit automatically as a prompt to the agent or populate the chat box with the prompt enabling the user to send the prompt to the agent without manually typing the prompt.

> [!IMPORTANT]
> This is a preview feature. Preview features aren't meant for production use and might have restricted functionality. These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2216214), and are available before an official release so customers can get early access and provide feedback.

## Configuring the zero prompt experience
You can configure your custom zero prompt experience in three steps:
1. Create a new topic in the **Copilot for finance and operations apps** agent.
1. Update the trigger node to trigger the topic when the Copilot chat panel opens in the finance and operations apps client.
1. Create an adaptive card with your zero prompts that you send to the user on the triggering event.

### Add a new topic
1. In Copilot Studio, open the **Copilot for finance and operations apps** agent.
1. Select the **Topics** tab.
1. Select **Add a topic** > **From blank**.
1. Change the **Name** of the topic from "Untitled" to something that describes the topic, like "Zero prompt experience".

### Update the trigger
When you open the **Copilot for finance and operations apps** chat experience in the client and start a new session, the control sends the `Microsoft.PowerApps.Copilot.RequestZeroPrompt` event to the agent. This event triggers the zero prompt experience topic.

1. On the **Trigger** node, select **Change trigger** > **A custom client event occurs**.
1. In the **Event name** field, enter `Microsoft.PowerApps.Copilot.RequestZeroPrompt`.
1. If you want to trigger this zero prompt experience only within a specific application context, define the condition using context variables. For example, if you want the zero prompt experience to be specific to the Vendors form, then in the **Condition** section:
   - Set the **Select a variable** field to `Global.PA_Copilot_ServerForm_PageContext.metadataName`.
   - Select **is equal to**.
   - Enter or select a value: **VendTable**.
1. Set the **Priority** value. If you have multiple topics that the zero prompt event triggers, the priority you set for the trigger node determines the order in which they execute.

> [!NOTE]
> You can create multiple topics for zero prompt experiences for the various conditions you want to support. For more information on available application context variables, see [Use application context with Copilot](./copilot-application-context.md).

### Configure the zero prompt experience adaptive card
Below the trigger node, add a **Message** node with an adaptive card that contains your zero prompt experience. This adaptive card contains actions that, on `Action.Submit`, send the zero prompt for that action. For more information on building adaptive cards, see [https://adaptivecards.microsoft.com](https://adaptivecards.microsoft.com).

On the adaptive card, add an object that contains an `Action.Submit` action with the following properties:

| Property | Description |
| -------- | ----------- |
| `scenario` | Defines the action as a Zero Prompt Card. Set this property to "ZeroPromptCard." |
| `skillType` | Defines the behavior of the zero prompt when selected. There are two options:<br> <ul> <li>`MCSMessageSkill`: this skill type takes the prompt in the `value` property and directly sends it to the Copilot Studio agent as a user message.<br><li>`PromptTextSkill`: This skill type takes the prompt in the `value` property and populates the chat input box of the chat panel with the prompt. This skill type is useful when you want more input from the user, such as specifying a record or table name.</ul> |
| `value` | The text of the prompt that you submit as the zero prompt. |
| `source` | The source for the zero prompt. Set this property to "ZeroPrompt." |

For example, the following action, when selected, populates the chat input in the chat panel with the text "How do I set up safety stock for a product?"

```yml
"selectAction": {
  "type": "Action.Submit",
  "data": {
    "scenario": "ZeroPromptCard",
    "skillType": "PromptTextSkill",
    "value": "How do I set up safety stock for a product?",
    "source": "ZeroPrompt",
    "actionSubmitId": "submitAction1"
  }
```

## Zero prompt experience topic example
The following example shows the full topic code for a zero prompt experience. You can try this example in your environment with the following steps:
1. In Copilot Studio, open the **Copilot for finance and operations apps** agent.
1. Select the **Topics** tab, and select **Add a topic**.
1. On the **More** menu, select **Open code editor**.
1. Copy the YML code from the following example, and paste it into the code editor, replacing all code previously in the code editor.
1. Select **Close code editor** and verify you see a **Trigger** and **Message** node showing up in the topic.
1. Provide a name for the topic, then **Save** the topic.
1. **Publish** the agent.
1. Open the finance and operations apps client, and open the Copilot sidecar chat experience. Select the zero prompt options and verify they work as expected.

```yml
kind: AdaptiveDialog
modelDescription: Zero Prompt Experience
beginDialog:
  kind: OnEventActivity
  id: main
  condition: =Global.PA_Copilot_ServerForm_PageContext.metadataName <> "VendTable"
  priority: 200
  eventName: Microsoft.PowerApps.Copilot.RequestZeroPrompt
  actions:
    - kind: SendActivity
      id: sendActivity_qkbCpT
      activity:
        attachments:
          - kind: AdaptiveCardTemplate
            cardContent: |-
              {
                "type": "AdaptiveCard",
                "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
                "version": "1.5",
                "body": [
                  {
                    "type": "ColumnSet",
                    "id": "ms-platform-zpe-columnsetheader-dc291457-0726-4472-9264-ab644fe9b13e",
                    "columns": [
                      {
                        "type": "Column",
                        "items": [
                          {
                            "type": "TextBlock",
                            "wrap": true,
                            "text": "Hello!"
                          },
                          {
                            "type": "TextBlock",
                            "wrap": true,
                            "text": "Welcome to the Zero Prompt Experience",
                            "id": "ms-platform-zpe-header-74453ffe-b4e3-4c81-9a6c-5c03dc4a3661",
                            "spacing": "Small"
                          }
                        ],
                        "width": "stretch"
                      }
                    ]
                  },
                  {
                    "type": "Container",
                    "id": "ms-platform-zpe-actionscontainer-d44c003a-b977-4e0b-a3fc-f8d30d60110d",
                    "showBorder": true,
                    "roundedCorners": true,
                    "selectAction": {
                      "type": "Action.Submit",
                      "data": {
                        "scenario": "ZeroPromptCard",
                        "skillType": "PromptTextSkill",
                        "value": "How do I set up safety stock for a product?",
                        "source": "ZeroPrompt",
                        "actionSubmitId": "submitAction1"
                      }
                    },
                    "items": [
                      {
                        "type": "ColumnSet",
                        "columns": [
                          {
                            "type": "Column",
                            "width": "auto",
                            "items": [
                              {
                                "type": "Image",
                                "url": "data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHZpZXdCb3g9IjAgMCAyMCAyMCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4NCjxwYXRoIGQ9Ik0zLjUgNEMyLjY3MTU3IDQgMiA0LjY3MTU3IDIgNS41VjcuNUMyIDguMzI4NDMgMi42NzE1NyA5IDMuNSA5SDUuNUM2LjMyODQzIDkgNyA4LjMyODQzIDcgNy41VjUuNUM3IDQuNjcxNTcgNi4zMjg0MyA0IDUuNSA0SDMuNVpNMyA1LjVDMyA1LjIyMzg2IDMuMjIzODYgNSAzLjUgNUg1LjVDNS43NzYxNCA1IDYgNS4yMjM4NiA2IDUuNVY3LjVDNiA3Ljc3NjE0IDUuNzc2MTQgOCA1LjUgOEgzLjVDMy4yMjM4NiA4IDMgNy43NzYxNCAzIDcuNVY1LjVaTTkuNSA1QzkuMjIzODYgNSA5IDUuMjIzODYgOSA1LjVDOSA1Ljc3NjE0IDkuMjIzODYgNiA5LjUgNkgxNy41QzE3Ljc3NjEgNiAxOCA1Ljc3NjE0IDE4IDUuNUMxOCA1LjIyMzg2IDE3Ljc3NjEgNSAxNy41IDVIOS41Wk05LjUgN0M5LjIyMzg2IDcgOSA3LjIyMzg2IDkgNy41QzkgNy43NzYxNCA5LjIyMzg2IDggOS41IDhIMTUuNUMxNS43NzYxIDggMTYgNy43NzYxNCAxNiA3LjVDMTYgNy4yMjM4NiAxNS43NzYxIDcgMTUuNSA3SDkuNVpNMy41IDExQzIuNjcxNTcgMTEgMiAxMS42NzE2IDIgMTIuNVYxNC41QzIgMTUuMzI4NCAyLjY3MTU3IDE2IDMuNSAxNkg1LjVDNi4zMjg0MyAxNiA3IDE1LjMyODQgNyAxNC41VjEyLjVDNyAxMS42NzE2IDYuMzI4NDMgMTEgNS41IDExSDMuNVpNMyAxMi41QzMgMTIuMjIzOSAzLjIyMzg2IDEyIDMuNSAxMkg1LjVDNS43NzYxNCAxMiA2IDEyLjIyMzkgNiAxMi41VjE0LjVDNiAxNC43NzYxIDUuNzc2MTQgMTUgNS41IDE1SDMuNUMzLjIyMzg2IDE1IDMgMTQuNzc2MSAzIDE0LjVWMTIuNVpNOS41IDEyQzkuMjIzODYgMTIgOSAxMi4yMjM5IDkgMTIuNUM5IDEyLjc3NjEgOS4yMjM4NiAxMyA5LjUgMTNIMTcuNUMxNy43NzYxIDEzIDE4IDEyLjc3NjEgMTggMTIuNUMxOCAxMi4yMjM5IDE3Ljc3NjEgMTIgMTcuNSAxMkg5LjVaTTkuNSAxNEM5LjIyMzg2IDE0IDkgMTQuMjIzOSA5IDE0LjVDOSAxNC43NzYxIDkuMjIzODYgMTUgOS41IDE1SDE1LjVDMTUuNzc2MSAxNSAxNiAxNC43NzYxIDE2IDE0LjVDMTYgMTQuMjIzOSAxNS43NzYxIDE0IDE1LjUgMTRIOS41WiIgZmlsbD0iIzcwNzA3MCIvPg0KPC9zdmc+",
                                "altText": "Exclamation icon"
                              }
                            ]
                          },
                          {
                            "type": "Column",
                            "width": "stretch",
                            "items": [
                              {
                                "type": "TextBlock",
                                "text": "Safety stock",
                                "weight": "Bolder"
                              },
                              {
                                "type": "TextBlock",
                                "text": "How do I set up safety stock for a product?"
                              }
                            ]
                          }
                        ]
                      }
                    ]
                  },
                  {
                    "type": "Container",
                    "id": "ms-platform-zpe-actionscontainer-d44c003a-b977-4e0b-a3fc-f8d30d60110e",
                    "showBorder": true,
                    "roundedCorners": true,
                    "selectAction": {
                      "type": "Action.Submit",
                      "data": {
                        "scenario": "ZeroPromptCard",
                        "skillType": "PromptTextSkill",
                        "value": "How can I troubleshoot live sync errors in dual-write?",
                        "source": "ZeroPrompt",
                        "actionSubmitId": "submitAction2"
                      }
                    },
                    "items": [
                      {
                        "type": "ColumnSet",
                        "columns": [
                          {
                            "type": "Column",
                            "width": "auto",
                            "items": [
                              {
                                "type": "Image",
                                "url": "data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHZpZXdCb3g9IjAgMCAyMCAyMCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4NCjxwYXRoIGQ9Ik0xMCAyQzE0LjQxODMgMiAxOCA1LjU4MTcyIDE4IDEwQzE4IDE0LjQxODMgMTQuNDE4MyAxOCAxMCAxOEM1LjU4MTcyIDE4IDIgMTQuNDE4MyAyIDEwQzIgNS41ODE3MiA1LjU4MTcyIDIgMTAgMlpNMTAgM0M2LjEzNDAxIDMgMyA2LjEzNDAxIDMgMTBDMyAxMy44NjYgNi4xMzQwMSAxNyAxMCAxN0MxMy44NjYgMTcgMTcgMTMuODY2IDE3IDEwQzE3IDYuMTM0MDEgMTMuODY2IDMgMTAgM1pNMTAgMTIuNUMxMC40MTQyIDEyLjUgMTAuNzUgMTIuODM1OCAxMC43NSAxMy4yNUMxMC43NSAxMy42NjQyIDEwLjQxNDIgMTQgMTAgMTRDOS41ODU3OSAxNCA5LjI1IDEzLjY2NDIgOS4yNSAxMy4yNUM5LjI1IDEyLjgzNTggOS41ODU3OSAxMi41IDEwIDEyLjVaTTEwIDZDMTAuMjQ1NSA2IDEwLjQ0OTYgNi4xNzY4OCAxMC40OTE5IDYuNDEwMTJMMTAuNSA2LjVWMTFDMTAuNSAxMS4yNzYxIDEwLjI3NjEgMTEuNSAxMCAxMS41QzkuNzU0NTQgMTEuNSA5LjU1MDM5IDExLjMyMzEgOS41MDgwNiAxMS4wODk5TDkuNSAxMVY2LjVDOS41IDYuMjIzODYgOS43MjM4NiA2IDEwIDZaIiBmaWxsPSIjNzA3MDcwIi8+DQo8L3N2Zz4=",
                                "altText": "Exclamation icon"
                              }
                            ]
                          },
                          {
                            "type": "Column",
                            "width": "stretch",
                            "items": [
                              {
                                "type": "TextBlock",
                                "text": "Troubleshoot errors",
                                "weight": "Bolder"
                              },
                              {
                                "type": "TextBlock",
                                "text": "How can I troubleshoot live sync errors in dual-write?"
                              }
                            ]
                          }
                        ]
                      }
                    ]
                  },
                  {
                    "type": "Container",
                    "id": "ms-platform-zpe-actionscontainer-d44c003a-b977-4e0b-a3fc-f8d30d60110f",
                    "showBorder": true,
                    "roundedCorners": true,
                    "selectAction": {
                      "type": "Action.Submit",
                      "data": {
                        "scenario": "ZeroPromptCard",
                        "skillType": "MCSMessageSkill",
                        "value": "How can I request time off?",
                        "source": "ZeroPrompt",
                        "actionSubmitId": "submitAction3"
                      }
                    },
                    "items": [
                      {
                        "type": "ColumnSet",
                        "columns": [
                          {
                            "type": "Column",
                            "width": "auto",
                            "items": [
                              {
                                "type": "Image",
                                "url": "data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHZpZXdCb3g9IjAgMCAyMCAyMCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4NCjxwYXRoIGQ9Ik0xMCA2LjUwMDEyQzEwIDYuMjIzOTggOS43NzYxNCA2LjAwMDEyIDkuNSA2LjAwMDEyQzkuMjIzODYgNi4wMDAxMiA5IDYuMjIzOTggOSA2LjUwMDEyVjEwLjUwMDFDOSAxMC43NzYzIDkuMjIzODYgMTEuMDAwMSA5LjUgMTEuMDAwMUgxMi41QzEyLjc3NjEgMTEuMDAwMSAxMyAxMC43NzYzIDEzIDEwLjUwMDFDMTMgMTAuMjI0IDEyLjc3NjEgMTAuMDAwMSAxMi41IDEwLjAwMDFIMTBWNi41MDAxMlpNMy4zNTI3MSA3Ljc5OTk4QzIuNTM0ODEgNy4yMjM4MSAyIDYuMjY3ODIgMiA1LjE4NzA1QzIgMy40MzA2NyAzLjQxMzUzIDIgNS4xNjU2MiAyQzYuMjQyNzQgMiA3LjE5MjE4IDIuNTQxNTEgNy43NjMxNCAzLjM2NTAxQzguNDY1NTMgMy4xMjgzIDkuMjE3NzggMyAxMCAzQzEwLjc3OTQgMyAxMS41MjkgMy4xMjczNyAxMi4yMjkyIDMuMzYyNDNDMTIuODAxIDIuNTM5OTcgMTMuNzUyNiAyIDE0LjgzMTEgMkMxNi41ODIzIDIgMTcuOTk5OSAzLjQyMjY4IDE3Ljk5OTkgNS4xNzUxNkMxNy45OTk5IDYuMjU0NzIgMTcuNDYyIDcuMjA4MjkgMTYuNjQxMiA3Ljc4MTU5QzE2Ljg3MzkgOC40Nzg3IDE3IDkuMjI0NjMgMTcgMTBDMTcgMTEuNzUzIDE2LjM1NTYgMTMuMzU1NSAxNS4yOTA4IDE0LjU4MzZMMTYuODUzNiAxNi4xNDYzQzE3LjA0ODggMTYuMzQxNiAxNy4wNDg4IDE2LjY1ODIgMTYuODUzNiAxNi44NTM0QzE2LjY1ODMgMTcuMDQ4NyAxNi4zNDE3IDE3LjA0ODcgMTYuMTQ2NCAxNi44NTM0TDE0LjU4MzcgMTUuMjkwN0MxMy4zNTU2IDE2LjM1NTYgMTEuNzUzMSAxNyAxMCAxN0M4LjI0Njk2IDE3IDYuNjQ0NDQgMTYuMzU1NiA1LjQxNjM4IDE1LjI5MDdMMy44NTM1NiAxNi44NTM2QzMuNjU4MyAxNy4wNDg5IDMuMzQxNzIgMTcuMDQ4OSAzLjE0NjQ1IDE2Ljg1MzZDMi45NTExOSAxNi42NTg0IDIuOTUxMTggMTYuMzQxOCAzLjE0NjQ0IDE2LjE0NjVMNC43MDkyNyAxNC41ODM2QzMuNjQ0NDEgMTMuMzU1NiAzIDExLjc1MyAzIDEwQzMgOS4yMzE0NCAzLjEyMzg2IDguNDkxODEgMy4zNTI3MSA3Ljc5OTk4Wk0zIDUuMTg3MDVDMyA1Ljg0OTE1IDMuMjkwOTggNi40NDE4NiAzLjc1MDcxIDYuODQyODZDNC40MTk0NiA1LjUyMTc0IDUuNDk0ODMgNC40NDEzNiA2LjgxMjIyIDMuNzY2MzJDNi40MTQwOSAzLjI5NjExIDUuODIzMjYgMyA1LjE2NTYyIDNDMy45NzMzNSAzIDMgMy45NzUzOSAzIDUuMTg3MDVaTTE2LjI0MTYgNi44Mjc2NEMxNi43MDYyIDYuNDI4NDEgMTYuOTk5OSA1LjgzNjE2IDE2Ljk5OTkgNS4xNzUxNkMxNi45OTk5IDMuOTcyNzMgMTYuMDI3OCAzIDE0LjgzMTEgM0MxNC4xNzE0IDMgMTMuNTc5NyAzLjI5NTMgMTMuMTgxMyAzLjc2MzAyQzE0LjQ5NjYgNC40MzUyNCAxNS41NzEyIDUuNTExMjggMTYuMjQxNiA2LjgyNzY0Wk00IDEwQzQgMTMuMzEzNyA2LjY4NjI5IDE2IDEwIDE2QzEzLjMxMzcgMTYgMTYgMTMuMzEzNyAxNiAxMEMxNiA2LjY4NjI5IDEzLjMxMzcgNCAxMCA0QzYuNjg2MjkgNCA0IDYuNjg2MjkgNCAxMFoiIGZpbGw9IiM3MDcwNzAiLz4NCjwvc3ZnPg==",
                                "altText": "Exclamation icon"
                              }
                            ]
                          },
                          {
                            "type": "Column",
                            "width": "stretch",
                            "items": [
                              {
                                "type": "TextBlock",
                                "text": "Request time off",
                                "weight": "Bolder"
                              },
                              {
                                "type": "TextBlock",
                                "text": "How can I request time off?"
                              }
                            ]
                          }
                        ]
                      }
                    ]
                  },
                  {
                    "type": "Container",
                    "id": "ms-platform-zpe-collapsed-footer-79fb882f-ec4e-4abd-bc65-8c523849da40",
                    "items": [
                      {
                        "type": "ColumnSet",
                        "columns": [
                          {
                            "type": "Column",
                            "width": "auto",
                            "items": [
                              {
                                "type": "TextBlock",
                                "wrap": true,
                                "text": "This is your ZPE footer",
                                "id": "fsFooterId"
                              }
                            ]
                          }
                        ]
                      }
                    ]
                  }
                ]
              }

inputType: {}
outputType: {}
```
