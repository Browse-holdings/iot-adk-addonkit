---
external help file: IoTCoreImaging-help.xml
Module Name: IoTCoreImaging
online version: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md
schema: 2.0.0
---

# Import-PSCoreRelease

## SYNOPSIS
Import Powershell Core Release into your workspace and update the wm xml files.

## SYNTAX

```
Import-PSCoreRelease [[-Version] <String>] [<CommonParameters>]
```

## DESCRIPTION
Import Powershell Core Release into your workspace and update the wm xml files.It also adds *OPENSRC_POWERSHELL* feature to the OEMFM.xml file. Add this *OPENSRC_POWERSHELL* to your product OEMInput.xml file. To register this new Powershell for remoting, you will need to update the oemcustomization.cmd file with the following lines for the first boot(run once).

```cmd
    REM Register Powershell Remoting, when using Open Source Powershell
    if exist C:\windows\system32\Powershell\Install-PowerShellRemoting.ps1 (
        set PATH=C:\windows\system32\Powershell;%PATH%
        C:\windows\system32\Powershell\pwsh.exe -ExecutionPolicy Unrestricted -File C:\windows\system32\Powershell\Install-PowerShellRemoting.ps1 >> C:\windows\System32\Winevt\logs\pwsh.txt
    )
```

## EXAMPLES

### EXAMPLE 1
```powershell
    Import-PSCoreRelease 7.0.0
    # Add IOT_POWERSHELL for WinRM
    Add-IoTProductFeature MyProduct All IOT_POWERSHELL
    # Add Open source Powershell
    Add-IoTProductFeature MyProduct All OPENSRC_POWERSHELL -OEM
    (or) addfid MyProduct All OPENSRC_POWERSHELL -OEM
```

## PARAMETERS

### -Version
Optional parameter, Version of Powershell Release from github.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.
For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES
See https://github.com/PowerShell/PowerShell/releases for powershell releases

## RELATED LINKS

[Add-IoTZipPackage](Add-IoTZipPackage.md)
