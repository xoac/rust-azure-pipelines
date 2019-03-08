[![Build Status](https://dev.azure.com/sylwesterrapala/azure-piplines/_apis/build/status/xoac.rust-azure-pipelines?branchName=master)](https://dev.azure.com/sylwesterrapala/azure-piplines/_build/latest?definitionId=3&branchName=master)

WIP

# Rust Templates for Azure Pipelines

## How to use run azure-pipelines.

1. Copy azure-pipelines.yml to your project if you don't have one Or add this resources.
```
resources:
  repositories:
    - repository: templates
      type: github
      name: xoac/rust-azure-pipelines
      endpoint: PiplinesTemplate

```
2. Specify [service connection](https://docs.microsoft.com/pl-pl/azure/devops/pipelines/library/service-endpoints?view=azure-devops)
![](allow_templates.png)

## How to deploy doc to github pages? 

## Sources:
* [Azure Pipelines for Rust Projects](https://nbsoftsolutions.com/blog/azure-pipelines-for-rust-projects)
* [tokio-rs](https://github.com/tokio-rs/tokio)

