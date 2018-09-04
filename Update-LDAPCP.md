## How to update LDAPCP

> **Important:**  
> Start a **new PowerShell console** to ensure the use of up to date persisted objects, which avoids concurrency update errors.  
> [Assembly must be updated manually](Install-LDAPCP.html) on SharePoint servers that do not run SharePoint service "Microsoft SharePoint Foundation Web Application".  
> If something goes wrong, [check this page](Fix-setup-issues.html) to fix issues.

- Run Update-SPSolution on the server running central administration:

```powershell
# This will start a timer job that will deploy the update on SharePoint servers. Central administration will restart during the process
Update-SPSolution -GACDeployment -Identity "LDAPCP.wsp" -LiteralPath "F:\Data\Dev\LDAPCP.wsp"
```

- Visit central administration > System Settings > Manage farm solutions: Wait until solution status shows "Deployed"
> If status shows "Error", restart the SharePoint timer service in central administration server, start a new PowerShell process and run Update-SPSolution again.
- [Update assembly manually](Install-LDAPCP.html) on SharePoint servers that do not run the service "Microsoft SharePoint Foundation Web Application"
- Restart IIS service on each SharePoint server
- Visit central administration > Security > LDAPCP global configuration page: review the configuration

## Updating from a version earlier than v10

Version 10 is a major update that has breaking changes. If you update from an earlier version, claim type configuration list will be reset and all customization made to that list will be lost.
