# Contributing Guide for CSMAN Source
## How to build a package for CovScript?
```sh
csman install cics.csbuild
```
[CSBuild System](https://github.com/covscript/csbuild) Can help you building a CovScript Package easily.
```sh
# Build a Package
csbuild init --package
# Build an Extension
csbuild init --extension
```
After initialization, you can find `csman.json` in your current directory which created by csbuild. It seems like this:
```json
{
    "company.package_name": {
        "Description": "Write a brief description about your package in a line",
        "Author": "Anonymous",
        "State": "Preview",
        "Version": "1.0",
        "RemoteUrl": "Remote Git Url of your branch",
        "ContentUrl": "Package Url in server",
        "Dependencies": {
            "cs.runtime": "Stable"
        },
        "Contents": {
        }
    }
}
```
About the `Dependencies` and `Contents` fields, please refer to [CSMAN.INFO](http://csman.info/).  
When you finish this file, run `csbuild package --content-url [Content Url]` in package directory. 
Then you will get a zip file named `<PACKAGENAME>_<VERSION>.zip`, 
please upload to your server and fill the actual url of your zip file to `ContentUrl` field of `csman.json`.
## Upload package information through Pull Request
```sh
csman upload
```
Run this command in package directory, CSMAN will read `csman.json` and put your file into right place automatically.  
CSMAN will commit changes to your remote branch, then please start a pull request to https://github.com/covscript/csman-source/
