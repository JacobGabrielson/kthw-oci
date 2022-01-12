# Prerequisites

This assumes you're on a mac.

## Install OCI CLI

[Set up CLI](https://docs.oracle.com/en-us/iaas/Content/API/SDKDocs/cliinstall.htm#Quickstart)

## Create Compartment

As a best practice, create a
[Compartment](https://blogs.oracle.com/developers/post/introduction-to-the-key-concepts-of-oracle-cloud-infrastructure)
for all the resources about to be created.

```bash
T=<your root tenancy id>
oci iam compartment create --description "Resources for Kubernetes the Hard Way on OCI" --name "kthw" -c $T --wait-for-state ACTIVE
C=$(oci iam compartment list --query "data[?name=='kthw'] | [0] | id")
cat >> ~/.oci/config <<EOM
[KTHW]
compartment-id=$C
EOM

export OCI_CLI_PROFILE=KTHW

```

