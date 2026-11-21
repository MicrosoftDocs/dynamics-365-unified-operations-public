---
title: Troubleshoot POS errors when calling headquarters
description: Learn how to diagnose POS messages that a connection to Commerce headquarters couldn't be established, and separate connectivity failures from headquarters errors.
author: jadeliu0319-rgb
ms.date: 11/21/2026
ms.topic: troubleshooting-general
ms.author: jadeliu
ms.reviewer: mirao
ai-usage: ai-assisted
---

# Troubleshoot POS errors when calling headquarters

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to diagnose the point of sale (POS) message "A connection to headquarters could not be established" in Microsoft Dynamics 365 Commerce. It helps you separate a genuine connectivity failure from an application error that Commerce headquarters returns.

## Symptom and scope

When a POS operation runs, POS shows a message that begins with the following text:

`A connection to headquarters could not be established.`

Some variants of the message add that Commerce Scale Unit (CSU) is responding, or that the real-time service might not be running properly or its trusted certificate might be missing or expired.

POS shows this message when a real-time call from CSU to Commerce headquarters fails. The message can wrap an application error that headquarters returns, such as a validation error, a posting error, or an exception from an extension. Therefore, the message isn't conclusive proof of a network outage or a stopped real-time service.

A generic HTTP 500 response, or a similar failure response, isn't a root cause by itself. Always look for the inner headquarters error before you decide on a fix.

This article applies to Store Commerce, Modern POS, and Cloud POS when they connect through CSU to Commerce headquarters.

> [!NOTE]
> Lifecycle Services (LCS) Log Search is available only for the high-availability (HA) production topology. Log Search doesn't include logs from CSU that runs on a self-hosted (store) scale unit or from Hardware station. For these components, use Event Viewer on the computer where the component is installed. For more information, see [Commerce component events for diagnostics and troubleshooting](retail-component-events-diagnostics-troubleshooting.md).

## Decision tree

Follow these steps in order:

1. **Confirm the environment and the operation**: Identify the environment type (production, sandbox, or development) and whether CSU is cloud-hosted or self-hosted. Identify the exact POS operation that failed. For example, completing a customer order.
1. **Record the failure time and context**: Record the failure time in Coordinated Universal Time (UTC), and verify the offset between the local time on the device and UTC. Note the device, the register, and the POS user.
1. **Review the permitted POS and CSU diagnostics**: Use the diagnostics explained in [Commerce component events for diagnostics and troubleshooting](retail-component-events-diagnostics-troubleshooting.md):

    - In Event Viewer, review the **Commerce-ModernPos**, **Commerce-RetailServer**, and **Commerce-LoggingProvider** logs under `Application and Services Logs\\Microsoft\\Dynamics`.
    - For Cloud POS, review the **Console** tab in the browser developer tools (F12).
    - On a CSU where you have Event Viewer access, enable the **Analytic** channel for **Commerce-RetailServer**, and find the incoming request (event 5000).
    - In LCS Log Search, filter by the UTC start and end times, the device ID, the POS user, the POS application session ID (**AppSessionID**), and the POS user session ID (**UserSessionID**).

    Use the **ActivityID** from the event 5000 entry to find every CSU event for the failed request, including the error that the real-time call returned.

1. **Classify the failure**: Treat each of the following scenarios separately:

    - **Genuine connectivity failure**: Other real-time operations also fail. The errors are timeout, DNS, TLS or certificate, authentication, or service-unavailable errors, and no headquarters application error is present. Investigate the connection between CSU and headquarters.
    - **Application failure**: Other real-time operations succeed, and an inner headquarters error shows a validation, posting, or business-rule failure. Fix the data, configuration, or process that the inner error identifies.
    - **Extension failure**: The inner error comes from custom code. Ask the owner of the extension to investigate it, as explained in the [example](#example-an-extension-posts-in-a-closed-fiscal-period).

1. **Escalate if you can't find the inner error**: If the available diagnostics don't show the inner headquarters error, open a support request. Include the correlation identifiers that are listed in [Evidence for support](#evidence-for-support) so that the support team can correlate the request with the headquarters error.

## Example: An extension posts in a closed fiscal period

The following example is a hypothetical scenario:

A retailer adds custom order-processing logic in headquarters. When a store associate completes a customer order in POS, the custom logic attempts a ledger posting that uses a date in a closed fiscal period. Headquarters rejects the posting. POS shows the outer message "A connection to headquarters could not be established," but other real-time operations such as customer search continue to work.

The actionable cause is the posting validation and the extension workflow, not the outer connectivity message. To resolve this kind of issue, follow these steps:

1. Validate the posting date and process that the extension is intended to use.
1. In a safe nonproduction environment, compare the behavior with the extension against standard behavior without the extension.
1. Correct the extension logic or the business process.

> [!IMPORTANT]
> Don't reopen a fiscal period without approval from your finance team. Don't disable production extensions or restart services as a universal fix. These actions don't address the inner error and can cause other problems.

## Capture checklist

If the existing POS and CSU events don't show enough details, capture the CSU events for the failed request while you reproduce the failure. The capture method depends on your topology and access. For more information about these events, see [Commerce component events for diagnostics and troubleshooting](retail-component-events-diagnostics-troubleshooting.md).

1. **Confirm access**: To use Event Viewer, you need access to the computer where the CSU is installed, which is typically a self-hosted (store) scale unit. For a cloud-hosted CSU in the HA production topology, use LCS Log Search instead. If you can use neither method, collect the available POS diagnostics and open a support request.
1. **Start a bounded capture**: In Event Viewer on the CSU computer, enable the **Analytic** channel for **Commerce-RetailServer**, as explained in [Finding incoming Commerce Scale Unit request events in Event Viewer](retail-component-events-diagnostics-troubleshooting.md#finding-incoming-commerce-scale-unit-request-events-in-event-viewer). If you use LCS Log Search, you don't need to enable a log. In both cases, record the start time in UTC.
1. **Reproduce only the failed operation**: Perform only the exact POS-to-headquarters operation that failed. Keep the capture window as short as possible.
1. **Stop the capture**: Record the end time in UTC. In Event Viewer, right-click the **Analytic** node, and then select **Disable log**.
1. **Inspect the request and the error**: Find the event 5000 entry for the incoming request that has the **AppSessionID** and **UserSessionID** of the POS session. Use its **ActivityID** to find every CSU event for the request, including the error that the real-time call returned. In LCS Log Search, filter by the UTC start and end times, the device ID, the **AppSessionID**, and the **UserSessionID**.
1. **Verify the capture**: Confirm that the events contain the failed operation, and not unrelated order or shipping activity. If they don't, repeat the capture.

If the CSU events don't contain the inner headquarters error, or if you can't capture these events in your environment, open a support request. Include the information that's listed in [Evidence for support](#evidence-for-support).

### Headquarters trace

A trace that you capture in headquarters by selecting **Help** > **Trace** records activity in a headquarters user session. It might not capture the real-time call from CSU. Capture this trace only if Support asks for it, and follow the procedure in [Capture a trace](../../fin-ops-core/dev-itpro/perf-test/trace-trace-tutorial.md). That article describes the required permissions, size limits, and how to stop, download, and delete traces.

## Evidence for support

When you open a support request, include the following sanitized information:

- The POS operation that failed.
- The versions of POS, CSU, and headquarters.
- The exact text of the inner error.
- The environment type and the topology, such as a production environment with a cloud-hosted CSU.
- The UTC time window of the failure, along with the verified local-to-UTC offset.
- The **AppSessionID**, **UserSessionID**, **ActivityID**, and any request identifiers.

Redact personal data and payment data before you share any artifact. Share artifacts only through approved Microsoft support channels.

## Validate the decision tree

Use the following scenarios to confirm that you apply the decision tree correctly:

| Scenario | What you observe | Expected result |
| -------- | ---------------- | --------------- |
| Connectivity failure | Several real-time operations fail. CSU events for the **ActivityID** show timeout, DNS, TLS or certificate, authentication, or service-unavailable errors. No headquarters application error is present. | You classify the failure as a genuine connectivity failure and investigate the connection between CSU and headquarters. |
| Application or extension failure | Other real-time operations succeed. CSU events for the **ActivityID**, or a headquarters trace, show an inner validation, posting, or extension error. | You classify the failure as an application or extension failure and fix the cause that the inner error identifies, not the connection. |
| Generic HTTP 500 response only | The failed request shows a generic HTTP 500 response, and you can't find an inner error. | You don't treat the HTTP 500 response as the root cause. You continue to look for the inner error, or you open a support request that includes the correlation identifiers. |

## Related content

- [Commerce component events for diagnostics and troubleshooting](retail-component-events-diagnostics-troubleshooting.md)
- [Capture a trace](../../fin-ops-core/dev-itpro/perf-test/trace-trace-tutorial.md)
