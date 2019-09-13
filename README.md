# getting-started
This repo contains some basic development information on how to develop terraform templates

It contains information and guidelines on writing terraform templates repoistory.

  * Each repositiry should have README.md which basically explains the infrastructure architecture, variables and its default values.
  
  * configuration tf files, variables.tf, outputs.tf. These are the recommended filenames for a minimal module, even if they're empty. main configuration tf file should be the primary entrypoint. For a simple module, this may be where all the resources are created. For a complex module, resource creation may be split into multiple files but any nested module calls should be in the main file. variables.tf and outputs.tf should contain the declarations for variables and outputs, respectively.
  
  * All variables and outputs should have one or two sentence descriptions that explain their purpose. 
  
  * Add LICENSE.
  
  * No secret and password values in variables.
  
  * No sensitive data in files.
  
  * Nested modules should exist under the modules/ subdirectory. Nested modules should be used to split complex behavior into multiple small modules that advanced users can carefully pick and choose.If the root module includes calls to nested modules, they should use relative paths like ./modules/consul-cluster so that Terraform will consider them to be part of the same repository or package
  
  
  

