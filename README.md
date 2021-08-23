
# Guidelines to publish the respository

Checklist to maintain the quality of the IBM Cloud open source repository for Schematics. Follow the do's and don'ts to publish your repository in https://github.com/Cloud-Schematics. 

## Do's and Don'ts for Terraform template creation
Some of the `must do` and `should have` task for the Terraform templates are:

### Must do
- Create Terraform template by using Terraform version0.13 or higher. For latest releases, refer to [IBM Cloud provider](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest).
- Ensure the Terraform related files such as `main.tf`, `versions.tf`, etc., are placed in a root folder.
- Ensure your repository contains `versions.tf` to run the required Terraform version. For `versions.tf`, refer to [sample versions tf file](https://cloud.ibm.com/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-setup_cli#install-provider-v13). 
- Ensure pre-commit hooks are executed to inspect your code meets Terraform standards. Refer to [sample repository that contains pre-commit hook](https://github.com/terraform-ibm-modules/terraform-ibm-iam/blob/main/.pre-commit-config.yaml).
- Prepare `README.md` that explains the **title**, **short description**, **version requirements**, **about examples**, **modules**, **prerequisites**, **input and output variables** with description, **steps to run the example or modules**, **verification**, **troubleshooting tips**, and **reference** from your repository. For more information, see [README template](README_Template.md). 
- Ensure your repository uses Terratest framework to validate your Terraform resources and data source to provision. Refer to [sample validated Terraform repository](https://github.com/terraform-ibm-modules/terraform-ibm-iam/blob/main/.github/workflows/validate_terraform.yml) to run Terratest. 
- [Optional] Use IBM Cloud Provider for Terraform modules for the simple configuration of your infrastructure. For more information, about IBM Cloud Provider for Terraform modules, see [Terraform getting started module](https://github.com/terraform-ibm-modules/getting-started).
- Ensure the variables and outputs must have one or two sentence descriptions that explains the purpose of the variables.
- Ensure your repository contains gitignore for any files that are not tracked by git remain untracked.
- Add required license file for your template.
- Run secrets manager test by using detect secret tool.
- Migrate your template to the latest versions. For example, migrate repository templates using Terraform v0.11 to Terraform v0.13 or higher.
- `Release tags` - Tags are used to identify template versions. Release tag names must be a semantic version, which can optionally be prefixed with `v`. For example, v1.0.0.
- Archive your template in a `.tgz` file extension format to onboard to your private catalog. The size of the `.tgz` must be `<=40MB`. <br> **Note** If you .tgz file size if greater than 40 MB, Use `rm -rf .git .gitignore` command to reduce the size of the `.tgz` file and create `tar czfv <reponame>.tgz .`.

### Should have

- Add tags for your template to ease user search operation.

### Don'ts
- Assume having a reference for the steps is good enough. The CLI steps and link to the API/SDK references if any, to be provided for the example.
- Add any secret, sensitive data in files, and password values of the parameters.


## Do's and Don'ts for Ansible action creation
Some of the `must do` and `should have` task for the Ansible actions repositories are:

### Must do
- Create the template by using the latest version of the Ansible.
- Prepare `README.md` that explains the **title**, **short description**, **version requirements**, **about examples**, **modules**, **prerequisites**, **input and output variables** with description, **steps to run the example or modules**, **verification**, **troubleshooting tips**, and **reference** from your repository. For more information, see [README template](README_Template.md). 
- Create an [Ansible playbook](https://cloud.ibm.com/docs/schematics?topic=schematics-create-playbooks) templates by using Schematic action standard. For sample template on Schematic action creation, see [Sample Ansible playbook templates for Schematics actions](https://cloud.ibm.com/docs/schematics?topic=schematics-sample_actiontemplates).
- Automate your [Action templates](https://cloud.ibm.com/docs/schematics?topic=schematics-sample_actiontemplates). For more information, about using both Terraform and Action template, see [Provisioning a LAMP stack on Virtual Servers for VPC](https://github.com/Cloud-Schematics/lamp-simple) to setup the infrastructure in Schematics.
- Ensure your repository contains gitignore for any files that are not tracked by git remain untracked.
- Ensure the variables and outputs must have one or two sentence descriptions that explains the purpose of the variables.
- Run secrets manager test by using detect secret tool.
- Add required license file for your template.
- Archive your template in a `.tgz` file extension format to onboard to your private catalog. The size of the `.tgz` must be `<=40MB`. <br> **Note** If you .tgz file size if greater than 40 MB, Use `rm -rf .git .gitignore` command to reduce the size of the `.tgz` file and create `tar czfv <reponame>.tgz .`.
- `Release tags` - Tags are used to identify template versions. Release tag names must be a semantic version, which can optionally be prefixed with `v`. For example, v1.0.0.

### Should have

- Add tags for your templatet to ease user search operation.

### Don'ts
- Assume having a reference for the steps is good enough. The CLI steps and link to the API/SDK references if any, to be provided for the example.
- Add any secret, sensitive data in files, and password values of the parameters.
