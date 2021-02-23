Welcome to the MicroBurst wiki! This wiki is broken out into the individual module types ([Az](https://github.com/NetSPI/MicroBurst/wiki/Az-Functions), [AzureAD](https://github.com/NetSPI/MicroBurst/wiki/AzureAD-Functions), etc.) which can be found in the sidebar to the right. Most of the core functions will be in the [Az](https://github.com/NetSPI/MicroBurst/wiki/Az-Functions) section, as that's where most of the Azure functionality is in the PowerShell modules.

# General Usage
### Importing the Module
	Import-Module .\MicroBurst.psm1
This will import all applicable functions based off of the currently installed modules in your environment.

# To Do 
There are several items on the MicroBurst "To Do" list that we could use some help on. Pull requests are always welcome (See below), so feel free to take a crack at one of these items:
* Converting all of the functionality in Get-AzPasswords over to the REST APIs

# Pull Request Process
For any new functionality, or updates to existing code, please try to generally keep with the coding practices (comments, indents, parameter names) of the existing code. When adding new functions, follow the naming convention used by existing functions in the same family of functions (Get-AzPasswords). 

Finally, please follow the Microsoft conventions for [approved PowerShell verbs](https://docs.microsoft.com/en-us/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands).
If you have any questions/ideas/comments, feel free to raise an [Issue](https://github.com/NetSPI/MicroBurst/issues) or ping [Karl on Twitter](https://twitter.com/kfosaaen).

For those looking for the original function descriptions, check out the now deprecated [AzureRM section](https://github.com/NetSPI/MicroBurst/wiki/AzureRM-%5BDeprecated%5D-Functions).