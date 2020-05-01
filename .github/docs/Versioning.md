# Versioning
Versioning in this project is controled via [semantic-release](https://github.com/semantic-release/semantic-release). As such it is important for all commits to follow these guidelines:

## Type
Must be one of the following:

* **major**: A new major version - This will bump the a MAJOR version
* **release**: A new major version - This will bump the a MAJOR version
* **breaking**: Introducing beaking changes - This will bump the a MAJOR version
* **feat**: A new feature - This will bump the a MINOR version
* **fix**: A bug fix - This will bump the PATCH version
* **perf**: A code change that improves performance - This will bump the PATCH version
* **chore**: Changes to the build process or auxiliary tools and libraries such as documentation generation - This does **not** bump versions or trigger a release

All other commit messages should be expected to **not** trigger releases and version changes.

**NB: If any commit message contains "breaking changes" this WILL trigger a MAJOR version release.**

**If the commit message contains [skip ci] the azure pipeline will not be triggered.**

## Examples
`feat: My new cool feature`  
`chor: Removes unused using statements`  
`fix: Unable to get profile`

# Building and Artifacts
Builds for this project are automated using azure-pipelines and [semantic-release](https://github.com/semantic-release/semantic-release).

The build steps are defined in the azure-pipelines.yml file, but generally they include **dotnet test** of all the projects, **dotnet publish** of the Service and API projects. 

If the commit message triggers a release, we build and push two docker image tags to our private container registry: [unicominternal.azurecr.io](unicominternal.azurecr.io)

# Deployments

Deployments to the integration environment are automated with each version release.

Deployments to production will be manually triggered in the [Pruvit Azure DevOps Portal](https://dev.azure.com/JustPruvit/UniCom/).
