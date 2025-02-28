# Onboarding

Want to contribute, or simply run our projects/applications? Read through this file to get started.

- [Onboarding](#onboarding)
  - [Machine configuration](#machine-configuration)
    - [Dev drive](#dev-drive)
    - [Root Directory.Build.props](#root-directorybuildprops)
    - [Project-level Directory.Build.props](#project-level-directorybuildprops)
    - [Project-level user secrets](#project-level-user-secrets)
  - [Installed apps (recommended)](#installed-apps-recommended)

## Machine configuration

There is some configuration needed for the projects to correctly work

### Dev drive

Windows users do have the opportunity to create `dev drive`. This drive will get its own letter and will use different file system that is faster for use with code. After creating this dev drive, all code should reside in there, instead of the usual C: etc.

> [!NOTE]
> Creating dev drive is not necessary, but can improve overall performance when developing. See [Set up windows dev drive](https://learn.microsoft.com/en-us/windows/dev-drive/)

### Root Directory.Build.props

In case of a .NET application, there is one root `Directory.Build.props` file, that specifies some variables to be used in the build process. This file is not part of any source control and must be copied manually to the root *(root of all dotteddev repositories)*.

Current version of the file can be seen here [root Directory.Build.props](./root/Directory.Build.props)

- ~~`$(DEV_FOLDER)`~~ (now using `$(MSBuildThisFileDirectory)` instead)
- `$(NUGET_PACKAGES)` - __not required__ - sets folder for new nuget downloads and cache
  - uses default folder if not set
- `$(NUGET_PACKAGES_BUILD_PATH)` - folder, where all projects should build their nuget packages

```xml
<!-- file: Directory.Build.props -->
<Project>
    <PropertyGroup>
      <NUGET_PACKAGES_BUILD_PATH>path/to/your/folder</NUGET_PACKAGES_BUILD_PATH>
    </PropertyGroup>
</Project>
```

> [!TIP]
> `$(MSBuildThisFileDirectory)` is property from MSBuild. To see all MSBuild variables visit [MSBuild reserved and well-known properties](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-reserved-and-well-known-properties) and [Common MSBuild project properties](https://learn.microsoft.com/en-us/visualstudio/msbuild/common-msbuild-project-properties)

### Project-level Directory.Build.props

When developing .NET application or package, some variables need to be set in the project root.

- `$(APP_NAME)` - __required__ - sets the application name, which is used in the root `Directory.Build.props` file to specify artifact build output path
- `$(ProjectRoot)` - __required__ - should be always set to the `$(MSBuildThisFileDirectory)`. All projects will reference other projects relative to this path

All project-level `Directory.Build.props` __MUST__ include file above

```xml
<!-- file: Directory.Build.props -->
<Project> 
  <PropertyGroup>
    <APP_NAME>name_of_app_or_library</APP_NAME>    
    <ProjectRoot>$(MSBuildThisFileDirectory)</ProjectRoot>
  </PropertyGroup>
  <Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />
</Project>
```

### Project-level user secrets

There is possibility, that some projects use some user secrets. Read docs for the project itself to set yours accordingly.

> [!CAUTION]
> Any confident credentials etc. __MUST__ be defined in user-secrets, not in plaintext!

## Installed apps (recommended)

- Visual Studio IDE
- Visual Studio Code
- .NET (version specified by each project)
- Node version manager
- Google chrome / Firefox
- Git
- Docker
- Docker desktop
