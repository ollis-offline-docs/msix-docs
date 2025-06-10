---
title: MSIX Packaging Tool release notes
description: This article provides the full history of release notes for different versions of the MSIX Packaging Tool.
ms.date: 04/28/2021
ms.topic: release-notes
keywords: windows 10, uwp, msix, msix packaging tool, insider program
ms.custom: Vibranium
---

# Release notes for the MSIX Packaging Tool

## Version 1.2024.508.0 
- Integration of [Trusted Signing](https://learn.microsoft.com/azure/trusted-signing/overview) to simply package signing process 

## Version 1.2024.405.0 - Public Version
- Enhanced [PSF Support](https://learn.microsoft.com/windows/msix/psf/psf-integration-with-mpt) for Process, Dynamic Library, Environment Variable and Middleware Fixups
- Improved guideline support for utilizing PSF Fixup feature in the tool

## Version 1.2023.1212.0 
- Bug fixes and general improvements

## Version 1.2023.1114.0
- Enhanced support to generate accelerator template with pre-filled fixes in Package Analyzer 
- Added provision for Deletion markers via Registry Legacy in PSF Fixups
- Added support for Package Analyzer Working directory FixUp 

## Version 1.2023.1005.0 
- New [Package Analyzer](https://learn.microsoft.com/windows/msix/packaging-tool/package-analyzer) feature that examines package trace logs and provides remediation support for post-conversions fixups
- Integration of the Package Support Framework (PSF) with MSIX Packaging Tool to support easy application of PSF Fixups

## Version 1.2023.807.0 
- Improvements in entry point detection by MSIX Packaging Tool
- Added notifications for Accelerator fixups that require manual intervention
- Enhanced accessibility features to better support keyboard navigation, voice access, screen reader compatibility and contrast themes
- Improvements in error reporting 
- Bug fixes and general improvements

## Version 1.2023.504.0
- Search for and apply [Accelerators](https://learn.microsoft.com/windows/msix/toolkit/accelerators) during conversion process

## Version 1.2023.319.0 
- MSIX Packaging Tool now supports High Contrast themes of Windows
- Enhanced UI support for local (non-English) languages
- UI changes for improved troubleshooting of the MSIX Packaging Tool driver installation failure

## Version 1.2023.118.0
- Portable Apps can now be packaged as MSIX Packages
- Added ability to edit files within a package using Package Editor
- Apply Trace fixup to your package from within the Package Editor
- Added feature to exclude dependent Windows services from MSIX packages
- MSIX Packaging Tool now monitors child processes during app installation

## Version 1.2022.1101.0
- Fixed a minor UI bug
- Fixed a localization bug

## Version 1.2022.1003.0
- Added support for auto application of PSF FixUps through Command Line Interface. The following PSF FixUps will be supported - FileRedirectionFixup, RegLegacyFixups, DynamicLibraryFixup, and EnvVarFixup
- PSF Scripts are now supported through the Command Line Interface
- Added support for new capabilities to the Package Editor
- Added support for new extensions - SearchPathOverride and InstallLocalVirtualization

## Version 1.2022.802.0
- Fixed a UI bug

## Version 1.2022.718.0
- Added support for null arguments during unattended installs
- Added support for unusual font files included in package
- Added support for start menu shortcuts

## Version 1.2022.512.0
- fixed a localization bug

## Version 1.2022.330.0
- Added driver detection to alert user if their application contains a driver during conversion
- General performance improvements and bug fixes

