# 

This Configuration bundles an Upbound Cloud extension and an API definition. 

# Crossplane configuration for "RDS as a Service"

This repository contains the definition for a [Crossplane configuration](https://docs.crossplane.io/v1.11/concepts/packages/#configuration-packages) that bundles a set of API definitions. This configuration is a starting point for new users who are creating their first control plane in [Upbound](https://cloud.upbound.io).

When this configuration is installed on a control plane, the control plane will have APIs to provision fully configured Amazon Relational
Database Service (RDS) instances, composed using cloud service primitives from the [Upbound Official AWS Provider](https://marketplace.upbound.io/providers/upbound/provider-aws).

## What's Inside

A custom API in [Crossplane](https://docs.crossplane.io/v1.11/getting-started/introduction/) is defined by:

- a CompositeResourceDefinition (XRD). This defines the schema or shape of the API.
- A Composition(s). Compositions implement the schema by _composing_ a set of Crossplane managed resources together.

For this configuration, the RDS API is defined by:

- a [PostgreSQLInstance](/apis/definition.yaml) type
- the PostgreSQLInstance is [composed](/apis/composition.yaml) of a single Instance resource and is configured to write a password for the database as a secret `upbound-provider-aws-password` to the `upbound-system` namespace of the control plane.

This repository also contains an [example claim](/.up/examples/postgres.yaml). You can apply this file on your control plane to invoke the RDS API and cause a database to be created.

## Next Steps

This repository is a starting point. You should be feel encouraged to:

1) create new API definitions in this same repo
2) tweak the existing API definition for RDS to your needs

Upbound will automatically detect the commits you make in your repo and build the configuration package for you. To learn more about how to build APIs for your managed control planes in Upbound, read the guide on [Upbound's docs](https://docs.upbound.io).
