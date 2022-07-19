This page will document the functions in MicroBurst that rely on the [Az](https://docs.microsoft.com/en-us/powershell/azure/new-azureps-module-az) PowerShell module.

# Functions Information
## Get-AzPasswords
### Description:
This function will collect available credentials from the following services in Azure:
* App Services
    * Connection Strings
    * Publish Profiles
* Storage Accounts
    * Access keys
* Cosmos DB
    * Access Keys
* Container Registries
    * Admin user credentials
* Key Vaults
    * Keys
    * Secrets
    * Certificates
* Automation Accounts
    * Run as Service Principal Account certificates
    * Stored Credentials
* Azure Kubernetes Services
    * Kubeconfig files for clusterUser and clusterAdmin users

### Usage:
Run with all services and all options:

`PS C:\> Get-AzPasswords -ExportCerts Y -ExportKube Y -ModifyPolicies Y -Verbose`

Run with all services:

`PS C:\> Get-AzPasswords -Verbose`

### Parameters:
Each service will have its own parameter (-StorageAccounts Y). By default, all services are set to 'Y', so disable any by setting the parameter to 'N'
* `-Subscription` - If not specified, the function will prompt you for a subscription to use
* `-ModifyPolicies` - Temporarily adds list and get rights for your current user in the key vault access policies
* `-ExportCerts` - Exports the Key Vault certificates to local files
* `-CertificatePassword` - The password used for exporting the automation account run as certificates

### Considerations:
The automation accounts section will create new runbooks in the automation accounts. These should get deleted by the script, but some times that delete fails. Additionally, the job run records will still show up in job logs, so it is a logged action.

If you have contributor rights, modifying the key vault access policies (not very opsec safe) can be a convenient way to access a vault.

***
## Get-AzDomainInfo
### Description:
This function will collect configurations and general information for services in Azure.

### Usage:
Run with the folder parameter to dump files inside the mentioned folder with verbose output:

`PS C:\> Get-AzDomainInfo -folder MicroBurst -Verbose`

### Parameters:

* `-folder` - Folder to output to
* `-Subscription` - If not specified, the function will prompt you for a subscription to use
* `-ResourceGroup` - ResourceGroup to use for the gathering of Azure service information
* `-Users` - These are specific parameters to limit the output. You may not care about exporting the users and groups. Use -Users N and -Groups N to disable.
* `-Groups` - Specify which Az Domain groups to dump information on, default is yes
* `-StorageAccounts` - Specify which Storage accounts to dump information on, default is yes
* `-Resources` - Specify which Azure resources to dump information on, default is yes
* `-VMs` - Specify which Azure VMs to dump information on, default is yes
* `-NetworkInfo` - Specify which Azure Network information to dump, default is yes
* `-RBAC` - Specify which RBAC Users and Roles to dump information on, default is yes
* `-LoginBypass` - Bypass login process if already authenticated to Az
* `Additional Common Parameters eg. such as Verbose, Debug, etc ...` - cmdlet supports the common parameters which can be further detailed at (https:/go.microsoft.com/fwlink/?LinkID=113216).

### Considerations:
These are specific parameters to limit the output. You may not care about exporting the users and groups. Use -Users N and -Groups N to disable.
***
## Get-AzKeyVaultsAutomation
### Description:
This function creates an Automation Account Runbook that exports all available Key Vault keys, secrets, and certificates. The Runbook utilizes any available "Run as" accounts in the automation account to access the vaults.

### Usage:
### Parameters:
### Considerations:

***
## Invoke-AzVMBulkCMD 
### Description:
This function executes commands on one or more Azure Virtual Machines in a subscription.

### Usage:
### Parameters:
### Considerations:
