---
title: MSIX SDK Release 1.7 release notes
description: This article provides release notes for version 1.7 of the MSIX SDK. This SDK is available on GitHub.
ms.date: 08/05/2019
ms.topic: release-notes
keywords: windows 10, uwp, msix
ms.custom: 19H1
---

# MSIX SDK 1.7 update

With the SDK release (1.7), we heard the feedback from our partners and added more APIs to provide developers with more options and flexibility in handling MSIX packages.

## Create MSIX package using the MSIX SDK

In this release you can now create an MSIX package using the MSIX SDK for Windows, MacOS and Linux. There are two ways to create a package:

- Use the **makemsix** tool and specify an input directory and the name of the output package.

    ```console
    makemsix.exe pack -d <directory> -p <package> [options]
    ```
    
- Use the `IAppxPackaging` APIs to create a package programmatically. Specifically, you can use `IAppxPackageWriter`, `IAppxPackageWriter3`, `IAppPackageWriterUtf8` and `IAppxPackageWriter3Utf8`. For an example that demonstrates how to use these APIs, see [**PackSample**](https://github.com/microsoft/msix-packaging/tree/master/sample/PackSample). 

## Update to msix.dll

This release adds the following interfaces to msix.dll:

- `IAppxManifestReader4`
- `IAppxPackageWriter`
- `IAppxPackageWriter3`
- `IAppxManifestOptionalPackageInfo`

## UTF8 API Variants

This release adds several new UTF8 API variants for existing API calls. With the inclusion of these new APIs, developers can choose to use the Utf8 variant for string manipulation according to their environment/platform. As with AppxPackaging APIs, the caller is responsible for deallocating the memory used by LPSTR* out parameters.

The following are the new UTF8 interfaces:

- `IAppxPackageWriterUtf8`
- `IAppxPackageWriter3Utf8`
- `IAppxManifestOptionalPackageInfoUtf8`

## Updates to test infrastructure

This release updates the test infrastructure to use [Catch2](https://github.com/catchorg/Catch2). Before this release, the SDK provided three different test implementations:

- PowerShell script for Windows.
- Shell script for Linux and macOS.
- Common shared library for Android and iOS.

This change removes the overhead of adding a test three times by simplifying the test infrastructure to a single implementation.

You can get the latest SDK on GitHub.

<div class="nextstepaction"><p><a class="x-hidden-focus" href="https://github.com/Microsoft/msix-packaging/tree/release_v1.7" data-linktype="external">MSIX SDK on GitHub</a></p></div>
