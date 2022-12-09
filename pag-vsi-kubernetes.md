---

copyright:
  years: 2022
lastupdated: "2022-12-09"

keywords: Virtual Servers, PAG, SSH

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# Preparing VSIs for {{site.data.keyword.pag_short}}
{: #pag-prep-vsi}

To use your VSI(s) with {{site.data.keyword.pag_short}}, you need to have the ssh public CA key of the {{site.data.keyword.pag_short}} instance configured on them. This ensures that logins will be only allowed on the VSI for all user certificates that are signed by the {{site.data.keyword.pag_short}} instance gateway CA, and reject all others.

In addition to needing the {{site.data.keyword.pag_short}} CA key configured, you will also need user accounts for each user who is preconfigured on the VSI. The user account name must match the user's IAM ID as described later on this page.

Normally the VSI administrator installs these {{site.data.keyword.pag_short}} CA keys to the VSI and enable certificate-based authentication.

To install the {{site.data.keyword.pag_short}} CA key and configure the VSI, perform the following steps:

1. Make sure you have the {{site.data.keyword.pag_short}} CLI plug-in that is installed on your local machine as described here: [Install {{site.data.keyword.pag_short}} CLI](/docs/privileged-access-gateway?topic=pags-ga-installing-the-pag-cli-plugin)

1. Log in to the IBM cloud account.

``` text
$ ibmcloud login --sso -a test.cloud.ibm.com -r us-south -c e7f84207f02a401784384cc02a128387 -g Default
```
This will log in and set the designated alpha account as well as the us-south region and Default resource group.

1. Make sure you are logged in to the VPN you had setup in the VPN Setup section of this [page](/docs/privileged-access-gateway?topic=pags-ga-PAG-Requirements). If you do not do this, the {{site.data.keyword.pag_short}} IP will not be accessible, and will time out.

1. Log in to the {{site.data.keyword.pag_short}}, by using the gateway IP/URL that was retrieved after provisioning the {{site.data.keyword.pag_short}} instance. The gateway IP is displayed on the Endpoint tab of the {{site.data.keyword.pag_short}} service UI for that instance.

``` text
$ ibmcloud pag login --gateway <gateway-url>
  ex. ibmcloud pag login --gateway 626f9c9b-d332-4cc1-a8eb-7d7f722b37a6.pag.appdomain.cloud
```

## Preparing the VSI endpoint
{: #pag-prep-vsi-endpoint}

1. Retrieve a public CA by running the below command, and then follow the instructions to add the public CA to the VSIs.

``` text
$ ibmcloud pag ca

<the_key_is_displayed_here>

USAGE NOTE
  - This CA public key needs to reside on the VSIs that would be accessed with Privileged Access Gateway.
  - Copy and paste the key above to a file.
  - For each VSI, copy this file to the VSI.
  - On the VSI, edit the file '/etc/ssh/sshd_config'.
  - Add a line containing TrustedUserCAKeys followed by the file path you copied the key file to.
  - For example: TrustedUserCAKeys /etc/ssh/pag-gateway-ca.pub
```
After changing the sshd_config file, you should restart sshd:

``` text
systemctl restart sshd
```

1. Before connecting to an endpoint for the first time, ensure that the target endpoint (VSI) has accounts with usernames being the IAM ID (IBMid-xxxxx) of all the users that will use those VSIs. If the IAM ID is not known, then it can be fetched from the output that every user gets on running the command `ibmcloud pag login --gateway`
