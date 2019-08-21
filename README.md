# OSDBuilder 

Use the following steps to create a new Windows 10 ISO image with the latest cumulative updates included with OSDBuilder.

Requirements:
- Use a Windows 10 platform
- Install the latest Windows 10 1809 ADK

## Install OSDBuilder

Open PowerShell (Admin) 
    Set-ExecutionPolicy ByPass
    Install-Module OSDBuilder -Force
    Import-Module OSDBuilder -Force

Create a folder for OSDBuilder

    mkdir d:\OSDBuilder
Set the path location

    Get-OSDBuilder -setpath d:\OSDBuilder

Create the OSDBuilder folder structure
    
    Get-OSBuilder -CreatePaths

Optional: OneDrive production
    Get-DownOSDBuilder -ContentDownload 'OneDriveSetup Production'

Mount the Windows 10 ISO
Import the mounted ISO
    
    Import-OSMedia

Select the index version to use. For the Enterprise version this is 3. 
Inject the latest cumulative updates available
    
    Update-OSMedia -Download -Execute

Create a task, remove Appx and enable the .NET 3.5 framework
    
    New-OSBuildTask -RemoveAppx -taskname "W10-1809" -EnableNetFX3

Create a final OSBuild 
    
    New-OSBuild -bytaskname 'W10-1809' -Execute

Create a new ISO file
    
    New-OSBMediaISO

More information about OSDBuilder: https://www.osdeploy.com/

