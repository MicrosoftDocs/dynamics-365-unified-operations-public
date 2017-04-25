---
# required metadata

title: X++ session run-time functions
description: This topic describes the session run-time functions.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31421
ms.assetid: a83ec18b-cc9e-40e3-ab06-87ff1c972a6a
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ session run-time functions

[!include[banner](../includes/banner.md)]


This topic describes the session run-time functions.

curExt
------

Retrieves the extension that is used for the current company.

    str curExt()

### Return value

The extension for the current company.

### Remarks

Use this method to avoid a call to the server tier. The alternative is the **company** method of the **Application** class, which does call the server tier.

### Example

    static void curExtExample(Args _arg)
    {
            str s;
            // Sets s to the extension of the current company.
            s = curExt();
            print "Current extension is " + s;
    }

## curUserId
Retrieves the nonnumeric ID that represents the current user.

    str curUserId()

### Return value

The nonnumeric ID that represents the current user.

### Example

    static void curUserIdExample(Args _arg)
    {
            str s;
            s = curUserId();
            print "Current user ID is " + s;
    }

## funcName
Retrieves a string that contains the current function context.

    str funcName()

### Return value

The name of the method that is executing this method.

### Remarks

If execution is currently within the member of a table or class, the name of the method is prefixed with the name of that table or class.

### Example

    static void funcNameExample(Args _arg)
    {
            print "Current function context is " + funcName();
    }

## getCurrentPartition
Retrieves the short name of the current partition.

    str getCurrentPartition()

### Return value

The short name of the current partition.

### Remarks

The maximum length of the data partition name that is returned is eight characters.

### Example

The following code example shows calls to, and output from, the **getCurrentPartition** function of the X++ language, and related functions or methods.

    static public void Main(Args _args)  // X++ method.
    {
            int64 iPartition;
            str sPartition;
            SelectableDataArea oSelectableDataArea;  // System ExDT.
            iPartition = getCurrentPartitionRecId();
            sPartition = getcurrentpartition();
            oSelectableDataArea = Global::getCompany( tableNum(BankAccountTable) );
            Global::info( strFmt(
                    "getCurrentPartitionRecId =%1 , getCurrentPartition =%2 , getCompany =%3",
                    iPartition, sPartition, oSelectableDataArea) );
    }
    /**** Pasted from Infolog window:
    Message_@SYS14327 (03:42:38 pm)
    getCurrentPartitionRecId =5637144576 , getCurrentPartition =initial , getCompany =ceu
    ****/

## getCurrentPartitionRecId
Retrieves the **RecId** field of the current partition.

    int64 getCurrentPartitionRecId()

### Return value

The **RecId** field of the current data partition.

### Remarks

To see a code example that relies on the **getCurrentPartitionRecId** function, see [How to: Include a Filter for Partition in Direct Transact-SQL](http://msdn.microsoft.com/library/5ce90a42-e862-464e-90bc-1eb16a8afd1a(AX.60).aspx).

### Example

The following code example shows calls to, and output from, the **getCurrentPartitionRecId** function of the X++ language, and related functions or methods.

    static public void Main(Args _args)  // X++ method.
    {
            int64 iPartition;
            str sPartition;
            SelectableDataArea oSelectableDataArea;  // System ExDT.
            iPartition = getCurrentPartitionRecId();
            sPartition = getcurrentpartition();
            oSelectableDataArea = Global::getCompany( tableNum(BankAccountTable) );
            Global::info( strFmt(
                    "getCurrentPartitionRecId =%1 , getCurrentPartition =%2 , getCompany =%3",
                    iPartition, sPartition, oSelectableDataArea) );
    }
    /**** Pasted from Infolog window:
    Message_@SYS14327 (03:42:38 pm)
    getCurrentPartitionRecId =5637144576 , getCurrentPartition =initial , getCompany =ceu
    ****/

## getPrefix
Retrieves the current execution prefix after successive calls to the **setPrefix** function.

    str getPrefix()

### Return value

The current execution prefix.

### Remarks

The prefix mechanism makes it more straightforward to write precise error messages about the transactions that an application performs. Because a hierarchical display is created in the Infolog, it can be easier to determine where each error came from.

### Example

    static void getPrefixExample(Args _arg)
    {
            setPrefix("Prefix");
            setPrefix("Another prefix");
            print getPrefix();
    }

## sessionId
Retrieves the session number of the current session.

    int sessionId()

### Return value

The numeric ID of the current session.

### Remarks

A session number is assigned when the client is started and connects to Application Object Server (AOS). Every call of this function during the life of the client returns the same integer value. The returned value is compatible with the **SessionID** extended data type. The **contains** methods return information about individual user sessions.

### Example

    static void sessionIdExample(Args _arg)
    {
            int session;
            session = sessionId();
            print "This session ID is number " + int2Str(session);
    }

## prmIsDefault
Determines whether the specified parameter for the current method has the default value.

    int prmIsDefault(anytype argument)

### Parameters

| Parameter | Description            |
|-----------|------------------------|
| Argument  | The parameter to test. |

### Return value

**1** if the default value for the parameter was used; otherwise, **0** (zero).

### Example

    static void prmIsDefaultExample(Args _arg)
    {
            void fn(boolean b = true, int j = 42)
            {
                    if (prmIsDefault(b) == 1)
                    {
                            print "First parameter is using the default value.";
                    }
                    else
                    {
                            print "First parameter is not using the default value.";
                    }
            }
            fn();
            fn(false);
    }

## runAs
Enables the caller to run an X++ method in the security context of another user. This function is most often used with batch processing.

    container runAs(
            str userId,
            int classId,
            str staticMethodName
            [,
            container params,
            str company,
            str language,
            str partition
            ])

### Parameters

| Parameter        | Description                                                                                       |
|------------------|---------------------------------------------------------------------------------------------------|
| userId           | The user to impersonate.                                                                          |
| classId          | The class to invoke in the impersonated session.                                                  |
| staticMethodName | The class method to invoke in the new user context.                                               |
| params           | The parameters to pass to the method; optional.                                                   |
| company          | The company that is selected for the impersonated session; optional.                              |
| language         | The language that is selected for the impersonated session; optional.                             |
| partition        | The partition key of the type that is returned by the **getCurrentPartition** function; optional. |

### Return value

A container that holds the return value or values of the method that is called by the **runAs** function, if any values were returned.

### Remarks

This function makes it possible to run code as another user. This capability presents a security threat. Therefore, this function runs under [Code Access Security](http://msdn.microsoft.com/library/09299e91-5b73-4cf5-a17e-f1f39b6bae76(AX.60).aspx). Calls to this function on the server require permission from the **RunAsPermission** class. Each use of this application programming interface (API) should be threat-modeled. If a security vulnerability is discovered, validate input to this API. The debugger might ignore breakpoints that are located in a method that is called by using the **runAs** function. X++ code that is executed by the **runAs** function must run as Microsoft .NET Framework Common Intermediate Language (CIL). If CIL hasn't been generated for the target static method, an error message indicates that the method isn't found. The **PartitionKey** system type is the exact type of the *partition* parameter. **PartitionKey** is a string that has a maximum length of eight characters.

### Example

The following example calls the **runDueDateEventsForUser** method in the **EventJobDueDate** class. The code runs in the security context of a user. Run this code by applying it to a method in a new class.

    server static public void Main(Args _args)
    {
            RunAsPermission perm;
            UserId runAsUser;
            SysUserInfo userInfo;
            userInfo = SysUserInfo::find();
            runAsUser = userInfo.Id;
            perm = new RunAsPermission(runAsUser);
            perm.assert();
            runAs(runAsUser, classnum(EventJobDueDate), "runDueDateEventsForUser");
            CodeAccessPermission::revertAssert();
    }

## setPrefix
Sets the prefix for the current execution scope.

    int setPrefix(str _prefix)

### Parameters

| Parameter | Description                                 |
|-----------|---------------------------------------------|
| \_prefix  | The prefix for the current execution scope. |

### Return value

**0** if the prefix was set successfully.

### Remarks

The complete prefix for the execution can be fetched by using the **getPrefix** function. When the scope is left, the prefix is automatically reset to the previous level. The prefix mechanism makes it more straightforward to write precise error messages about the transactions that an application performs. For example, the **AA** method calls the **BB** method, and each method calls the **setPrefix** function. Messages that the **BB** method writes to the Infolog appear nested in a hierarchy. When the **BB** method ends, and control returns to the **AA** method, the prefix that was set by the **BB** method isn't attached to subsequent messages.

### Example

    static void setPrefixExample(Args _arg)
    {
            int i;
            i = setPrefix("Prefix");
            print i;
    }


