---
title: Remote conversion setup in MSIX Packaging Tool
description: This article describes how to set up and connect to a remote machine to run app conversions using the MSIX Packaging Tool.
ms.date: 02/26/2019
ms.topic: install-set-up-deploy
keywords: MSIX, MPT, MSIX Packaging Tool, remote IP
ms.custom: 19H1
---

# Setup instructions for remote machine conversions

Connecting with a remote machine is one option to ensure that you are following the [best practices](prepare-your-environment.md) recommendation for your conversion environment as it can be a cleaner environment than your local machine. There are a few steps that you will need to take before getting started with remote conversions.  

PowerShell remoting must be enabled on the remote machine for secure access. You must also have an administrator account for your remote machine.  If you would like to connect using an IP address, follow the instructions for connecting to a non-domain joined remote machine.

## Connecting to a remote machine in a trusted domain

To enable PowerShell remoting, run the following on the remote machine from a PowerShell window as an **administrator**: 

``` PowerShell
Enable-PSRemoting -Force -SkipNetworkProfileCheck
```

Be sure to sign in to your domain-joined machine using a domain account and not a local account, or you will need to follow the set up instructions for a non-domain joined machine.

### Port configuration

If your remote machine is part of a security group(such as Azure), you must configure your network security rules to reach the MSIX Packaging Tool server.  

#### Azure

1. In your Azure Portal, go to **Networking** > **Add inbound port**
2. Click **Basic**
3. Service field should remain set to **Custom**
4. Set the port number to **1599** (MSIX Packaging Tool default port value – this can be changed in the Settings of the tool) and give the rule a name (e.g. AllowMPTServerInBound)

#### Other infrastructure

Make sure your server port configuration is aligned to the MSIX Packaging Tool port value(MSIX Packaging Tool default port value is 1599 – this can be changed in the Settings of the tool)

## Connecting to a non-domain joined remote machine(includes IP addresses)

For a non-domain joined machine, you must be set up with a certificate to connect over HTTPS.

1. Enable PowerShell remoting and appropriate firewall rules by running the following on the remote machine in a PowerShell window as an **administrator**:

``` PowerShell
Enable-PSRemoting -Force -SkipNetworkProfileCheck  

New-NetFirewallRule -Name "Allow WinRM HTTPS" -DisplayName "WinRM HTTPS" -Enabled  True -Profile Any -Action Allow -Direction Inbound -LocalPort 5986 -Protocol TCP
```
 
2. Generate a self-signed certificate, set WinRM HTTPS configuration, and export the certificate

``` PowerShell
$thumbprint = (New-SelfSignedCertificate -DnsName $env:COMPUTERNAME -CertStoreLocation Cert:\LocalMachine\My -KeyExportPolicy NonExportable).Thumbprint

$command = "winrm create winrm/config/Listener?Address=*+Transport=HTTPS @{Hostname=""$env:computername"";CertificateThumbprint=""$thumbprint""}"

cmd.exe /C $command

Export-Certificate -Cert Cert:\LocalMachine\My\$thumbprint -FilePath <path_to_cer_file>
```

3. On your local machine, copy the exported cert and install it under the Trusted Root store

``` PowerShell
Import-Certificate -FilePath <path> -CertStoreLocation Cert:\LocalMachine\Root
```

### Port configuration 

If your remote machine is part of a security group (such as Azure), you must configure your network security rules to reach the MSIX Packaging Tool server.  

#### Azure

Follow the instructions to [add a custom port](#azure) for the MSIX Packaging Tool, as well as adding a network security rule for WinRM HTTPS

1. In your Azure Portal, go to **Networking** > **Add inbound port**
2. Click **Basic**
3. Set Service field to **WinRM**

#### Other infrastructure 

Make sure your server port configuration is aligned to the MSIX Packaging Tool port value (MSIX Packaging Tool default port value is 1599 – this can be changed in the Settings of the tool)
