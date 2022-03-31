---
title: Create a Store Commerce extension installer package
description: This topic explains how to create a Store Commerce extension installer package.
author: mugunthanm
ms.date: 03/30/2022
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-30-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Create a Store Commerce extension installer

[!include [banner](../includes/banner.md)]

## Create a Store Commerce extension installer package
This topic explains how to create the extension installer for Store Commerce.

To create the extension installer for Store Commerce extension, follow these steps.
You can find the full code samples in [Store Commerce Extension samples GitHub repo](https://github.com/microsoft/Dynamics365Commerce.InStore)
1.	In Microsoft Visual Studio 2017, create a new console application (.NET Core), and name it StoreCommerce.ExtInstaller.
2.	Edit the .proj file, and change the target framework to the .NET Framework version 4.6.1, as shown in the following XML.
```js
        <Project Sdk="Microsoft.NET.Sdk">
            <PropertyGroup>
                <OutputType>Exe</OutputType>
                <TargetFramework>net461</TargetFramework>
            </PropertyGroup>
        </Project>
```
3.	Delete the Program.cs file that was generated.
4.	Add a reference to the Microsoft.Dynamics.Commerce.Sdk.Installers.StoreCommerce NuGet Package:
    1.	In Solution Explorer, select and hold (or right-click) the project, and then select Manage NuGet packages.
    2.	In the NuGet Package Manager window, on the Browse tab, search for Microsoft.Dynamics.Commerce.Sdk.Installers.StoreCommerce.
    3.	Select the package, and then select Install.
    4.	Select the version that matches your go-live version.
5.	Add a reference to the Store Commerce Extension csproj projects, Commerce runtime and database scripts project extensions:
    1.	In Solution Explorer, select and hold (or right-click) the project, and then select Add > Reference.
    2.	In Reference Manager, on the Projects tab on the left, select the extension project that you created earlier.

Sample code:
```ts
<Project Sdk="Microsoft.NET.Sdk">
	  <Import Project="..\CustomizationPackage.props " />
	  <PropertyGroup>
	    <OutputType>Exe</OutputType>
	    <TargetFramework>net461</TargetFramework>
	  </PropertyGroup>
	  <ItemGroup>
	    <PackageReference Include="Microsoft.Dynamics.Commerce.Sdk.Installers.StoreCommerce" Version="$(CommerceSdkPackagesVersion)" />
	  </ItemGroup>
	  <ItemGroup>
	    <ProjectReference Include="..\CommerceRuntime\Contoso.GasStationSample.CommerceRuntime.csproj">
	      <ReferenceOutputAssembly>false</ReferenceOutputAssembly>
	    </ProjectReference>
	    <ProjectReference Include="..\Pos\Contoso.GasStationSample.Pos.csproj">
	      <ReferenceOutputAssembly>false</ReferenceOutputAssembly>
	    </ProjectReference>
	  </ItemGroup>
	  <ItemGroup>
	    <!-- Settings included in the CommerceRuntimeExtensionSettings item group will be added to the generated CommerceRuntime config file and available at runtime in the CommerceRuntime extension. -->
	    <CommerceRuntimeExtensionSettings Include="ext.Contoso.GasolineItemId">
	      <Value>gasoline</Value>
	    </CommerceRuntimeExtensionSettings>
	  </ItemGroup>
	</Project>
```
6.	Compile and build the project. The output of this project contains the Store Commerce extension installer.
When you press F5 and build the project, the installer will be automatically deployed. 
7.	To manually install the extension, open Windows PowerShell in administrator mode, go to the extension installer folder, and run the install command.

```sh
PS C:\StoreCommerce.ExtInstaller\bin\Debug\net461> .\ StoreCommerce.ExtInstaller.exe install
```
To uninstall the extension, run the uninstall command.
```ps
PS C:\StoreCommerce.ExtInstaller\bin\Debug\net461> .\ StoreCommerce.ExtInstaller.exe uninstall
```
**Before you install the extension installer, install the Store Commerce app.**

8.	After you've finished installing the extension, close Store Commerce if it's running. Then, to load the extension, open Store Commerce by using the Store Commerce icon on the desktop. 
