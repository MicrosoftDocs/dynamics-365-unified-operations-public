---
title: The asset downtime scenario
description: This article describes the asset downtime scenario, which lets you use sensor data to monitor the availability of your assets.
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form: IoTIntCoreScenarioManagement, IoTIntCoreScenarioConfigurationWizardV2, EntAssetObjectProductionStop
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# The anomaly detection scenario

The anomaly detection scenario involves monitoring the behavior of a machine and generating an alert if any abnormal patterns or deviations from the usual behavior are detected. This scenario requires the installation of a sensor on the machine that continuously collects data and sends it to the Azure IoT Hub for analysis. The anomaly detection system analyzes the data in real-time and triggers an alert if it identifies any anomalies or deviations from normal operating conditions. This proactive approach helps to identify potential issues before they escalate into significant problems, enabling timely maintenance or intervention to minimize downtime and optimize machine performance.

## Set up the asset anomaly detection scenario

Follow these steps to set up the *asset anomaly detection* scenario in Supply Chain Management.

1.  Go to **Asset Management &gt; Setup &gt; Sensor Data Intelligence &gt; Scenarios** to open the **Scenarios** page.

2.  In the **Asset anomaly detection** scenario box, select **Configure** to open the setup wizard for this scenario.

3.  On the **Sensors** page, select **New** to add a sensor to the grid. Then set the following fields for it:

    - **Sensor ID** – Enter the ID of the sensor that you're using. (If you're using the Raspberry PI Azure IoT Online Simulator and have set it up as described in [<u>Set up a simulated sensor for testing</u>](https://learn.microsoft.com/en-us/dynamics365/supply-chain/sensor-data-intelligence/sdi-set-up-simulated-sensor), enter *AssetDownTime*.)

    <!-- -->

    - **Sensor description** – Enter a description of the sensor.

4.  Repeat the previous step for each additional sensor that you want to add now. You can come back and add more sensors at any time.

5.  Select **Next**.

6.  On the **Business record mapping** page, in the **Sensors** section, select the record for one of the sensors that you just added.

7.  In the **Business record mapping** section, select **New** to add a row to the grid.

8.  On the new row, set the **Business record** field to the asset that you're using the selected sensor to monitor. (If you're using the demo data, select *AK-101, Air Knife for Line 1*.)

9.  In the **Business record mapping** section, select **New** to add a row to the grid.

10. On the new row, set the **Business record** field to the counter that you're using the selected sensor to monitor. (If you're using the demo data, make sure there is a counter associated with asset *AK-101, Air Knife for Line 1* that can be selected.)

11. Select **Next**.

12. On the **Anomaly detection parameters** page, define parameters that impact the number of notifications that you wish to receive:

- **Sensitivity**: Enter a value between 0 and 99 to set the sensitivity of the anomaly detection. The higher the value, the more sensitive the system will be, which will result in more notifications.

- **Max anomaly ratio:** Enter the maximum number anomaly alerts the sensor will generate per time period, as a factor between 0.01 and 0.5. The higher the value, the more notifications you will receive.

13. Select **Next**.

14. On the **Activate sensors** page, in the grid, select the sensor that you set up, and then select **Activate**. For each activated sensor in the grid, a check mark appears in the **Active** column.

15. Select **Finish**.

## View machine status on the Notifications page

On the **Notifications** page, supervisors can view the notifications that are generated when an anomaly is detected.

To open the **Notification** page, go to **Asset management &gt; Inquiries &gt; Sensor Data Intelligence &gt; Notifications**.

The following illustration shows an example of an anomaly notification.

\[Picture is coming\]

## Include the anomaly detection to the Azure IoT solution 

To enable anomaly detection, you must include the Azure Cognitive Services Anomaly Detector component to the Internet of Things (IoT) solution on your Azure subscription. The following architectural diagram provides an overview of the solution and its components.

![A picture containing text  screenshot  diagram  design Description automatically generated](media/image1.png)

If you have not already deployed the solution,

Sensor Data Intelligence uses data from sensors that are connected to Microsoft Azure. To enable Azure to retrieve data from your sensors and share it with Dynamics 365 Supply Chain Management, you must deploy an Internet of Things (IoT) solution on your Azure subscription. The following architectural diagram provides an overview of the solution and its components.

Sensor Data Intelligence uses data from sensors that are connected to Microsoft Azure. To enable Azure to retrieve data from your sensors and share it with Dynamics 365 Supply Chain Management, you must deploy an Internet of Things (IoT) solution on your Azure subscription. The following architectural diagram provides an overview of the solution and its components.

##  Defining the length of time series used for anomaly detection.

Going to Azure Stream Analytics resource called 'msdyn-iiot-sdi-asset-univariate-anomaly-detection-' and navigate to query.

![](media/image2.png)

![](media/image3.png)

On line 48 the parameters of the SlidingWindow can be adjusted. The SlidingWindow aggregates sensor readings over a fixed period of time, in this example over 1000 seconds. So, 1000 previous sensor readings will be used to identify whether the current sensor reading is an anomaly.

[Sliding Window (Azure Stream Analytics) - Stream Analytics Query \| Microsoft Learn](https://learn.microsoft.com/en-us/stream-analytics-query/sliding-window-azure-stream-analytics)

Increasing this number, in general, can help the Anomaly Detection service to learn the pattern and detect anomalies more accurately.

Keep in mind that the length of time series that is used for anomaly detection should be between 12 and 8640.

[Cognitive Services APIs Reference (microsoft.com)](https://westus2.dev.cognitive.microsoft.com/docs/services/AnomalyDetector/operations/post-timeseries-entire-detect)

## XXX

![image](media/image4.png)

# Transparency note

---

title: Transparency note for \[Feature\]

description: This transparency note provides information about the AI technology used in \[Product\], along with key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

ms.date: \[Date\]

ms.custom:

\- transparency-note

ms.topic: article

author: \[Author\]

ms.author: \[Author\]

ms.reviewer: \[Reviewer\]

---

\# Transparency note for \[Feature\]

This transparency note describes the AI impact of \[Product\]'s \[Feature\] feature.

\#\# What is \[Feature\]?

\[Describe the system in plain English. What type of system is this? What does it do? At a high level, what does the system take as input? What kind of outputs does the system produce?\]

\#\# What are the system's capabilities?

\[Building on the previous question, provide semi-technical, high-level information on how the system offers functionality for various uses.\]

\#\# What is the system's intended use?

\[Explain intended use(s), as identified in your Impact Assessment.\]

\#\# How was \[Feature\] evaluated? What metrics are used to measure performance?

\[Provide evidence of system accuracy and performance as well as a description of the extent to which these results are generalizable across use cases that were not part of the evaluation.\]

\#\# What are the limitations of \[Feature\]? How can users minimize the impact of the \[Feature\] limitations when using the system?

\[See Impact Assessment. Describe the known limitations of the system including uses for which the system was not designed or evaluated. Discuss steps that the user can take to minimize errors and the impact of trade-offs for the user.\]

\#\# What operational factors and settings allow for effective and responsible use of the system?

\[Describe the operational factors and ranges within which the system is expected to perform reliably and safely. List the choices that end users can make (e.g., customization, settings, etc.), with a description of how those choices may impact system behavior in the real world.\]

\#\# See also

\- \[Feature page\](\[Link\])

\[!INCLUDE\[footer-include\](../includes/footer-banner.md)\]
