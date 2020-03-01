# Go API client for puppetforgeclient

## Introduction
The Puppet Forge API (hereafter referred to as the Forge API) provides quick access to all the
data on the Puppet Forge via a RESTful interface. Using the Forge API, you can write scripts and
tools that interact with the Puppet Forge website.

The Forge API's current version is `v3`. It is considered regression-stable, meaning that the returned
data is guaranteed to include the fields described in the schemas on this page; however, additional data
might be added in the future and clients must ignore any properties they do not recognize.

## OpenAPI Specification
The Puppet Forge v3 API is described by an
[OpenAPI 3.0](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.0.md) formatted
specification file. The most up-to-date version of this specification file can be accessed at
[https://forgeapi.puppet.com/v3/openapi.json](/v3/openapi.json).

## Features
* The API is accessed over HTTPS via the `forgeapi.puppet.com` domain. All data is returned in JSON
  format.
* Blank fields are included as `null`.
* Nested resources may use an abbreviated representation. A link to the full representation for the
  resource is always included.
* All timestamps in JSON responses are returned in ISO 8601 format: `YYYY-MM-DD HH:MM:SS ±HHMM`.
* The HTTP response headers include caching hints for conditional requests.

## Concepts and Terminology
* **Module**: Modules are self-contained bundles of code and data with a specific directory structure. Modules are identified by a combination of the author's username and the module's name, separated by a hyphen. For example: `puppetlabs-apache`
* **Release**: A single, specific version of a module is called a Release. Releases are identified by a combination of the module identifier (see above) and the Release version, separated by a hyphen. For example: `puppetlabs-apache-4.0.0`

## Errors
The Puppet Forge API follows [RFC 2616](https://tools.ietf.org/html/rfc2616) and
[RFC 6585](https://tools.ietf.org/html/rfc6585).

Error responses are served with a `4xx` or `5xx` status code, and are sent as a JSON document with a content type
of `application/json`. The error document contains the following top-level keys and values:

  * `message`: a string value that summarizes the problem
  * `errors`: a list (array) of strings containing additional details describing the underlying cause(s) of the
    failure

An example error response is shown below:

```json
{
  \"message\": \"400 Bad Request\",
  \"errors\": [
    \"Cannot parse request body as JSON\"
  ]
}
```

## User-Agent Required
All API requests must include a valid `User-Agent` header. Requests with no `User-Agent` header will
be rejected. The `User-Agent` header helps identify your application or library, so we can communicate
with you if necessary. If your use of the API is informal or personal, we recommend using your username
as the value for the `User-Agent` header.

User-Agent headers are a list of one or more product descriptions, generally taking this form:

```
<name-without-spaces>/<version> (comments)
```

For example, the following are all useful User-Agent values:

```
MyApplication/0.0.0 Her/0.6.8 Faraday/0.8.8 Ruby/1.9.3-p194 (i386-linux)
My-Library-Name/1.2.4
myusername
```


## Overview
This API client was generated by the [OpenAPI Generator](https://openapi-generator.tech) project.  By using the [OpenAPI-spec](https://www.openapis.org/) from a remote server, you can easily generate an API client.

- API version: 18
- Package version: 1.0.1
- Build package: org.openapitools.codegen.languages.GoClientCodegen

## Installation

Install the following dependencies:

```shell
go get github.com/stretchr/testify/assert
go get golang.org/x/oauth2
go get golang.org/x/net/context
go get github.com/antihax/optional
```

Put the package under your project folder and add the following in import:

```golang
import "./puppetforgeclient"
```

## Documentation for API Endpoints

All URIs are relative to *https://forgeapi.puppet.com*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*ModuleOperationsApi* | [**DeleteModule**](docs/ModuleOperationsApi.md#deletemodule) | **Delete** /v3/modules/{module_slug} | Delete module
*ModuleOperationsApi* | [**DeprecateModule**](docs/ModuleOperationsApi.md#deprecatemodule) | **Patch** /v3/modules/{module_slug} | Deprecate module
*ModuleOperationsApi* | [**GetModule**](docs/ModuleOperationsApi.md#getmodule) | **Get** /v3/modules/{module_slug} | Fetch module
*ModuleOperationsApi* | [**GetModules**](docs/ModuleOperationsApi.md#getmodules) | **Get** /v3/modules | List modules
*ReleaseOperationsApi* | [**AddRelease**](docs/ReleaseOperationsApi.md#addrelease) | **Post** /v3/releases | Create module release
*ReleaseOperationsApi* | [**DeleteRelease**](docs/ReleaseOperationsApi.md#deleterelease) | **Delete** /v3/releases/{release_slug} | Delete module release
*ReleaseOperationsApi* | [**GetFile**](docs/ReleaseOperationsApi.md#getfile) | **Get** /v3/files/{filename} | Download module release
*ReleaseOperationsApi* | [**GetRelease**](docs/ReleaseOperationsApi.md#getrelease) | **Get** /v3/releases/{release_slug} | Fetch module release
*ReleaseOperationsApi* | [**GetReleasePlan**](docs/ReleaseOperationsApi.md#getreleaseplan) | **Get** /v3/releases/{release_slug}/plans/{plan_name} | Fetch module release plan
*ReleaseOperationsApi* | [**GetReleasePlans**](docs/ReleaseOperationsApi.md#getreleaseplans) | **Get** /v3/releases/{release_slug}/plans | List module release plans
*ReleaseOperationsApi* | [**GetReleases**](docs/ReleaseOperationsApi.md#getreleases) | **Get** /v3/releases | List module releases
*UserOperationsApi* | [**GetUser**](docs/UserOperationsApi.md#getuser) | **Get** /v3/users/{user_slug} | Fetch user
*UserOperationsApi* | [**GetUsers**](docs/UserOperationsApi.md#getusers) | **Get** /v3/users | List users


## Documentation For Models

 - [DeprecationRequest](docs/DeprecationRequest.md)
 - [DeprecationRequestParams](docs/DeprecationRequestParams.md)
 - [InlineObject](docs/InlineObject.md)
 - [InlineResponse200](docs/InlineResponse200.md)
 - [InlineResponse2001](docs/InlineResponse2001.md)
 - [InlineResponse2002](docs/InlineResponse2002.md)
 - [InlineResponse2003](docs/InlineResponse2003.md)
 - [InlineResponse400](docs/InlineResponse400.md)
 - [InlineResponse401](docs/InlineResponse401.md)
 - [InlineResponse403](docs/InlineResponse403.md)
 - [InlineResponse404](docs/InlineResponse404.md)
 - [InlineResponse409](docs/InlineResponse409.md)
 - [Module](docs/Module.md)
 - [ModuleAbbreviated](docs/ModuleAbbreviated.md)
 - [ModuleMinimal](docs/ModuleMinimal.md)
 - [Pagination](docs/Pagination.md)
 - [Release](docs/Release.md)
 - [ReleaseAbbreviated](docs/ReleaseAbbreviated.md)
 - [ReleaseMinimal](docs/ReleaseMinimal.md)
 - [ReleasePlan](docs/ReleasePlan.md)
 - [ReleasePlanAbbreviated](docs/ReleasePlanAbbreviated.md)
 - [ReleasePlanPlanMetadata](docs/ReleasePlanPlanMetadata.md)
 - [ReleasePlanPlanMetadataDocstring](docs/ReleasePlanPlanMetadataDocstring.md)
 - [ReleasePlanPlanMetadataDocstringTags](docs/ReleasePlanPlanMetadataDocstringTags.md)
 - [ReleaseTask](docs/ReleaseTask.md)
 - [User](docs/User.md)
 - [UserAbbreviated](docs/UserAbbreviated.md)


## Documentation For Authorization



## ApiKeyAuth

- **Type**: API key

Example

```golang
auth := context.WithValue(context.Background(), sw.ContextAPIKey, sw.APIKey{
    Key: "APIKEY",
    Prefix: "Bearer", // Omit if not necessary.
})
r, err := client.Service.Operation(auth, args)
```



## Author



