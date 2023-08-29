

## Pipeline Requirements

The setVariable pipeline requires the following parameters to be defined:
Paramaters:


| Name  | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| appDeploymentTarget | string | | | Required | |
| key | string | | | Required | |
| sqlJobStateAKSApps | string | | | Optional | |
| sqlJobStateWorkloadName | string | | | Optional | |
| sqlJobExtensionPointWorkloadName | string | | | Optional | |
| SQLJob_ExtensionPoint | string | | | Optional | |
| sqlJobViewStateAKSApps | string | | | Optional | |
| sqlJobViewStateWorkloadName | string | | | Optional | |
| sqlJobExtensionPointAKSApps | string | | | Optional | |
| enablesqlJobsVariables | boolean | 'true' | 'true'/'false' | Required | |


  These parameters provide multiple use case options for the setvariables templates pipeline, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

### Direct use of a template

You can directly call a particular template as per the requirement. for example: to use setup and init only.

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: github/ADO.Pipelines.Templates
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'



  steps:

  - template: frameWork/common/setVariables/templates/sqlJobsVariables.yml
      parameters:
        appDeploymentTarget: ${{parameters.appDeploymentTarget}}
        key: ${{parameters.key}}
        sqlJobExtensionPointAKSApps: claims-extpt-sqljob-$(claims.extpt.blueGreenEnv)
        sqlJobExtensionPointWorkloadName: claims-extpt-sqljob

Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.

  ```
