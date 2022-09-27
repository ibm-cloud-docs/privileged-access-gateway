---

copyright:
  years: 2022
lastupdated: "2022-09-12"

keywords: using PAG with SSH, using SSH, key agent, host name, gateway

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

# Using PAG with SSH
{: #pag-using-pag-ssh}

Once you have provisioned a {{site.data.keyword.pag_full}} (PAG) instance, and your {{site.data.keyword.virtualmachinesshort}} have been prepared for PAG as described [here](/docs/allowlist/privileged-access-gateway?topic=privileged-access-gateway-pag-prep-vsi), you are ready to start using it to access your servers.

IBM requires that the SSH key agent is running on your local machine to use PAG with the CLI. This requirement will go away in future releases.
{: note}

To run the key agent, run:
```sh
$ eval ssh-agent
```


1. Make sure you have the PAG CLI plug-in installed on your local machine. If you do not have it, you can install by typing `ibmcloud plugin install pag`.

1. Login with the CLI to your IBM cloud account, selecting the us-south region. For example, `ibmcloud login --sso -r us-south`.

1. Make sure you are logged in to the {{site.data.keyword.vpn_short}} you had setup in the VPN Setup section of this [page](/docs/allowlist/privileged-access-gateway?topic=privileged-access-gateway-pag-requirements). If you do not do this, the PAG gateway hostname will not be accessible, and will time out.

1. Log in to the PAG gateway, by using the gateway hostname that was retrieved after provisioning the PAG instance. The gateway hostname is displayed on the Endpoint tab of the PAG service UI for that instance.

   ```sh
   $ ibmcloud pag login --gateway <gateway-url>
     ex. ibmcloud pag login --gateway 626f9c9b-d332-4cc1-a8eb-7d7f722b37a6.pag.appdomain.cloud

     The keys are typically valid for about an hour, after which one would have to login again.
   ```

## Steps for connecting to an endpoint
{: #pag-connecting-endpoint}

1. Run SSH to a target endpoint by means of PAG.

   ```sh
   $ ibmcloud pag ssh <target-hostname>
     ex. ibmcloud pag ssh 169.59.165.66
   ```

2. Execute the commands on to the target VSI through the interactive terminal.

3. Type `exit` or `logout` to end the session.

## Retrieving and viewing the session recordings
{: #pag-retrieve-recordings}

You can retrieve and view your [session recordings](/docs/allowlist/privileged-access-gateway?topic=privileged-access-gateway-pag-session-recording-playback).
