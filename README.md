# installer.sh
WIP! Installer script to use in scaffolding projects.


Future home for https://github.com/integratedexperts/drupal-dev/blob/8.x/install.sh

## What is it?
Imagine you have a repository with files that need to be distributed to multiple projects. And not just once, but actually allow to keep files up-to-date in the future with an ease. 

The workflow would be to have a repository with some source files (scaffolding) and several repositories with projects using these files (consumers). In order to distribute the files, one would download scaffolding files, copy them over to each consumer site, rename file names and other values (very tedious and lengthy process) and resolve any conflicts, if any of the scaffolding files already exist.

This project provides bash installer script that handles discovering and downloading scaffolding versions from GitHub, and token replacements.

## Usage
1. Copy file into your scaffolding repository
2. Provide a URL to it in your scaffolding repository `README.md` file:
```
bash <(curl -L https://raw.githubusercontent.com/YOURORG/YOURSCAFFOLDINGREPO/BRANCH/install.sh?"$(date +%s)") "$@"
```
3. Consumers will be using this URL to get the latest releases of your scaffolding files.

## Features
- Allow to override existing files (update)
- Allow to discover values by providing callbacks (TBD). I.e., all files starting with `MyProject` will be replaced with the actual value of the file within that project.
- Verbose output while installing
- Has automated tests
- Provide variables:
  - `PACKAGE_VERSION` - filled in witht the value of the latest release by the discovery mechanism from GitHub.
  - `PACKAGE_COMMIT_SHA` - can be specified to override release dicovery mechanism
- Allow to provide config in scaffolding repo using `.installconfig` file
