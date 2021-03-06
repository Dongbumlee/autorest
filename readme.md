# <img align="center" src="./docs/images/logo.png">  AutoRest


The **AutoRest** tool generates client libraries for accessing RESTful web services. Input to *AutoRest* is a spec that describes the REST API using the [OpenAPI Specification](https://github.com/OAI/OpenAPI-Specification) format.

<!-- 1) returns SVGs now which aren't rendered by GitHub 2) seems to be awfully unresponsive and unreliable lately
[![PR Stats](http://issuestats.com/github/Azure/autorest/badge/pr?style=flat-square)](http://issuestats.com/github/Azure/autorest)
[![Issue Stats](http://issuestats.com/github/Azure/autorest/badge/issue?style=flat-square)](http://issuestats.com/github/Azure/autorest)
-->

## Support Policy
AutoRest is an open source tool -- if you need assistance, first check the documentation. If you find a bug or need some help, feel free to submit an [issue](https://github.com/Azure/autorest/issues)

# Getting Started using AutoRest ![image](./docs/images/normal.png)

Start by reading the documentation for using AutoRest:
- [Installing AutoRest](./docs/installing-autorest.md) - Shows how to install AutoRest.
- [Understanding AutoRest Versions and Extensions](./docs/autorest-versioning.md) - AutoRest core and extension versioning
- [Managing AutoRest](./docs/managing-autorest.md) - shows how to get new updates to AutoRest and choose which version to use for code generation.
- [Generating a Client using AutoRest](./docs/examples/generating-a-client.md) - shows simple command line usage for generating a client library.
- [Command Line Interface Documentation](./docs/user/command-line-interface.md) - explains common command line arguments.
- [Examples](./Samples) - full, walkthrough-style scenarios for using AutoRest.
- [Recent Updates](./changelog.md) - notes on recent updates .

# New! AutoRest Version 3.0 
AutoRest 3.0 introduces a large number of internal changes to support new scenarios. 

## Features

### OpenAPI3 support! 
AutoRest 3.0 finally supports OpenAPI3 files as an input format, with the following caveats:
- existing AutoRest v2 generators may not support all features from OpenAPI3. (see next section)
- `anyOf`, `oneOf` are not currently supported 
- other OpenAPI3 specific features may not be entirely supported.

### Generators

A new set of language generator plugins are being written that adopt the lighter-weight patterns for Azure Core libraries.<br>
Existing V2 generators will default to processing with the AutoRest 2 pipeline. <br>
If you want to force it to use the v3 (to get support for OpenAPI3 ) add `--v3` to the command line:
> `autorest --v3 --csharp ...`

| Generator | Command | Notes |
|----|---|---|
|PowerShell| `autorest --powershell ...` |Fully V3 Supported - use to generate powershell modules |   
|CSharp|`autorest --csharp ...` |v2 generator, may use OpenAPI3 with `--v3` switch (may be some differences) - v3 generator in progress | 
|Python|`autorest --python ...` |v2 generator, may use OpenAPI3 with `--v3` switch (may be some differences) - v3 generator in progress| 
|Java|`autorest --java ...` |v2 generator, may use OpenAPI3 with `--v3` switch (may be some differences) - v3 generator in progress | 
|TypeScript|`autorest --typescript ...` |v2 generator, may use OpenAPI3 with `--v3` switch (may be some differences) - v3 generator in progress | 
|Go|`autorest --go ...` |v2 generator, may use OpenAPI3 with `--v3` switch (may be some differences) - v3 generator in progress | 
|Ruby|`autorest --ruby ...` |v2 generator - does not support v3 feature, no OpenAPI3 support | 

#### New V3 Pipeline

In AutoRest v3, the pipeline has been drastically rebuilt, which allows support for:
- OpenAPI3 inputs
- Supporting merging multiple API versions 
- Model Deduplication and Subset reduction across multiple API versions
- Azure Profile support (v3 generator required)

Some related information:
- [Validation Rules & Linting](https://github.com/Azure/azure-openapi-validator/blob/master/docs/readme.md) - about the validation rules in AutoRest
- [Client Runtimes](./docs/developer/architecture/Autorest-and-Clientruntimes.md) - information about the client runtimes required for using code generated by AutoRest
<!-- - [Developer Guide](./docs/developer/guide/) - Notes on developing with AutoRest -->

### Supported Platforms

While AutoRest itself runs on NodeJS, some generators use the .NET Core 2.0 runtime, which is the most limiting factor.
See [dotnet/core/release-notes/2.0/2.0-supported-os.md](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for a list of supported platforms.

---

### Code of Conduct 
This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

