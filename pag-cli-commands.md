---

copyright:
  years: 2022
lastupdated: "2022-12-06"

kaywords: cli, commands

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}
{:caption: .caption}

# CLI commands for the {{site.data.keyword.pag_short}} plug-in
{: #pag-cli-commands}

All the commands are run in the {{site.data.keyword.pag_short}} namespace of the IBM Cloud CLI.


## Main commands
{: #cli-main-commands}

| Command | Description |
|-----------|-------------|
| `gateway`| Set or Get the gateway host URL |
| `ssh`| SSH access to Linux Virtual Server Instances in an IBM Cloud VPC |
| `rdp`| [Future] For Remote Desktop Protocol (RDP) access to Windows Virtual Server Instances in an IBM Cloud VPC |
| `ks`| IBM Kubernetes Service access|
| `oc`| IBM RedHat Openshift access |
| `session`| Session management |
| `play`| Play recorded sessions |
{: caption="Table 1. CLI main commands for {{site.data.keyword.pag_short}}}

### Gateway commands (`gateway`)
{: #cli-gateway-commands}

| Command | Description | Usage |
|-----------|------------|-------------|
| `set`| Set the Gateway host URL |`ibmcloud pag gateway set <Gateway-Host-URL>` |
| `get`| Get the Gateway host URL |`ibmcloud pag gateway get` |
{: caption="Table 2. CLI gateway commands for {{site.data.keyword.pag_short}}}

### SSH commands (`ssh`)
{: #cli-ssh-commands}

| Command | Description | Usage |
|-----------|------------|-------------|
| `ca`| Retrieve the CA Keys |`ibmcloud pag ssh ca` |
| `connect`| Connect to new ssh session for a virtual server instance|`ibmcloud pag ssh connect <virtual server address>` |
{: caption="Table 3. CLI SSH commands for {{site.data.keyword.pag_short}}}

### Kubernetes service command (`ks`)
{: #cli-kubernete-commands}

| Command | Description | Usage |
|-----------|------------|-------------|
| `config`| Connect to the Gateway and initialise Gateway for proxying IBM Cloud Kubernetes Service clusters |`ibmcloud pag ks config <target-cluster-name>` |
{: caption="Table 4. CLI KS commands for {{site.data.keyword.pag_short}}}

### RedHat Openshift command (`oc`)
{: #cli-openshift-commands}

| Command | Description | Usage |
|-----------|------------|-------------|
| `config`| Connect to the Gateway and initialise Gateway for proxying IBM Cloud RedHat Openshift Service clusters |`ibmcloud pag oc config [--passcode <passcode>]` |
{: caption="Table 5. CLI RedHat Openshift commands for {{site.data.keyword.pag_short}}}

 User is prompted on the above to provide a [One time code](https://identity-1.us-south.iam.cloud.ibm.com/identity/passcode) when `--passcode` parameter is not provided.
{: note}

### Session commands (`sessions`)
{: #cli-session-commands}

| Command | Description | Usage |
|-----------|------------|-------------|
| `list`| Display list of sessions |`ibmcloud pag session list` |
| `terminate`| [Future] Terminate session based on session id |`ibmcloud pag session terminate <session-id>` |
{: caption="Table 6. CLI session commands for {{site.data.keyword.pag_short}}}

### Play command (`play`)
{: #cli-play-commands}

| Command | Description | Usage |
|-----------|------------|-------------|
| `play`| Play recorded session contents from the given file |`ibmcloud pag play <path-to-file>` |
{: caption="Table 7. CLI play commands for {{site.data.keyword.pag_short}}}
