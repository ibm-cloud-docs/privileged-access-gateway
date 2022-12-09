---

copyright:
  years: 2022
lastupdated: "2022-12-09"

keywords: PAG UI, UI, CLI

subcollection: privileged-access-gateway

---

{{site.data.keyword.attribute-definition-list}}

<!-- Removed this topic from Experimental release. 08032022 PW -->

# Provisioning {{site.data.keyword.pag_full}} using IBM Cloud CLI
{: #pag-provisioning-cli}

For first-time users of ibmcloud CLI, reference this link : [Getting started with the IBM Cloud CLI](https://cloud.ibm.com/docs/cli?topic=cli-getting-started)

## Step 1. Logging in to the IBM Cloud account
{: #pag-provisioning-cli-logging-cloud-acct}

```sh
$ ibmcloud login --sso -a test.cloud.ibm.com -r us-south -c e7f84207f02a401784384cc02a128387 -g Default
```
This will log in and set the designated account as well as the us-south region and Default resource group.

## Step 2. Creating the {{site.data.keyword.pag_short}} service
{: #pag-provisioning-cli-create-pag-service}

```sh
$ ibmcloud resource service-instance-create NAME SERVICE_NAME SERVICE_PLAN_NAME LOCATION [-p, --parameters @JSON_FILE | JSON_STRING ]
```

Here the NAME is the Arbitrary name that is given to the instance, SERVICE_NAME is `privilege-access-service`, for SERVICE_PLAN_NAME pick the `lite` plan, LOCATION is the location where is it to be deployed, use `global` here.
The parameters to be passed include :

- cosinstance
- cosbucket
- cosapikey
- subnetcrn

These are similar to the ones that need to be provided while provisioning by using the UI.
Refer to the above section on how `To get the Cloud Object Storage Instance CRN, Bucket Name and the API key`
Sample Command :

```sh
ibmcloud resource service-instance-create test-instance-123 privileged-access-gateway lite global -p '{"cosinstance":"crn:v1:staging:public:cloud-object-storage:global:a/fa806bc113a24f6880f01631eb9b08a8:8c8b1697-42d2-4c19-a8a9-6accf866991f::","cosbucket":"pag-dev-cos-cos-standard-t0a","cosapikey":"your-cos-api-key","subnetcrn":"crn:v1:staging:public:is:us-south-1:a/1b05234f0a46a4fe52ca6411ba9352af::subnet:0716-f5cfcb99-0cab-4363-a9d1-0476451586b0"}'
```
