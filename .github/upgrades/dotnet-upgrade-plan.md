# .NET 8.0 Upgrade Plan

## Execution Steps

Execute steps below sequentially one by one in the order they are listed.

1. Validate that an .NET 8.0 SDK required for this upgrade is installed on the machine and if not, help to get it installed.
2. Ensure that the SDK version specified in global.json files is compatible with the .NET 8.0 upgrade.
3. Upgrade NetPrints\NetPrintsEditor.csproj
4. Upgrade NetPrints\NetPrintsVSIX.csproj
5. Upgrade NetPrints\NetPrintsCLI.csproj
6. Upgrade NetPrints\NetPrintsEditorUnitTests.csproj
7. Upgrade NetPrints\NetPrintsUnitTests.csproj

## Settings

### Excluded projects

| Project name | Description |
|:-----------------------------------------------|:---------------------------:|
| NetPrints\NetPrints.csproj | No issues found |

### Aggregate NuGet packages modifications across all projects

| Package Name | Current Version | New Version | Description |
|:---------------------|:---------------:|:-----------:|:------------------------------------|
| System.Management | 4.5.0 | 8.0.0 | Recommended for .NET 8.0 |
| Microsoft.VSSDK.BuildTools | 16.1.3116 | 15.7.104 | Incompatible with .NET 8.0 |
| MvvmLightLibsStd10 | 5.4.1.1 | (deprecated) | Deprecated, consider CommunityToolkit.Mvvm |

### Project upgrade details

#### NetPrints\\NetPrintsEditor.csproj modifications

Project properties changes:
  - Target framework should be changed from `net461` to `net8.0-windows`

NuGet packages changes:
  - System.Management should be updated from `4.5.0` to `8.0.0` (recommended for .NET 8.0)
  - MvvmLightLibsStd10 is deprecated; consider replacing with CommunityToolkit.Mvvm

#### NetPrints\\NetPrintsVSIX.csproj modifications

Project properties changes:
  - Convert project file to SDK-style
  - Target framework should be changed from `.NETFramework,Version=v4.6.1` to `net8.0-windows`

NuGet packages changes:
  - Microsoft.VSSDK.BuildTools should be updated from `16.1.3116` to `15.7.104` (incompatible with .NET 8.0)

#### NetPrints\\NetPrintsCLI.csproj modifications

Project properties changes:
  - Target frameworks should be changed from `netcoreapp2.0;net461` to `netcoreapp2.0;net461;net8.0`

#### NetPrints\\NetPrintsEditorUnitTests.csproj modifications

Project properties changes:
  - Target framework should be changed from `net461` to `net8.0`

#### NetPrints\\NetPrintsUnitTests.csproj modifications

Project properties changes:
  - Target framework should be changed from `netcoreapp2.0` to `net8.0`
