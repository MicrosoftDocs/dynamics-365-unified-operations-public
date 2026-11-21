---
title: Capture and replay real-time service traces
description: Capture Commerce real-time service calls, inspect their logs, and safely replay a captured call in a suitable nonproduction environment.
author: jadeliu0319-rgb
ms.topic: how-to
ms.date: 11/21/2026
ms.author: jadeliu
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2026-11-21
ai-usage: ai-assisted
---

# Capture and replay real-time service traces

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to capture Microsoft Dynamics 365 Commerce real-time service (RTS) calls, review the captured trace logs, and replay a captured call in a suitable nonproduction environment. It also explains how RTS trace log records differ from the downloadable performance traces that the standard tracing tool creates.

Use these tools to diagnose RTS issues together with Microsoft support or your engineering team. For information about events from other Commerce components, see [Commerce component events for diagnostics and troubleshooting](retail-component-events-diagnostics-troubleshooting.md).

## Before you begin

Review the following considerations before you capture or replay RTS calls:

- Captured records can contain sensitive request and response data. Keep captures short and narrowly scoped.
- Handle any exported diagnostic data securely, and share it only through approved support channels.
- Don't include actual customer records in public examples, such as forum posts or shared documentation.
- Configure trace capture per legal entity. Before you start a capture, switch to the legal entity whose RTS calls you want to capture.
- If you can't access the RTS trace capture or simulator actions, contact your system administrator.

## Capture real-time service calls

To capture RTS calls, follow these steps:

1. In the legal entity where you want to capture RTS calls, go to **Retail and Commerce** > **Retail and Commerce IT** > **Realtime service trace capture**.
1. Select **START TRACE**.
1. Enter the capture duration in seconds. This value must be greater than 0 and can't be more than 900 seconds (15 minutes).
1. To capture only specific calls, expand **Records to include (Optional)**, and enter a value in the **Class name** field, the **Method name** field, or both. These filters are optional.
1. Select **OK** to start the capture.
1. Reproduce the scenario that you want to diagnose before the capture duration ends.

The following screenshot shows a 60-second capture configuration before you select **OK**:

:::image type="content" source="./media/realtime-service-trace-capture.png" alt-text="Screenshot of the RTS trace capture dialog with a 60-second duration, **Start trace** selected, and the optional class and method filters expanded." lightbox="media/realtime-service-trace-capture.png":::

You can't start a new capture while the current legal entity already has an active trace. To change the configuration of an active capture, stop it first, and then start a new capture.

### Stop an active capture

To stop an active capture, follow these steps:

1. Open the **Realtime service trace capture** dialog box.
1. Select **ABORT CURRENT TRACE**.
1. Select **OK**.

## Review captured trace logs

To review captured RTS calls, go to **Retail and Commerce** > **Retail and Commerce IT** > **Realtime service trace logs**. The newest entries appear first. Each record includes the following information:

- The activity ID of the call.
- The time when the call was captured.
- The language and company of the call.
- The class and method that were called.
- The serialized parameters of the request.
- The response that was captured for the call.

The following screenshot shows an empty trace log:

:::image type="content" source="./media/realtime-service-trace-logs.png" alt-text="Screenshot of the RTS trace logs page with an empty grid and the **Open realtime service simulator** and **Clear trace logs** actions." lightbox="./media/realtime-service-trace-logs.png":::

### Clear trace logs

To remove captured records, on the **Realtime service trace logs** page, select **Clear trace logs**. You can't clear trace logs while a capture is active. Stop the active capture first.

## Replay a captured call in a nonproduction environment

In this article, *replay* means running a captured call again by using the **Realtime service simulator**. The simulator actually re-executes the call. It doesn't only display the captured data.

> [!WARNING]
> Replay runs the captured call again. When you set **Commit data changes** to **No**, the database transaction for the call is rolled back after the call runs. However, rollback doesn't guarantee that every external side effect of the call is undone. Keep **Commit data changes** set to **No** for diagnostic replay, use only a suitable nonproduction environment, and coordinate replay with Microsoft support or your engineering team.

The simulator is controlled separately from trace capture. It's designed to be turned off in production environments and allowed in nonproduction environments. If the simulator isn't available in your nonproduction environment, contact Microsoft support. Don't try to work around this restriction.

The following screenshot shows the simulator controls. Its fields are blank because no captured record was selected for this example.

:::image type="content" source="./media/realtime-service-simulator.png" alt-text="Screenshot of the RTS simulator with the **Invoke** action, blank input fields, and **Commit data changes** set to **No**." lightbox="./media/realtime-service-simulator.png":::

To replay a captured call, follow these steps:

1. On the **Realtime service trace logs** page, select the captured record that you want to replay.
1. Select **Open realtime service simulator**. The **Realtime service simulator** page opens, and the **Class name**, **Method name**, **Parameters**, **Company**, and **Language** fields are prefilled from the captured record.
1. Review the prefilled values. The **Class name** and **Method name** fields are required, and the **Parameters** field must contain valid JSON.
1. Make sure that **Commit data changes** is set to **No**.
1. Select **Invoke** to run the call.

If you choose to commit data changes, the simulator shows a warning. After each invocation, the simulator resets **Commit data changes** to **No**.

## Get a downloadable performance trace

RTS trace log records and downloadable performance traces are different artifacts. The RTS trace logs don't replace a performance trace. To get a downloadable execution or performance trace, use the standard tracing tool explained in [Capture a trace](../../fin-ops-core/dev-itpro/perf-test/trace-trace-tutorial.md).

| Artifact | What it contains | Where to get it |
| -------- | ---------------- | --------------- |
| RTS trace log record | The activity ID, capture time, language, company, class, method, serialized parameters, and response of a captured RTS call. | The **Realtime service trace logs** page. |
| Performance trace | An execution trace that you can analyze using Trace parser. | The standard tracing tool that you open by selecting **Help & Support** and then **Trace**. |

> [!NOTE]
> Whether a standard trace captures the execution of a call that you run by selecting **Invoke** in the simulator isn't confirmed for every environment. Before you rely on this approach, confirm with Microsoft support whether it captures the data that you need.

To use the standard tracing tool, you need administrator access. Or, an administrator must assign you the **System tracing user** role. This requirement applies to the standard tracing tool. It isn't a documented requirement for the RTS trace capture or simulator actions.

The following screenshot shows the **Tracing** pane before you enter a trace name or start a trace:

:::image type="content" source="./media/realtime-service-performance-trace.png" alt-text="Screenshot of the Tracing pane with the required **Trace name** field, **Include SQL parameter values** set to **No**, and the **Start trace** and **Captured traces** buttons." lightbox="media/realtime-service-performance-trace.png":::

To capture a performance trace around a replayed call, follow these steps:

1. In a nonproduction environment where the simulator is available, open the captured call in the **Realtime service simulator**, as explained in [Replay a captured call in a nonproduction environment](#replay-a-captured-call-in-a-nonproduction-environment).
1. Ensure **Commit data changes** is set to **No**.
1. On the navigation bar, select **Help & Support**, and then select **Trace**.
1. In the **Trace name** field, enter a name for the trace.
1. Select **Start trace**.
1. In the simulator, select **Invoke**.
1. Select **Stop trace**.
1. Select **Download trace** to store the trace on your local computer, or select **Upload trace** to store it in the cloud for later download.

If you download a trace, you can't make it available for later upload. For more information about trace size limits, uploaded traces, and analysis in Trace parser, see [Capture a trace](../../fin-ops-core/dev-itpro/perf-test/trace-trace-tutorial.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
