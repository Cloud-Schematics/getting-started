
# Title

_The title must summarize the goal of the example, such as `Setting up IBM WebSphere Application Server on IBM Cloud virtual servers with Schematics` or `Running cloud operations on VPC Virtual Server instances with Schematics`. Use proper IBM Cloud service names._

**SHORTDESC**

_Provide 1-2 sentences of what the example is supposed to do and the cloud resources that are affected by this example. Use links to the IBM Cloud resource documentation so that users can read about the product if they want to._

IBM Cloud Schematics provides powerful tools to automate your cloud infrastructure provisioning and management process, the configuration and operation of your cloud resources, and the deployment of your app workloads.
To do so, Schematics leverages open source projects, such as Terraform, , OpenShift, Operators, and Helm, and delivers these capabilities to you as a managed service. Rather than installing each open source project on your workstation, and learning the API or CLI. You declare the tasks that you want to run in IBM Cloud and watch Schematics run these tasks for you. For more information about Schematics, see [About IBM Cloud Schematics](https://cloud.ibm.com/docs/schematics?topic=schematics-about-schematics).

## Version requirements

_Specify the Terraform and provider version that your example supports when testing in Schematics as stated in the example._

|Name|Versions|
|--|--|
| Terraform | >=0.13 |

IBM Cloud Providers

|Name|Versions|
|--|--|
| ibm | >= 1.22.0 |
| sysdig | >= 0.5.0 |

## About this example

_Provide an overview of included example, how the example works, an architecture overview of what the example does._
This repository includes the following example that you can use to run cloud operations on an IBM Cloud VPC Virtual Server instance.

- **start-vsi-example.yaml** Use this example to start an IBM Cloud VPC Virtual Server instance.
- **stop-vsi-example.yaml** Use this example to stop an IBM Cloud VPC Virtual Server instance.
- **reboot-vsi-example.yaml** Use this example to restart an IBM Cloud VPC Virtual Server instance.
- **main.tf** Lists the data and resources used in this example.

## Modules

_List the Terraform modules or the Terraform templates used in this example._

This is a collection of modules that make it easier to provision a cloud object stoarge on IBM Cloud Platform:

[COS Instance](https://github.com/terraform-ibm-modules/terraform-ibm-cos/tree/master/modules/instance)
[COS Bucket](https://github.com/terraform-ibm-modules/terraform-ibm-cos/tree/master/modules/bucket)

## Prerequisites

_Include all the steps that must be completed to run this example in Schematics. These actions include paid IBM Cloud accounts, IAM permissions, IBM Cloud services that must be provisioned, or data that must be retrieved. Each prerequisite must include the steps that you need to take to complete it. If these steps are already documented in IBM Cloud, provide the link to the documentation as part of the prerequisite description._

**Steps**

* Make sure that you have the required permissions to [create an IBM Cloud Schematics action](https://cloud.ibm.com/docs/schematics?topic=schematics-access).
* Make sure that you have the required permissions to [create and work with IBM Cloud VPC infrastructure components](https://cloud.ibm.com/docs/vpc?topic=vpc-iam-getting-started).
* [Getting started with VPC](/docs/vpc?topic=vpc-creating-a-vpc-using-the-ibm-cloud-console)
* [VSI instance UI](https://cloud.ibm.com/vpc-ext/compute/vs)

## Input variables

_List all the input variables that are required or optional for the example. Also include the information of how to retrieve the variable value, the data type, and if this value is required or optional. Make sure to include why this input variable is needed. For example,_

The following inputs must be provided to provision the resource for this example:

|Input variable|Required/ optional|Data type|Description|
|--|--|--|--|
|`instance_ip`|Required|String|The private or public IP address of your VPC Gen2 Virtual Server instance. You can retrieve the IP address by doing XYZ|

## Output variables

_List all the output variables that are displayed for the example. Also include the information of how to retrieve the variable value, the data type. For example,_

You can access the following output reference after your resource is created.

|Output variable|Data type|Description|
|--|--|--|
|`instance_name`|String|The name of the instance.|

## Running the example in Schematics by using console

_Add detailed steps for how to create the Schematics action from the UI, specify input variables, define the resource inventory, and so on. Steps must be provided as an ordered list. For each step make sure to think about why the user must run this step, any links that you can provide to get the user to the right place, and to provide sample screen caps. Use bold tags and code ticks to highlight console field names and values that the user needs to enter. Make sure to also include verification steps so that the user can check whether running the example was successful._

**Sample steps to create an action**


1. To create an action, click [VPC Virtual Server instances template](https://cloud.ibm.com/schematics/actions/create?name=-is-instance-actions&url=https://github.com/Cloud-Schematics/-is-instance-actions){: external}.
2. Edit an action name, resource group, and the region where you want to create an action. Then, click **Create**.
3. In the Define your Action action section, enter `<GitHub_URL>` in the **GitHub or GitLab repository URL** field.
4. Optionally, enter the **Personal access token** of your private repositories.
4. Click **Retrieve example**.
5. Select the **example_name** example. Supported example are **start-vsi-example.yaml**, **stop-vsi-example.yaml**, and **reboot-vsi-example.yaml**.
6. Select the **Verbosity** level to control the level of output produce as the example runs.
7. Click **Advanced options** to define your input variables for your example.
8. Enter **Key** and **Value** as stated in the input variables section. Optionally, check **Sensitive** to hide your value.
9. Click **Add input value** to define more variables for your example.
10. Click **Next** to save your action sections. Observe the action page status run to view the **pending** status to **normal** status.
11. Click **Check action** to verify your action details. The **Jobs** page opens automatically. You can view the results of this check by looking at the logs. 
12. Click **Run action** to stop the virtual server instance. You can monitor the progress of this action by reviewing the logs on the **Jobs** page. 

## Running the example in Schematics by using command line

_Add detailed steps for how to create the Schematics action/workspace through command line, specify input variables, define the resource inventory, and so on. Steps must be provided as an ordered list. For each step, make sure to think about why the user must run this step, any links that you can provide to get the user to the right place. Use bold tags and code ticks to highlight field names and values that the user needs to enter. Make sure to also include verification steps so that the user can check whether running the example was successful._

**Sample payload file**

```
{
 "name": "<ACTION_NAME>",
 "description": "<DESCRIPTION>",
 "location": "<LOCATION>",
 "resource_group": "<RESOURCE_GROUP>",
  "source": {
    "source_type" : "git",
    "git" : {
      "git_repo_url": "<YOUR_REPOSITORY>"
    }
 },
 "command_parameter": "<SSH_YML_FILE>",
 "tags": [
  "string"
 ],
 "source_readme_url": "stringtype",
 "source_type": "GitHub"
}
```

**Command to create an action**

```
ibmcloud schematics action create --name ACTION_NAME [--description DESCRIPTION] --location GEOGRAPHY --resource-group RESOURCE_GROUP [--template GIT_TEMPLATE_REPO] [--example-name example_NAME] [--bastion BASTION_HOST_IP_ADDRESS] [--target-ini TARGET_HOSTS_FILE] [--credential CREDENTIAL_FILE_NAME] [--input INPUT_VARIABLES_LIST] [--input-file INPUT_VARIABLE_FILE_PATH] [--env ENV_VARIABLES_FILE_PATH] [--github-token GITHUB_ACCESS_TOKEN] [--output OUTPUT] [--file FILE_NAME] [--json] [--no-prompt]
```

## Verification

_List all the steps to [view the job](https://cloud.ibm.com/docs/schematics?topic=schematics-action-setup#action-jobs){: external}, [edit the settings](https://cloud.ibm.com/docs/schematics?topic=schematics-action-setup#action-settings){: external}, and observe the status of the job activities._

1. Verify that your virtual server instance is stopped. 
  1. From the [Virtual server instances for VPC dashboard](https://cloud.ibm.com/vpc-ext/compute/vs){: external}, find your virtual server instance. 
  2. Verify that your instance shows a `Stopped` status. 
2. Optional: Repeat the steps in this getting started tutorial and select the **start-vsi-example.yaml**, example to start your virtual server instance again.

## Delete an action

1. From the [Schematics actions dashboard](https://cloud.ibm.com/schematics/actions){: external}.
2. Decide the action name that you want to delete, click the three vertical dots against your action name. Then, click **Delete**.

## Troubleshooting

_Optionally Include all the possible known issues the user would face during a VSI operation, and list the errors that you want to share concerning action._

## Reference

_Provide any reference blog, article, or documentation mapping to an advanced level of examples._

1. [VSI instance UI](https://cloud.ibm.com/vpc-ext/compute/vs)

## Getting help

_For any help and support, see [Schematics help and support](https://cloud.ibm.com/docs/schematics?topic=schematics-schematics-help){: external}._
