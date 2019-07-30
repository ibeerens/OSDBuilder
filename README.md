OSDBuilder

Windows 10 image

Use a Windows 10 platform
Install the latest ADK

Install OSDBuilder

Open PowerShell
Install-Module OSDBuilder
Set-ExecutionPolicy ByPass
Import-Module OSDBuilder

mkdir d:\OSDBuilder
Get-OSDBuilder -setpath d:\OSDBuilder
Get-OSBuilder -CreatePaths

Mount the Windows 10 ISO

Import-OSMedia
Select the version to update 

Update-OSMedia -Download -Execute
New-OSBuildTask -RemoveAppx -taskname "W10-1809" -EnableNetFX3

New-OSBuild -bytaskname wind10build -Execute

New-OSBMediaISO