---

copyright:
  years: 2022
lastupdated: "2022-12-06"

keywords: Kubernetes, login, CLI, gateway, RedHat, Openshift

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# Using {{site.data.keyword.pag_short}} with Kubernetes
{: #pag-using-pag-kubernetes}

{{site.data.keyword.pag_full}} supports access to both IBM Cloud Kubernetes service clusters and IBM Cloud Redhat Openshift clusters. This page decribes both types of clusters and how they are used with the {{site.data.keyword.pag_short}} CLI.

Before running any Kubernetes commands you have to make sure the gateway is set.

Set {{site.data.keyword.pag_short}} to use the gateway hostname of your instance. The gateway hostname is displayed on the Endpoint tab of the {{site.data.keyword.pag_full}} service UI for that instance.

```sh
$ibmcloud pag gateway set <gateway URL>
```
You can list the existing clusters in your account with the following command:

```sh
$ibmcloud ks cluster ls
```

## Using {{site.data.keyword.pag_short}} with IBM Cloud Kubernetes service clusters
{: #pag-using-pag-kubernetes-service}

Connect to the Gateway and initialise Gateway for proxying IBM Cloud Kubernetes Service clusters.

```sh
$ibmcloud pag ks config <cluster name>
```
This gets the kubernetes configuration file.

When the CLI command is run, the cluster can be controlled through the `kubectl` command like it would normally be done.

Reference [Setting up the CLI](https://cloud.ibm.com/docs/containers?topic=containers-cs_cli_install#kubectl) for information on how to install and use kubectl.
{: note}

## Using {{site.data.keyword.pag_short}} with IBM Cloud RedHat OpenShift clusters
{: #pag-using-pag-redhat-openshift-clusters}

Connect to the Gateway and initialise Gateway for proxying IBM Cloud RedHat Openshift Service clusters.

```sh
$ibmcloud pag oc config <cluster name> [--passcode <passcode>]
```
This gets the RedHat Openshift configuration file.

 When the CLI command is run, the cluster can be controlled through the `oc` or `kubectl` command like it would normally be done.

If both private and public endpoints are enabled on your cluster, {{site.data.keyword.pag_short}} uses the private address.
{: note}

Common comands that you run for both types include the [ks](/docs/privileged-access-gateway?topic=privileged-access-gateway-pag-cli-commands#cli-kubernete-commands) and [oc](/docs/privileged-access-gateway?topic=privileged-access-gateway-pag-cli-commands#cli-openshift-commands) as referenced in the CLI [commands](/docs/privileged-access-gateway?topic=privileged-access-gateway-pag-cli-commands) topic.
{: tip}
