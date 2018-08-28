# How to update LDAPCP

> **Important:**  
> Start a **new PowerShell console** to ensure the use of up to date persisted objects, which avoids concurrency update errors.  
> Version 10 has breaking changes, please read below if you update from an earlier version.  
> If some SharePoint servers do not run SharePoint service "Microsoft SharePoint Foundation Web Application", ldapcp.dll must be manually updated in their GAC as [documented here](Install-LDAPCP.html).  
> If something goes wrong, [check this page](Fix-setup-issues.html) to fix issues.

- Update solution

Run this cmdlet on the server running central administration:

```powershell
# This will start a timer job that will deploy the update on SharePoint servers. Central administration will restart during the process
Update-SPSolution -GACDeployment -Identity "LDAPCP.wsp" -LiteralPath "F:\Data\Dev\LDAPCP.wsp"
```

- Wait 1 minute
- Restart IIS service on each SharePoint server
- Visit central administration > Security > LDAPCP global configuration page: Check version and review configuration

## Updating from a version earlier than v10

Version 10 is a major update that has breaking changes. If you update from an earlier version, claim type configuration list will be reset and all customization made to that list will be lost.
