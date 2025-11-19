

This article explains how merchants can leverage the Asynchronous Payment Notification framework to receive crucial and actionable updates from Adyen, which are then displayed in the Commerce HQ. This system provides the operations team with the necessary visibility to take timely actions based on the received information.
 
Minimum required version
Commerce headquarters: 10.0.46
 
Prerequisites:
##Link your Commerce environment to a Dataverse environment
The payment notification service uses Dataverse. Therefore, to receive payment notifications, you must link your Commerce environment to a corresponding Dataverse environment. Learn more in Connect finance and operations apps with a new Microsoft Dataverse instance and Connect finance and operations apps with an existing Microsoft Dataverse instance.
 
##Required role to complete the setup
Some of the steps require a Commerce headquarters user who is either an administrator or has the Commerce Payment Administrator role assigned to them in Microsoft Power platform.
#Setup
The following setup steps are same as the steps required to enable the Pay by Link capability. So, if you have enabled the Pay by Link feature, then the steps mentioned in the sections "Enable the features required for receiving the payment notifications" and "Create a webhook to receive payment notifications from Adyen" could be skipped as they would already be completed.
##Enable the features required for receiving the payment notifications
To enable payment notifications for pay by link, enable the following features in the Feature management workspace:
•	Enhanced wallet support and payment improvements. Learn more in Wallet payment support.
•	The unified payments experience in POS. Learn more in Check out faster with optimized payment flows.
•	The Payments Notification feature.
 
 
## Create a webhook to receive payment notifications from Adyen
Refer the instructions mentioned in the following link and complete the steps until the section "Test the connection to the payment notification service: https://learn.microsoft.com/en-us/dynamics365/commerce/dev-itpro/pay-by-link-overview#create-a-webhook-to-receive-payment-notifications-from-adyen. 
 
With these steps Dynamics 365 Commerce can receive authorization notifications from Adyen. However, to enable the payments notification service to send other business critical notifications to Commerce HQ navigate to Commerce shared parameters -> Payment notifications form and enable the "Persist payment processor notifications" configuration. 
 
Now to select which notifications should be sent to the Dynamics 365 Commerce, navigate Adyen customer portal and open the webhook created in the above steps. Under the Events section where we previously only selected Authorization, additionally select the business critical events which are actionable for your business. Please refer the below link to learn more about various events that can be sent by Adyen: https://docs.adyen.com/api-explorer/Webhooks/1/overview
 
[Important] It is important to only select the business critical events as notifications volume can quickly grow and consume critical storage space in the Commerce HQ. We recommend start by choosing three to four events such as Capture, Capture_failed, Refund, and Refund_failed. 
 
Once the events are selected, save the changes and test the webhook from Adyen customer portal by selecting the chosen events one by one to ensure the events are received by the Commerce notifications service.
 
Such notifications can be seen in the Commerce HQ in the form named "Payment process notifications" (Retail and Commerce -> Inquiries and reports -> Payment notifications). However, please note that not all the selected events are sent to Commerce HQ, rather some events are just acknowledged and ignored. This is done to prevent overloading the Commerce HQ and Commerce notifications service. The below list shows which events can be saved to the Commerce HQ and which will be ignored. 
 
Let's take a few examples from the below list to understand the expected behavior. 
 
1.	AUTHORIZATION: If you select this event in the Adyen customer portal, then Adyen will send both successful and failed authorizations information as events, irrespective of where these events are generated i.e., payment terminal, e-commerce etc. This could result in thousands of events every minute but these are not actionable because these failures will be visible to the sales associate (using POS) or the customer (using e-commerce site). Thus, the Commerce system ignores all authorizations except the ones related to the Pay by Link which originate from one of the commerce channels.
2.	CAPTURE:  If you select this event in the Adyen customer portal, then like the authorization event, Adyen will send both successful and failed Capture events irrespective of where these events are generated. These would likely also be a large amount and the success events are not actionable and hence ignored. However, any capture that fails then Adyen sends the Capture event with a property named "Success" with value False. These failures are actionable as it means that product has been sold but the payment could not be captured. Thus the operations team could investigate the capture failure and manually recover the payment. 
3.	CAPTURE_FAILURE" Capture_failure event is different from Capture with success value false. In rare cases, it is possible that Adyen sends the Capture notification with Success property as True, but the payment capture still fails due to rejection by the card scheme (learn more here: https://docs.adyen.com/api-explorer/Webhooks/1/post/CAPTURE_FAILED). Thus, such events, if configured from the Adyen portal, are always saved in the Commerce HQ as they are actionable and these should be limited.
4.	
5.	| Webhook Name                                      | Saved to Commerce HQ?                                                   |
6.	|---------------------------------------------------|-------------------------------------------------------------------------|
7.	| AUTHORISATION                                     | No. Only the Pay by Link related authorizations are saved              |
8.	| AUTHORISATION_ADJUSTMENT                          | Partially. Only when the "Success" property of the event is False      |
9.	| AUTORESCUE                                        | Partially. Only when the "Success" property of the event is False      |
10.	| CANCEL_AUTORESCUE                                 | Partially. Only when the "Success" property of the event is False      |
11.	| CANCEL_OR_REFUND                                  | Partially. Only when the "Success" property of the event is False      |
12.	| CANCELLATION                                      | Partially. Only when the "Success" property of the event is False      |
13.	| CAPTURE                                           | Partially. Only when the "Success" property of the event is False      |
14.	| ORDER_CLOSED                                      | Partially. Only when the "Success" property of the event is False      |
15.	| ORDER_OPENED                                      | Partially. Only when the "Success" property of the event is False      |
16.	| POSTPONED_REFUND                                  | Partially. Only when the "Success" property of the event is False      |
17.	| RECURRING_CONTRACT                                | Partially. Only when the "Success" property of the event is False      |
18.	| REFUND                                            | Partially. Only when the "Success" property of the event is False      |
19.	| REFUND_WITH_DATA                                  | Partially. Only when the "Success" property of the event is False      |
20.	| REFUNDED_REVERSED                                 | Partially. Only when the "Success" property of the event is False      |
21.	| VOID_PENDING_REFUND                               | Partially. Only when the "Success" property of the event is False      |
22.	| CAPTURE_FAILED                                    | Yes                                                                     |
23.	| CHARGEBACK                                        | Yes                                                                     |
24.	| CHARGEBACK_REVERSED                               | Yes                                                                     |
25.	| DIRECT_DEBIT_NOTICE_OF_CHANGE_NOTIFICATION        | Yes                                                                     |
26.	| EXPIRE                                            | Yes                                                                     |
27.	| ISSUER_COMMENTS                                   | Yes                                                                     |
28.	| ISSUER_RESPONSE_TIMEFRAME_EXPIRED                 | Yes                                                                     |
29.	| MANUAL_REVIEW_ACCEPT                              | Yes                                                                     |
30.	| MANUAL_REVIEW_REJECT                              | Yes                                                                     |
31.	| NOTIFICATION_OF_CHARGEBACK                        | Yes                                                                     |
32.	| NOTIFICATION_OF_FRAUD                             | Yes                                                                     |
33.	| OFFER_CLOSED                                      | Yes                                                                     |
34.	| PREARBITRATION_LOST                               | Yes                                                                     |
35.	| PREARBITRATION_OPEN                               | Yes                                                                     |
36.	| PREARBITRATION_WON                                | Yes                                                                     |
37.	| REFUND_FAILED                                     | Yes                                                                     |
38.	| REPORT_AVAILABLE                                  | Yes                                                                     |
39.	| REQUEST_FOR_INFORMATION                           | Yes                                                                     |
40.	| SECOND_CHARGEBACK                                 | Yes                                                                     |
41.	| TECHNICAL_CANCEL                                  | Yes                                                                     |
 
#Purge old payment notifications:
To ensure that the old notifications are deleted to save the storage consumed by these notifications and keep the notifications form actionable, the notifications can be either be deleted manually from the "Payment process notifications" form, or deleted automatically via using a batch job named "Purge payment provider notifications data". The batch job allows the user to specify the number of days indicating the notifications older than this value will be deleted.

