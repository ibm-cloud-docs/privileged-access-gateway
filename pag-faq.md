---

copyright:
  years: 2022
lastupdated: "2022-10-07"


keywords: faqs, help, vpc, error messages, region, location, virtual servers, kubernetes, ssh, provisioning, high availability, PAG faqs

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# FAQs for Privileged Access Gateway
{: #pag-faqs}

## Why is my VPC not selectable in the PAG?
{: #pag-faqs-vpc}

Currently, only VPCs in the `us-south` region are usable with PAG.

## Why are my `ibmcloud pag` CLI commands hanging with no response?
{: #pag-faqs-cli-hung}

The PAG gateway that is created in your VPC is accessible from the private network inside your VPC only. Make sure that the VPN is configured for your VPC and that you are logged in to the VPC.

## I have logged in to the PAG gateway, but am unable to ssh into any of my Virtual Servers through PAG. What do I do?
{: #pag-faqs-cannot-ssh}

You may not have the Virtual Servers that are properly prepared to be used with PAG. You need user accounts on the Virtual Server for the IAM ID of each user. You also need a PAG Certificate Authority key on the virtual server. Run `ibmcloud pag ca` and follow the instructions there. Also, make sure that the users have the PAG IAM role `ssh-user`.

## Why am I not able to successfully connect to a Kubernetes cluster with `ibmcloud pag kube login`?
{: #pag-faqs-kubernetes-cluster-login-error}

Ensure that the user has the `kubernetes-user` IAM role for PAG. In addition, the user needs IAM permission to the Kubernetes cluster itself.

Also, and for this release, you must have a public gateway accessible from the subnet that you select for PAG in order for PAG to be able to authorize you have access.

## Why are some of my VPCs not selectable for use with PAG in the provisioning UI?
{: #pag-faqs-vpc-not-selectable}

You can only use VPCs in the `us-south` region for PAG at this time. Therefore, only those VPCs are selectable on the provisioning UI.

## Can I create multiple gateways for a PAG instance in different zones for high availability?
{: #pag-faqs-create-multiple-gateways}

Currently, a gateway is allowed in only one zone. Multiple gateways in different zones will be allowed in the future.

##  I selected Create on a PAG instance, but when I checked the resource list later, it indicated that the PAG instance provisioning has failed. What do I do?
{: #pag-faqs-provisioning-failed}

In the case of a provisioning failure, delete the failed instance from the resource list and try to provision the PAG service again.

##  Why am I not able to successfully connect to PAG with `ibmcloud pag login`?
{: #pag-faqs-login-failed}

First, check to make sure you have the correct IAM permissions to access PAG.

Also, and for this release, you must have a public gateway accessible from the subnet that you select for PAG in order for PAG to be able to authorize you have access.
