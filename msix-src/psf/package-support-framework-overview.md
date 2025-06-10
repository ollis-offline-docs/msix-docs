---
description: The Package Support Framework helps you fix issues that prevent your desktop application from running in an MSIX container.
title: Package Support Framework
ms.date: 05/14/2020
ms.topic: article
keywords: windows 10, uwp, msix
ms.custom: RS5
---

# Package Support Framework Overview

The Package Support Framework (PSF) is an open source kit that helps you apply fixes to your existing desktop application when you don't have access to the source code, so that it can run in an MSIX container. The Package Support Framework helps your application follow the best practices of the modern runtime environment.

Here are some common examples where you can find the Package Support Framework useful:

* Your app can't find some DLLs when launched. You may need to set your current working directory. You can learn about the required current working directory in the original shortcut before you converted to MSIX.
* The app writes into the install folder. You will typically see it by "Access Denied" errors in [Process Monitor](./package-support-framework.md).
* Your app needs to pass parameters to the executable on launch. You can learn more how PSF can help by going [here](psf-launch-apps-with-parameters.md) and learn more about the available configurations [here](https://github.com/microsoft/MSIX-PackageSupportFramework/tree/master/PsfLauncher).

This framework is open source, lightweight, and you can use it to address application issues quickly. It also gives you the opportunity to consult with the community around the globe, and to build on top of the investments of others.

For a step-by-step guide, see [our get started guide](/windows/uwp/porting/package-support-framework).

## Get started using the Package Support Framework
Here are the tools you will need: 

1. [The Package Support Framework](https://github.com/microsoft/MSIX-PackageSupportFramework/releases) 
1. Get [Process Monitor](/sysinternals/downloads/procmon) to identify issues

You can check our [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/) for all the available fixes. If you find one, you can apply it to your package. Our [step-by-step guide](/windows/uwp/porting/package-support-framework) shows you how to do this. It will also show you how to use the Visual Studio debugger to step through your application and verify that the fix is working and that it has resolved the compatibility issue.

If you can't find a runtime fix that addresses your issue, you can [create one](create-package-support-framework.md). To do that, you'll identify which function calls fail when your application runs in an MSIX container. Then, you can create replacement functions that you'd like the runtime manager to call instead. This gives you an opportunity to replace the implementation of a function with behavior that conforms to the rules of the modern runtime environment.

To create the Package Support Framework leverages the [Detours](https://www.microsoft.com/research/project/detours) technology which is an open source framework developed by Microsoft Research (MSR) and helps with API redirection and hooking.

You can also use the Package Support Framework to run scripts to customize an application for the user environment dynamically. For more information, see [this article](run-scripts-with-package-support-framework.md).

### Limitations

The Package Support Framework does not support registry overrides. It is designed to resolve run time issues.

## Data and telemetry

The Package Support Framework includes telemetry that collects usage data and sends it to Microsoft to help improve our products and services. Read Microsoft's [privacy statement to learn more](https://privacy.microsoft.com/privacystatement). However, data will be collected only when both of the following conditions are met:

* The Package Support Framework binaries are used from the [NuGet package](https://www.nuget.org/packages?q=packagesupportframework) on a Windows 10 computer.
* The user has enabled collection of data on the computer.

The NuGet package contains signed binaries and will collect usage data from the computer. Telemetry is not collected when the binaries are built locally by cloning the repo or downloading the binaries directly.
