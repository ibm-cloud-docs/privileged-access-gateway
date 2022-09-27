---

copyright:
  years: 2022
lastupdated: "2022-09-12"

keywords: virtual servers PAG, CA key, SSH, endpoint, gateway, host name

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# Preparing Virtual Servers for PAG
{: #pag-prep-vsi}

To use your Virtual Servers with {{site.data.keyword.pag_full}} (PAG), you need to have the SSH public CA key of the PAG gateway instance configured on them. This ensures that logins will be allowed on the Virtual Server for all user certificates that are signed by the PAG instance gateway CA, and reject all others.

In addition to needing the PAG gateway CA key configured, you also need user accounts for each user who is preconfigured on the Virtual Server. The user account name must match the user's IAM ID as described later on this page.

Normally the Virtual Server administrator is the one to install these PAG CA keys to the Virtual Server and enable certificate-based authentication.

To install the PAG CA key and configure the Virtual Server, perform the following steps:

1. Make sure you have installed the PAG CLI plug-in on your local machine by using `ibmcloud plugin install pag`.

2. Login with the CLI to your IBM cloud account, selecting the `us-south` region. For example, `ibmcloud login --sso -r us-south`.

3. Make sure you are logged in to the VPN you had setup in the VPN Setup section of this [page](/docs/allowlist/privileged-access-gateway?topic=privileged-access-gateway-pag-requirements). If you do not do this, the PAG gateway hostname will not be accessible, and will time out.

4. Log in to the PAG gateway, by using the gateway hostname that was retrieved after provisioning the PAG instance. The gateway hostname is displayed on the Endpoint tab of the PAG service UI for that instance.

```sh
$ ibmcloud pag login --gateway <gateway-url>
  ex. ibmcloud pag login --gateway 626f9c9b-d332-4cc1-a8eb-7d7f722b37a6.pag.appdomain.cloud
```

## Preparing the Virtual Server endpoint
{: #pag-prep-vsi-endpoint}

1. Retrieve a public CA by running the below command, and then follow the instructions to add the public CA to the VSIs.

```sh
$ ibmcloud pag ca

<the_key_is_displayed_here>

USAGE NOTE
  - This CA public key needs to reside on the VSIs that would be accessed with PAG gateway.
  - Please copy and paste the key above to a file.
  - For each Virtual Server, copy this file to the Virtual Server.
  - On the Virtual Server, edit the file '/etc/ssh/sshd_config'.
  - Add a line containing TrustedUserCAKeys followed by the file path you copied the key file to.
  - For example: TrustedUserCAKeys /etc/ssh/pag-gateway-ca.pub
```
After changing the sshd_config file, you should restart sshd:

```sh
systemctl restart sshd
```

2. Before connecting to an endpoint for the first time, ensure that the target endpoint(Virtual Server) has accounts with usernames being the IAM ID (IBMid-xxxxx) of all the users that use those Virtual Servers. If the IAM ID is not known, then it can be fetched from the output that every user gets on running the command `ibmcloud pag login --gateway`

An Administrator can get the IAM IDs for their users. Go to Manage -> Access (IAM) and then select Users. On each user, the Administrator can click on the details on the right upper corner and see the IAM id for the user.
{: note}

This command outputs for all users in your account along with their IAM IDs
```sh
ibmcloud account users --output json | jq -r '.[] | (.userId)+" "+(.ibmUniqueId)'
```
{: tip}

