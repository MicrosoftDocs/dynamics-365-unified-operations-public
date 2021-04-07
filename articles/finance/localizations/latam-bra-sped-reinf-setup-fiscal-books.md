---
# required metadata

title: Set up fiscal books
description: This topic provides information about setting up SPED-Reinf events using Fiscal books in Microsoft Dynamics 365 Finance for Brazil.
author: sndray
manager: AnnBe
ms.date: 01/19/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8.1

---

# Set up fiscal books

The following topic describes the required set up in Fiscal Books module to generate and issue events to the tax authorities. 

## Set up service types

The service type table represents table 06 that the tax authorities have established to classify the services that are provided, based on assignment of labor. A detailed list of available values is available on the SPED website.

1.  Go to **Fiscal books \> Setup \> SPED Reinf \> Service types**.

2.  Select **New**, enter a classification code that has been established by the tax authorities, and enter a description.

	![Service types](media/bra-service-type-setup.png)

After the list of service types is created, the service types must be assigned to service codes. Go to **Inventory management \> Setup \> Fiscal information \> Service code**, and then, for each service, assign the related service type.

**Set up tax classification codes**

Go to **Fiscal books \> Setup \> SPED Reinf \> Tax classification codes** and enter the available classification types.

![Tax classification](media/bra-tax-classification-codes.png)

This information is assigned to the fiscal organization on the **General** FastTab at **Fiscal books \> Setup \> Fiscal organization**.

![Fiscal organization](media/bra-fiscal-organization-setup.png)

## Set up codes explanation suspension

Go to **Fiscal books \> Setup \> SPED Reinf \> Codes explanation suspension**, and set up the codes that are used in event R-1070 when suspension of withholding applies. These codes are assigned at **Fiscal books \> Periodic \> SPED Reinf \> Administrative and judicial process**.

![Explanation codes](media/bra-codes-explanation-suspension.png)

## Set up acquisition type determination

This setup is used to determine the type of agriculture acquisition of incoming fiscal documents and reported in the tag **indAquis** for the event R-2055. 
Go to **Fiscal books > Setup > SPED Reinf > Acquisition of rural production** to determine the classification of fiscal document based on the following criteria:

- **Vendor account**: All, group or table
- **CFOP** : All, group or table
- **Fiscal classification**

## GILRAT and SENAR taxes

Go to **Fiscal books > Setup > SPED Reinf > GILRAT tax codes** or **SENAR tax codes** to identify which sales tax codes are used to represent these taxes. Sales tax code should be defined as Tax type = **Other**. The amount of these taxes are used in the event R-2055 in the tags **vlrRatDescPR** and **vlrSenarDesc**

## Vendor setup

Go to **Accounts payable > Vendors > All vendors > Fiscal information > SPED Reinf > Reinf taxation over payroll**. This new attribute is included to determine the type of taxation because this information is required in event R-2055 in tag **indOpcCP**.

## Set up fiscal books parameters

Go to **Fiscal books \> Setup \> Fiscal books parameters**, and set up the number sequence for events R-2010 and R-2020.

![Fiscal books parameters](media/bra-sped-fiscal-books-parameters.png)

> [!NOTE]
> If the number sequences weren't initialized during the setup checklist for KB installation, you can generate them by using a wizard. To start the wizard, go to **Organization administration \> Number sequences \> Number sequences**, and select **Generate**. You will then be able to configure the related number sequence.

-   **Area:** Fiscal books

-   **Reference:** SPED-Reinf event ID

## SPED-Reinf events

All the information that the SPED-Reinf provides about taxes and contributions in a given assessment period is known as a *movement*. Therefore, every movement can contain one or more events.

To close the transmission of periodic events for a given movement in a specific assessment period, you must send event R-2099, "Closure of periodic event." After the closure event is processed and validated, it's accepted. Acceptance of the closure event finalizes the sum of the calculation bases that are included in the movement. The tax credit can then be calculated, and the DARF can be
generated to collect taxes and contributions that are owed.

If a correction or new events must be sent for a movement that has already been closed, you must reopen the movement by sending event R-2098, "Reopening of periodic event." After a movement is reopened, you must send a new closing event.

**When there is no movement in the assessment period**

The "no movement" situation for a taxpayer occurs only when there is no information to send to the periodic event group from event R-2010 to event R-2070. In this case, event R-2099, "Closure of periodic event," which provides the information for closure, declares the non-occurrence of transactions in the first assessment period of the year that this situation occurs in. If the "no movement" situation persists in the following years, the taxpayer must repeat this procedure in January of each year.

**Receiving protocol**

The receiving protocol confirms that the information that was sent was successfully delivered and validated to the SPED-Reinf environment. The receiving protocol is the starting point for correcting or deleting a given event, if correction and deletion are allowed.

Every event that is transmitted has a receiving protocol. To correct an event, you must enter the number of the event's receiving protocol.

The amount of time that receiving protocols are kept in the government database isn't defined. Therefore, as a precaution, it's important that the taxpayer retain them, because they provide proof that the ancillary tax obligation has been delivered and met.

> [!NOTE]
> The delivery protocol is transient information that provides proof that the event has been transmitted, and that the appropriate validation will be processed. It doesn't demonstrate compliance with the ancillary obligation.

**Amendment and correction**

The procedure for amending information that is sent to the SPED-Reinf occurs only in events R-1000, "Taxpayer information," and R-1070, "Administrative and
lawsuits table."

In all other cases where the information that was sent must be amended, the procedure for correction or deletion must be used.

**Deletion events**

To exclude events that were approved by the tax authority but incorrectly delivered, you must send event R-9000, "Deletion event." In this event, you must identify the event to delete by filling in the **Event Type** tag (**TpEvento**). You must also fill in **Event Receipt Number** (**NRRECEVT**), which specifies the receipt protocol number of the file that was sent and must be deleted.

**Digital signature**

The digital certificate that is used in the SPED-Reinf must be issued by a certification authority that is accredited by ICP-Brasil.

The digital certificate must belong to the "A" series. Certificates can belong to two series: the "A" series and the "S" series. The "A" series includes the digital signature certificates that are used for web identity confirmation on emails, virtual private networks (VPNs), and electronic documents, with verification of the integrity of its information. The "S" series includes the confidentiality certificates that are used in the encoding of documents, databases, messages, and other sensitive electronic information.

The digital certificate must be of the "A1" or "A3" type. Digital certificates of the "A1" type are stored on the computer that they are used from. Digital certificates of the "A3" type are stored in a tamper-resistant portable device that contains a chip that can do the digital signing. Examples of these devices include smart cards and tokens. These devices are reasonably secure, because every operation is done by the chip on the device, and there is no external access to the private key of the digital certificate.

The digital certificates are required at two moments:

-   **For delivery actions**: Before the request for delivery to the SPED-Reinf is started, the requestor's digital certificate is used to help guarantee the safety of the information traffic on the internet. For the digital certificate to be accepted as a transmitter function, it must be of the e-CNPJ type.

-   **For document signing**: The events can be generated by any fiscal establishment of the legal entity or its proxy. However, the digital subscriber of those events must belong to the main fiscal establishment (headquarters), its legal representative, or an attorney that is granted by means of electronic and non-electronic proxy.

The digital certificates that are used to sign the events that are sent to the SPED-Reinf must be enabled for the digital signature function in accordance with the certificate policy.

The events in the SPED-Reinf must be transmitted by using a valid digital certificate. However, an exception is made for micro and small businesses (ME and EPP) that meet the Simple Nacional criteria and have seven or fewer employees. These businesses can transmit their events by using an access code.


