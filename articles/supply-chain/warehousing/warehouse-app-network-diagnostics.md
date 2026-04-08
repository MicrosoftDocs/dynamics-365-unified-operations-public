---
title: Check Wi-Fi connectivity and performance
description: Learn how to use the network diagnostics tool in the Warehouse Management mobile app. Use it to test your Wi-Fi connection and identify potential issues.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 04/08/2026
ms.custom:
  - bap-template
---

# Check Wi-Fi connectivity and performance

The network diagnostics tool in the Warehouse Management mobile app analyzes the most critical endpoints on your network to quickly identify connectivity problems. Use it as a first step when troubleshooting connection issues. It helps detect common problems such as unreachable networks, DNS resolution failures, and slow connections.

## What the network diagnostics tool does

The tool runs a series of tests against key network endpoints and displays results that help you identify where problems occur. Based on the results, it shows:

- **Wi-Fi network name** — Confirms which network the device is connected to.
- **Connection status** — Indicates whether the device has an active network connection.
- **Connection speed** — The negotiated link speed with the Wi-Fi access point.
- **Signal strength** — Helps identify if the device is too far from an access point or in an area with poor coverage.
- **IP address** — Confirms the device received a valid IP address from the network.
- **Download speed** — Measures actual data throughput, which might differ from the connection speed due to network congestion or interference.

## When to use network diagnostics

Run the diagnostics tool when you encounter any of the following issues:

- The app can't connect to Supply Chain Management.
- Operations are slow or time out.
- Scanning or data submission is unreliable.
- You need to provide network information to the Microsoft support team.

## Run a network diagnostic test

1. Open the Warehouse Management mobile app on the affected device.
1. Open the **Diagnostics** page by using one of the following methods:
    - From the **Welcome** page, select **Set up connection** (or select **Connect** and then **Set up connection**), and then select **Diagnostics**.
    - From the **Main menu**, select **Connection settings**, then **Set up connection**, and then **Diagnostics**.

1. Select **Analyze Wi-Fi**. The **Wi-Fi diagnostics** page opens and shows details about your current Wi-Fi connection.
1. To run deeper analysis, select **Run network diagnostics**. The tool pings critical endpoints to test DNS resolution, reachability, and response times.

## Interpret the results

Use the guidance provided in the following table to identify common issues:

| Result | What it means | Recommended action |
|---|---|---|
| No Wi-Fi network name shown | The device isn't connected to a Wi-Fi network. | Verify Wi-Fi is enabled and the device is in range of an access point. |
| IP address is missing or invalid | The device didn't receive an IP address (DHCP failure). | Check DHCP server availability and network configuration. |
| Low signal strength | The device is too far from the access point or there's interference. | Move the device closer to an access point or check for physical obstructions. |
| Low download speed | Network congestion, interference, or bandwidth limitations. | Check network load and consider dedicated Wi-Fi for warehouse devices. |
| Endpoint ping failures | DNS resolution or network routing issues. | Verify DNS settings and that required endpoints aren't blocked by a firewall. |
