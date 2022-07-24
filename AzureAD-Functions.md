This page will document the functions in MicroBurst that rely on the [AzureAD](https://docs.microsoft.com/en-us/powershell/module/azuread) PowerShell module.

# Functions Information

## Get-AzureADDomainInfo
PowerShell function for dumping information from an AzureAD domain via an authenticated AzureAD connection.
### Description:
The function will dump available information for an AzureAD domain out to CSV files in the -folder parameter (or current) directory.
### Usage:
Run to dump unformation about the AzureAD domain.

`PS C:\> Get-AzureADDomainInfo -Verbose`

### Parameters:

* `-folder` -The folder to output to.
* `-Users` -The flag for dumping the list of AzureAD-Users.
* `-Groups` -The flag for dumping the list of AzureAD-Groups. Disable ('N') if you just want to get a user list.
* `Additional Common Parameters eg. such as -Verbose, -Debug, etc ...` - cmdlet supports the common Module parameters which can be further detailed at [Microsoft Cmdlet Common Parameters](https:/go.microsoft.com/fwlink/?LinkID=113216)

### Considerations:
None