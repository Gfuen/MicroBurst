This page will document the functions in MicroBurst that rely on the [MSOnline](https://docs.microsoft.com/en-us/powershell/module/msonline) PowerShell module.

# Functions Information
## Get-MSOLDomainInfo.ps1
PS C:\> Import-Module .\Get-MSOLDomainInfo.ps1

PS C:\> Get-Help Get-MSOLDomainInfo

NAME: Get-MSOLDomainInfo

SYNOPSIS: PowerShell function for dumping information from an Office365 domain via an authenticated MSOL connection.

SYNTAX: Get-MSOLDomainInfo [[-folder] <String>] [[-Users] <String>] [[-Groups] <String>] [<CommonParameters>]

DESCRIPTION: The function will dump available information for an Office365 domain out to CSV and txt files in the -folder parameter directory.
    
    -------------------------- EXAMPLE 1 --------------------------
    
    PS C:\>Get-MSOLDomainInfo-folder Test -Verbose
    
    VERBOSE: Getting Domain Contact Info...
    VERBOSE: Getting Domains...
    VERBOSE: 4 Domains were found.
    VERBOSE: Getting Domain Users...
    VERBOSE: 200 Domain Users were found across 4 domains.
    VERBOSE: Getting Domain Groups...
    VERBOSE: 90 Domain Groups were found.
    VERBOSE: Getting Domain Users for each group...
    VERBOSE: Domain Group Users were enumerated for 90 groups.
    VERBOSE: Getting Domain Devices...
    VERBOSE: 22 devices were enumerated.
    VERBOSE: Getting Domain Service Principals...
    VERBOSE: 134 service principals were enumerated.
    VERBOSE: All done.