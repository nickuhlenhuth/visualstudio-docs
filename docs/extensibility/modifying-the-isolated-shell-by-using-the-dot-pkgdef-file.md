---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file
title: "Modifying the Isolated Shell By Using the .Pkgdef File | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio shell, isolated mode, .pkgdef file"
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: 27
author: "gregvanl"
ms.author: "gregvanl"
manager: ghogen
ms.workload: 
  - "vssdk"
---
# Modifying the Isolated Shell By Using the .Pkgdef File
The .pkgdef file supports settings that you can use to customize an isolated shell application. It specifies values that are created when an application is installed on a computer and that are referenced by the Visual Studio shell when it starts the application. The settings are organized in the file based on the applicable registry keys.  
  
> [!WARNING]
>  Note that .pkgdef files that are not declared in the .vsixmanifest file of the VSPackage are not scanned when Visual Studio starts.  
  
 The .pkgdef file contains sections that are each identified by a key, either `[$RootKey$]` or `[$RootKey$\`*subkey*`]`, where $RootKey$ is the root key for the application.  
  
 Each section contains name/value pairs that have the following format: `"`*ValueName*`"=`*Value*.  
  
 Values are either a string that is enclosed in quotes, or a 32-bit integer that is represented as a dword. Values have the following constraints:  
  
-   All dword values are in hexadecimal format, for example `dword:00000001`.  
  
     For boolean values, 1 represents true, and 0 represents false.  
  
-   All GUID strings are in registry format, for example, `"{00000000-0000-0000-0000-000000000000}"`.  
  
-   All localizable resource identifiers have the form "@*resourceID*" or "#*resourceID*", where *resourceID* is the resource identifier in the application UI package, for example, `"@102"`. The application UI package is the package that is referenced in the AppLocalizationPackage setting.  
  
 For example,  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 You can add comments to the .pkgdef file. A single-line comment has two slashes as the first two characters.  
  
 For a list of the substitution strings, see [Substitution Strings Used in .Pkgdef and .Pkgundef Files](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
 The following sections describe specific registry values that affect the behavior of the Visual Studio shell in isolated mode. You can also define additional registry values for the application in this file.  
  
> [!NOTE]
>  If a setting is not provided in the .pkgdef file, then no corresponding entry is made in the registry.  
  
## Settings  
 The following table describes the values defined under [$RootKey$].  
  
|Name|Type|Value|  
|----------|----------|-----------|  
|AddinsAllowed|dword|True if add-ins can be loaded; otherwise, false.<br /><br /> The default value is true.|  
|AllowsDroppedFilesOnMainWindow|dword|True if the main window can accept dropped files; otherwise, false. Files dropped on the main window are opened by using the <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> method. This is equivalent to opening a document by using the **Open** command on the **File** menu in the application.<br /><br /> The default value is true.|  
|AppIcon|string|The full path of the program icon. This icon appears in the title bar to the left of the application name.<br /><br /> The default value is "$RootFolder$\\*solutionName*.ico", where *solutionName* is the name of the application solution file.|  
|AppLocalizationPackage|string|The GUID of the VSPackage that contains the UI satellite assembly for the application. This VSPackage includes a compiled version of the .vsct file and can include other localized strings. Feature sets and menu command groups can be enabled or disabled by changing the settings in the UI project .vsct file.<br /><br /> The default value is "{*vsUiPackageGuid*}", where *vsUiPackageGuid* is the GUID assigned to the application UI package.|  
|AppName|string|The name of the application. The name appears in the title bar of the application window.<br /><br /> The default value is the name of the application solution file.|  
|CommandLineLogo|string|The banner text when the application is run in a console window. This setting affects only applications that support command-line build operations.<br /><br /> The default value is "*companyName**solutionName* Version 1.0.", where *companyName* is the name of the company provided when Windows was installed, and *solutionName* is the name of the application solution file.|  
|DefaultDebugEngine|string|The GUID of the default debug engine to use for the application.<br /><br /> Note: An empty GUID (all zeros) indicates that the application does not specify a default debug engine. This enables the debugger to select the debug engine to use.<br /><br /> The default value is "{00000000-0000-0000-0000-000000000000}".|  
|DefaultHomePage|string|The default home page URL for the internal Web browser window.<br /><br /> If the **Home page** option is available in the application, then this setting also affects the default state of the option. For more information, see [Web Browser, Environment, Options Dialog Box](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> The default value is the URL of the company provided when Windows was installed.|  
|DefaultProjectsLocation|string|The full path of the default projects folder. For example,<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> If the **Visual Studio projects location** option is available in the application, then this setting also affects the default state of the option. For more information, see [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> The default value is "$MyDocuments$\\*solutionName*", where *solutionName* is the name of the application solution file.|  
|DefaultSearchPage|string|The default search page URL for the internal Web browser window.<br /><br /> If the **Search page** option is available in the application, then this setting also affects the default state of the option. For more information, see [Web Browser, Environment, Options Dialog Box](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> The default value is "http://search.live.com".|  
|DefaultUserFilesFolderRoot|string|The name of the user folder, relative to the current user's My Documents folder.<br /><br /> The default value is the name of the application solution file.|  
|DisableOutputWindow|dword|Indicates whether the isolated shell should treat the output window as disabled.<br /><br /> If this value is set to true, Visual Studio does not display the solution build manager output in the **Output** window and hides the **Show Output window when build starts** check box in the **Projects and Solutions** category in the **Options** dialog box.<br /><br /> The default value is false.|  
|HideMiscellaneousFilesByDefault|dword|True to hide the **Miscellaneous Files** folder by default in **Solution Explorer**; otherwise, false.<br /><br /> If the **Show Miscellaneous files in Solution Explorer** option is available in the application, then this setting also affects the default state of the option. For more information, see [Documents, Environment, Options Dialog Box](../ide/reference/documents-environment-options-dialog-box.md).<br /><br /> The default value is false.|  
|HideSolutionConcept|dword|True to create all projects as stand-alone projects and hide the solution and solution-related commands for stand-alone projects by default; otherwise, false.<br /><br /> If the **Always show solution** option is available in the application, then this setting also affects the default state of the option. For more information, see [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> The default value is false.|  
|NewProjDlgInstalledTemplatesHdr|string|The name for the Visual Studio nstalled templates header in the **Templates** list in the **New Project** dialog box. This is either a string or a localizable resource identifier that is loaded from the application UI package.<br /><br /> The default value is "*solutionName* installed templates", where *solutionName* is the name of the application solution file.|  
|NewProjDlgSlnTreeNodeTitle|string|The name for the **Visual Studio Solutions** node in the **Project types** tree in the **New Project** dialog box. This is either a string or a localizable resource identifier that is loaded from the application UI package.<br /><br /> The default value is "*solutionName* installed templates", where *solutionName* is the name of the application solution file.|  
|SolutionFileCreatorIdentifier|string|The application identifier, which appears as the second line in the solution files that are generated by the application. This line indicates the application that created the file. By convention, this value includes both the name of the application and the application version number. For example,<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> The VSLauncher.exe program, which is the default program for opening a Visual Studio solution file, uses this second line to determine the version of Visual Studio in which to open the solution file. The application would require its own launcher to handle its associated solution files. The launcher could also use this second line in the solution file to determine in which version of the application to open the solution.<br /><br /> Note: The Visual Studio VSLauncher.exe program does not handle .sln files that were created by an isolated shell application.<br /><br /> The default value is "*solutionName* Solution File, Format Version 10.00", where *solutionName* is the name of the application solution file.|  
|SolutionFileExt|string|The solution filename extension for the application. We recommend that you choose a unique filename extension (not.sln).<br /><br /> The default value is "*solutionName*_sln", where *solutionName* is the name of the application solution file.|  
|SplashScreenBitmap|string|The full path of the bitmap file for the splash screen for the application.<br /><br /> The default value is "$RootFolder$\Splash.bmp".|  
|ThisVersionDTECLSID|string|The class identifier (CLSID) of the automation object for the application.<br /><br /> The application automation object is the top-level object for the application in the Visual Studio shell automation model and implements the <xref:EnvDTE._DTE?displayProperty=fullName> interface.<br /><br /> If the application automation object is correctly registered under the HKEY_CLASSES_ROOT\CLSID registry key, then you can use the [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) function to directly create an instance of the application.<br /><br /> The Visual Studio shell uses this CLSID to register the application automation object in the Running Object Table (ROT) by using the ACTIVEOBJECT_WEAK flag. This lets you use the [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)function to retrieve a pointer to a running instance of the application. In addition, if you define a ProgID for the application automation object, then the Visual Studio shell also registers each instance of the application in the ROT by using an item moniker of the form *progID*:*processID*, where *progID* is the ProgID of the application automation object, and *processID* is the process identifier for that instance of the application. For example, if you create a moniker as follows:<br /><br /> `CreateItemMoniker(L"!",`  *instanceString* `, &instanceMoniker)`<br /><br /> where `instanceString` is the *progID*:*processID* string. then you could use `instanceMoniker` with the ROT GetObject function to get the instance.<br /><br /> If the ThisVersionDTECLSID setting is omitted, then the application is not exposed through the Component Object Model (COM). In this case, an instance of the application cannot be created by calling the [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) function and cannot be registered in the ROT.<br /><br /> Each version of a VSPackage must have a different CLSID.<br /><br /> The default value is the GUID that Visual Studio generated for the automation object of the application.|  
|ThisVersionSolutionCLSID|string|The CLSID of the solution object for the application.<br /><br /> The solution automation object contains information about the current open solution in an instance of the application and implements the <xref:EnvDTE._Solution?displayProperty=fullName> interface.<br /><br /> If the solution automation object is correctly registered under the HKEY_CLASSES_ROOT\CLSID registry key, then you can use the [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) function to directly create a solution object for the application.<br /><br /> The Visual Studio shell uses this CLSID to register the solution automation object in the ROT by using the ACTIVEOBJECT_WEAK flag.<br /><br /> If this setting is omitted, then the solution class is not registered with the Component Object Model (COM), and a solution object cannot be created by calling the [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) function and cannot be registered in the ROT.<br /><br /> The default value is a GUID that Visual Studio generated for the solution object of the application.|  
|UserFilesSubFolderName|string|The name of the subfolder under the user's My Documents folder in which the application creates user files and subfolders.<br /><br /> The default value is the name of the application solution file.|  
|UserOptsFileExt|string|The extension for solution user options files for the application.<br /><br /> The default value is the name of the application solution file.|  
  
## Binding Path Settings  
 The [$RootKey$\BindingPaths\\{00000000-0000-0000-0000-000000000000}] key contains the list of directories that the shell checks for assemblies. These directories are added to the list of directories that the shell probes for private assemblies for the application.  
  
 By default, no binding-path entries are added to the .pkgdef file. However, the following subdirectories of the Visual Studio installation directory are automatically added to the application binding-path list in the registry.  
  
-   Common7\IDE\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 To add a directory to the binding path, add an entry of the form "*directoryName*"="", where *directoryName* is an absolute path. For example,  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## Profile Settings  
 The following table describes the values that are defined for each associated package under [$RootKey$\Profile].  
  
|Name|Type|Value|  
|----------|----------|-----------|  
|AutoSaveFile|string|The directory in which the application stores auto-save files.<br /><br /> The default value is "$RootFolder$\Profiles\CurrentSettings.vssettings".|  
  
## Package Satellite DLL Settings  
 The following table describes the values that are defined under [$RootKey$\Packages\\{*vsPackageGuid*}\SatelliteDll] for the satellite DLL of each associated package, where *vsPackageGuid* is the GUID of the associated package.  
  
|Name|Type|Value|  
|----------|----------|-----------|  
|DllName|string|The file name of the DLL.<br /><br /> The default value is "*solutionName*ui.dll", where *solutionName* is the name of the application solution file.|  
|Path|string|The directory that contains the satellite DLL.<br /><br /> The default value is "$PackageFolder$".|  
  
## Package Menu Item Settings  
 The [$RootKey$\Menus] registry key defines UI resource files for the application.  
  
 Menu item values have the form "{*vsUiPackageGuid*}"=", *resourceId*, *versionNumber*", where *vsUiPackageGuid* is the GUID of the application UI package, *resourceId* is the resource identifier of the CTMENU resource that contains the UI elements, and *versionNumber* is a virtual version number for the CTMENU resource. For more information, see [Registering Interop Assembly Command Handlers](../extensibility/internals/registering-interop-assembly-command-handlers.md).  
  
 By default, a menu item entry is created in the .pkgdef file for the application UI package.  
  
 For each package that provides menu items and that is distributed as a part of the application, add a menu item entry for the package.  
  
## See Also  
 [Customizing the Isolated Shell](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgundef Files](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)