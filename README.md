# Camel K Reference Architecture

This repository serves as an example of GitOps-oriented management of an integration solution based on the Camel K platform.

## Provisioning

1. Install Camel K and Nexus (m88i) operators for all namespaces.

  `oc apply -f openshift-operators/ -n openshift-operators`

2. Create a namespace for Nexus and deploy an artifact server.

  `oc new-project nexus`

  `oc apply -f nexus/ -n nexus`

  Nexus will take a few minutes to initialize. If you are using the operator and custom resource provided, then the required Maven repositories (Red Hat's, etc.) are already proxied.

3. Create a namespace to deploy the integration and apply the provided custom resources.

  `oc new-project hello-world`

  `oc apply -f hello-world/ -n hello-world`
