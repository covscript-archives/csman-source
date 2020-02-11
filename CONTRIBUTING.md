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
        "ContentUrl": "Package Url in server",
        "Dependencies": {
            "cs.runtime": "latest"
        },
        "Contents": {
        }
    }
}
```
About the `Dependencies` and `Contents` fields, please refer to [CSMAN.INFO](http://csman.info/).  
When you finish this file, run `csbuild package --content-url [Content Url]` in package directory. 
Then you will get a zip file named `<PACKAGENAME>_<VERSION>.zip`, please upload to your server.
## Upload package information through Pull Request
```sh
csman upload --config [path to your csman.json]
```
Run this command in your local branch directory, CSMAN will put your file into right place automatically.  
Then commit changes to your remote branch, start a pull request to https://github.com/covscript/csman-source/
