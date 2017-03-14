---
# required metadata

title: Data entities - Retail
description: This article provides a list of the data entities that are available for the Retail functionality in Microsoft Dynamics AX.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 20 - 32
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 96223
ms.assetid: f9e602d7-f9e1-4214-8b45-d079bd436f69
ms.search.region: Global
ms.search.industry: Retail
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Retail

This article provides a list of the data entities that are available for the Retail functionality in Microsoft Dynamics AX.

Available data entities
-----------------------

Sequence

Entity name

Area

Entity type

Dependency

Comments

**27.1.001 RET Base setup**

1

Retail device types

Retail

Setup

None

This entity imports the various Retail device types for the point of sale (POS).

2

POS skins

Retail

Setup

None

This entity imports the various skins for the POS.

3

Supported country regions

Retail

Setup

None

This entity imports the supported countries/regions.

**27.1.002 RET Channel - POS Permissions**

4

Permissions

Retail

Setup

None

This entity imports the permissions for the POS.

5

POS permission group

Retail

Setup

None

This entity imports the permission groups.

6

POS operations

Retail

Setup

None

This entity imports the POS operation details.

**27.1.003 RET Channel - POS Images**

7

POS layout images

Retail

Setup

None

This entity imports the layout images for the POS.

**27.4.001 RET Channel - POS Screen**

8

POS button grid

Retail

Setup

None

This entity imports the button grid details for the POS screen.

9

POS button grid buttons

Retail

Setup

None

This entity imports the grid button details for the POS screen.

10

POS screen layouts

Retail

Setup

None

This entity imports the layout information for the POS screens.

11

POS screen layout zones

Retail

Setup

None

This entity imports the screen layout zones for the POS.

12

POS screen layout button grid zones

Retail

Setup

None

This entity imports the button grid layout information for the POS.

13

POS screen layout image zones

Retail

Setup

None

This entity imports the image layouts for the POS.

14

POS screen layout report zones

Retail

Setup

None

This entity imports the report layout for the POS.

**27.4.002 RET - Receipt Profile**

15

Receipt format

Retail

Setup

None

This entity imports the format of the receipts.

16

Receipt profile

Retail

Setup

None

This entity imports the profiles of the receipts.

17

Receipt profile line

Retail

Setup

None

This entity imports the types of lines for each receipt profile line.

**27.4.003 RET - Infocodes**

18

Info codes

Retail

Setup

None

This entity imports the infocodes.

19

Info code groups

Retail

Setup

None

This entity imports the infocode groups.

20

Reference between info code group and info codes

Retail

Setup

None

This entity imports the references between the infocode groups and infocodes.

21

Subcode

Retail

Setup

None

This entity imports the subcodes.

**27.4.004 RET - Payments**

22

Payment methods

Retail

Setup

None

This entity imports the various possible payment methods.

23

Payment card types

Retail

Setup

None

This entity imports the various payment card types.

24

Payment card numbers

Retail

Setup

None

This entity imports the valid payment card numbers for payments.

25

Payment services

Retail

Setup

None

This entity imports the various payment services.

**27.4.005 RET - Sales tax override group**

26

Sales tax overrides

Retail

Setup

None

This entity imports the sales tax code override information.

27

Sales tax override group

Retail

Setup

None

This entity imports the group for the sales tax override codes.

28

Sales tax override group member

Retail

Setup

None

This entity imports the definitions for the sales tax override code groups.

**27.4.006 RET - Trade agreement journal name**

29

Trade agreement journal name

Retail

Setup

None

This entity imports the trade journal name and descriptions.

**27.4.007 RET - Disposition code**

30

Disposition code

Retail

Setup

None

This entity imports the disposition code and descriptions.

**27.4.008 RET - Channel profile**

31

POS functionality profile

Retail

Setup

None

This entity imports the parameters for the various POS functionality profiles.

32

POS visual profile

Retail

Setup

None

This entity imports the parameters for the various POS visual profiles.

**Note:** The following set of information must be manually added from the UI.

Offline profile

Retail

Setup

This data must be entered manually.

Keyboard mapping groups

Retail

Setup

This data must be entered manually.

Hardware profile

Retail

Setup

This data must be entered manually.

RTS profile

Retail

Setup

This data must be entered manually.

Database connection profile

Retail

Setup

This data must be entered manually.

Data sync interval

Retail

Setup

This data must be entered manually.

**27.4.009 RET - Channel master**

33

Retail channel

Retail

Setup

None

This entity imports the channel parameters information and description. You can also use the stores or call centers entity individually.

34

Retail store address book

Retail

Setup

None

This entity imports the address book information for each store.

35

POS registers

Retail

Setup

None

This entity imports the POS parameters information and description.

36

Retail devices

Retail

Setup

None

This entity imports the device information and description for the devices.

**27.4.010 RET - Channel locator**

37

Retail locator groups

Retail

Setup

None

This entity imports the group information of the retail stores.

38

Retail locator group member

Retail

Setup

None

This entity imports the grouping information for the stores.

39

Retail locator group owner

Retail

Setup

None

This entity imports the store group and owner information for the stores.

**27.4.011 RET - Channel master additional setup**

40

Store payment methods

Retail

Setup

None

This entity imports the payment method configuration details for the various payment options.

41

Store payment card setup

Retail

Setup

None

This entity imports the payment card information and setup for the various payment options.

42

Store section

Retail

Setup

None

This entity imports the section configuration details for the stores.

43

Store shelves

Retail

Setup

None

This entity imports the shelving setup for the stores.

**Note:** Manual setup by using the UI is required for channel configuration. The following group isn't a set of entities but information that must be manually created in the UI for channel configuration.

Channel profile

Retail

Setup

This data must be entered manually.

Data sync interval

Retail

Setup

This data must be entered manually.

Channel database

Retail

Setup

This data must be entered manually.

Channel database group

Retail

Setup

This data must be entered manually.

Retail shared parameters

Retail

Setup

This data must be entered manually.

Retail headquarters parameters

Retail

Setup

This data must be entered manually.

**27.4.012 RET - Merchandising – Assortment**

44

Assortment

Retail

Setup

None

This entity imports the assortment ID and description. When you import, open the Microsoft Excel file, and remove any records that have a status of **Draft**.

45

Assortment product lines

Retail

Setup

None

This entity imports the assortment line configuration information.

**27.4.013 RET - Merchandising - Price points**

46

Price point group

Retail

Setup

None

This entity imports the price point group setup information.

47

Price points

Retail

Setup

None

This entity imports the price point setup information.

**27.4.014 RET - Merchandising - Periodic discount**

48

Periodic discount

Retail

Setup

None

This entity imports the discount setup header information.

49

Periodic discount line

Retail

Setup

None

This entity imports the discount line information, together with details about each discount line item.

**27.4.015 RET - Merchandising - Discount price groups**

50

Retail discount price groups

Retail

Setup

None

This entity imports the discount group information.

**27.4.016 RET - Merchandising - Threshold discount**

51

Threshold discount tiers

Retail

Setup

None

This entity imports the threshold parameters for discount offering.

**27.4.017 RET - Merchandising - Mix and match discount**

52

Mix and match line group setup

Retail

Setup

None

This entity imports the mix and match discount group information.

53

Mix and match line groups

Retail

Setup

None

This entity imports the mix and match discount definition information.

**27.4.018 RET - Merchandising - Date intervals**

54

Date intervals

Retail

Setup

None

This entity imports the various date interval definitions for the program.

**27.4.019 RET - Merchandising - Loyalty program**

55

Loyalty program

Retail

Setup

None

This entity imports the names of the various loyalty programs.

56

Loyalty tier

Retail

Setup

None

This entity imports the tier definitions for the loyalty tiers.

57

Loyalty tier price groups

Retail

Setup

None

This entity imports the definition of the loyalty tier price groups.

58

Loyalty schemes

Retail

Setup

None

This entity imports the various loyalty schemes for the loyalty program.

59

Loyalty scheme channels

Retail

Setup

None

This entity imports the various loyalty scheme definitions in the loyalty program.

**27.4.020 RET - Merchandising - Reward points**

60

Loyalty reward points

Retail

Setup

None

This entity imports the Retail loyalty reward points information.

**27.4.021 RET - Merchandising - Loyalty tier rules**

61

Retail loyalty tier rules

Retail

Setup

None

This entity imports the tier rules for the Retail loyalty programs.

**27.4.022 RET - Merchandising - Affiliation**

62

Retail affiliations

Retail

Setup

None

This entity imports the various Retail affiliations.

63

Retail affiliation translations

Retail

Setup

None

This entity imports the language translations for various Retail affiliations.

64

Retail affiliation price groups

Retail

Setup

None

This entity imports the price groups for various Retail affiliations.

**27.4.023 RET - Merchandising - Catalog**

65

Catalog

Retail

Setup

None

This entity imports all the catalog definitions and details.

66

Catalog channels

Retail

Setup

None

This entity imports the catalog channel details.

67

Catalog products

Retail

Setup

None

This entity imports the products in the catalogs.

68

Catalog price groups

Retail

Setup

None

This entity imports the catalog number and price groups relation.

69

Catalog product categories

Retail

Setup

None

This entity imports the catalog product category and hierarchy details.

**27.4.024 RET - Barcodes**

70

Bar code mask

Retail

Setup

None

This entity imports the masking details and information for bar codes.

71

Bar code mask characters

Retail

Setup

None

This entity imports the masking character information and details for bar codes.

72

Bar code mask segment

Retail

Setup

None

This entity imports the masking segment information for bar codes.

73

Barcode setup

Retail

Setup

None

This entity imports the setup parameters for bar codes.

74

Item-Barcode

Retail

Setup

None

This entity imports the bar code information for the items.

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities home page](data-entities.md)

