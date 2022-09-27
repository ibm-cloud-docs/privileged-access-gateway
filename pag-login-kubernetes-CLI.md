---

copyright:
  years: 2022
lastupdated: "2022-08-31"

keywords: PAG Kubernetes, login, CLI, gateway, PAG

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# Using PAG with Kubernetes
{: #pag-using-pag-kubernetes}

To login and use a Kubernetes cluster through {{site.data.keyword.pag_full}} (PAG), you need the following CLI command:

```sh
$ ibmcloud pag kube login --gateway <Gateway URL> --cluster <kubernetes cluster name>
```

If the gateway parm is not specified, it uses the gateway url last entered in either this command or in another PAG CLI call.

When the CLI command is run, the cluster can be controlled through the `kubectl` command like it would normally be done.

Reference [Setting up the CLI](https://cloud.ibm.com/docs/containers?topic=containers-cs_cli_install#kubectl) for information on how to install and using kubectl.
{: note}

