Auth0 Terraform Provider
========================

[![Build](https://github.com/alexkappa/terraform-provider-auth0/workflows/Build/badge.svg)](https://github.com/alexkappa/terraform-provider-auth0/actions)
[![Maintainability](https://api.codeclimate.com/v1/badges/9c49c10286123b716c79/maintainability)](https://codeclimate.com/github/alexkappa/terraform-provider-auth0/maintainability)
[![Test Coverage](https://api.codeclimate.com/v1/badges/9c49c10286123b716c79/test_coverage)](https://codeclimate.com/github/alexkappa/terraform-provider-auth0/test_coverage)
[![Gitter](https://badges.gitter.im/terraform-provider-auth0/community.svg)](https://gitter.im/terraform-provider-auth0/community)


Requirements
------------

-	[Terraform](https://www.terraform.io/downloads.html) `0.11.x` || `0.12.x`
-	[Go](https://golang.org/doc/install) 1.10 (to build the provider plugin)

Using the provider
------------------

To install this provider, copy and paste this code into your Terraform configuration. Then, run `terraform init`.

```
provider "auth0" {
  version = "> 0.8"
}
```

To configure the provider with your personal client credentials, define the `domain`, `client_id` and `client_secret`.

```
provider "auth0" {
  version = "> 0.8"
  domain = "<domain>"
  client_id = "<client-id>"
  client_secret = "<client-secret>"
}
```

These variables can also be accessed via the `AUTH0_DOMAIN`, `AUTH0_CLIENT_ID` and `AUTH0_CLIENT_SECRET` environment variables respectively.

Examples of resources can be found in the [examples directory](example/).

Building The Provider
---------------------

Clone repository to: `$GOPATH/src/github.com/alexkappa/terraform-provider-auth0`

```sh
$ mkdir -p $GOPATH/src/github.com/alexkappa; cd $GOPATH/src/github.com/alexkappa
$ git clone git@github.com:alexkappa/terraform-provider-auth0
```

Enter the provider directory and build the provider

```sh
$ cd $GOPATH/src/github.com/alexkappa/terraform-provider-auth0
$ make build
```

Developing the Provider
-----------------------

If you wish to work on the provider, you'll need [Go](http://www.golang.org) installed on your machine (version 1.10+ is *required*). You'll also need to correctly setup a [GOPATH](http://golang.org/doc/code.html#GOPATH), as well as adding `$GOPATH/bin` to your `$PATH`.

On how to develop custom terraform providers, read the [official guide](https://www.terraform.io/docs/extend/writing-custom-providers.html).

To compile the provider, run `make build`. This will build the provider and install the provider binary in the `$GOPATH/bin` directory.

```sh
$ make build
...
$ $GOPATH/bin/terraform-provider-auth0
...
```

In order to test the provider, you can simply run `make test`.

```sh
$ make test
```

In order to run the full suite of Acceptance tests, the following environment variables must be set:

```sh
AUTH0_DOMAIN=<your-auth0-tenant-domain>
AUTH0_CLIENT_ID=<your-auth0-client-id>
AUTH0_CLIENT_SECRET=<your-auth0-client-secret>
```

Then, run `make testacc`. 

*Note:* The acceptance tests make calls to a real Auth0 tenant, and create real resources. Certain tests, for example
for custom domains (`TestAccCustomDomain`), also require a paid Auth0 subscription to be able to run successfully. 

At the time of writing, the following configuration steps are also required for the test tenant:

* The `Username-Password-Authentication` connection must have _Requires Username_ option enabled for the user tests to 
successfully run.

Supporting the provider
-----------------------

This project is maintained by myself ([@alexkappa](https://github.com/alexkappa)) with contributions from [great people](https://github.com/alexkappa/terraform-provider-auth0/graphs/contributors) across the community. 

I am not affiliated with [Auth0](https://auth0.com/) and all work that goes into this provider is done during my spare time. Please be patient with issues and pull requests.

If you or your company relies on this plugin or the [Go SDK](https://github.com/go-auth0/auth0) and would like to ensure its continuing support please consider [donating](https://github.com/sponsors/alexkappa).