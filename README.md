[![Build Status](https://dev.azure.com/sylwesterrapala/azure-piplines/_apis/build/status/xoac.rust-azure-pipelines?branchName=master)](https://dev.azure.com/sylwesterrapala/azure-piplines/_build/latest?definitionId=3&branchName=master)

# Azure Pipelines templates for rust

This repository contains ready to use templates for azure pipelines and can be used in very net manner.
Support:
- check minimal rust version is supported
- test on stable, nightly or beta channels
- check against common mistakes with clippy lints
- check format with rustfmt 
- cross **tests** and checks
- running rust on Windows Linux or macOs Agent is supported
- deploy docs to github-pages

**And you can get it with minimal configuration.**

### How to use run azure-pipelines?

1. Copy `azure-pipelines.yml` to your project.
2. Specify [service connection](https://docs.microsoft.com/pl-pl/azure/devops/pipelines/library/service-endpoints?view=azure-devops)
![](img/service_connection_pipelines.png)
3. Find all TODOs in `azure-pipelines.yml` and comment that sections if u don't wanna use them.

### How to deploy doc to github pages? 
This is useful if u want to have a separate documentation for master branch.

#### Github part
1. First you need to create a PAT (Personal Access Token) on Github. (recommended scopes for the token: `repo`, `user`, `admin:repo_hook`.)
2. Then create a branch `gh-pages` and us it as repo page. [Here you find how to do it](https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages#enabling-github-pages-to-publish-your-site-from-master-or-gh-pages)

#### Azure part

1. Go to your azure dev-ops pipeline project and click edit.  
![](img/doc_deploy1.png)  
2. Go inside variables:  
![](img/doc_deploy2.png)  
3. Add variable called `DocPublishToken` with value of your PAT(Personal Access Token). Don't forget to mark it as secret.  
![](img/doc_deploy3.png)  
4. Edit azure-pipelines.yml section with doc deploy (parameters.git) and you are done.

Example master doc generated for this example create.
[master doc for this hello word app](https://xoac.github.io/rust-azure-pipelines/doc/rust_azure_pipelines/)

### I have own `azure-pipelines.yml` and just wanna use one template. How?
It's simple. You just need this resources in your `azure-pipelines.yml`:
```
resources:
  repositories:
    - repository: templates
      type: github
      name: xoac/rust-azure-pipelines
      ref: refs/heads/master  # You can also specify tag refs/tags/v0.0.1
      endpoint: PipelinesTemplates
```

and now you can use all templates from `ci` folder like this `ci/TEMPLATE_NAME@templates` for [example](https://github.com/xoac/rust-azure-pipelines/blob/688c24b239cc7b4d4b5c89dbee321df468cf3825/azure-pipelines.yml#L19)

master branch can change. If u don't want it use some tag changin `ref` to `refs/tags/TAG`.


----

#### Sources:
* [Azure Pipelines for Rust Projects](https://nbsoftsolutions.com/blog/azure-pipelines-for-rust-projects)
* [tokio-rs](https://github.com/tokio-rs/tokio)

