# Ado_Download_Securefile.ado

Use this Azure template to download a secure file contents in azure agent.Once downloaded, use the name value that is set on the task (or "Reference name" in the classic editor) to reference the path to the secure file on the agent machine. For example, if the task is given the name mySecureFile, its path can be referenced in the pipeline as $(mySecureFile.secureFilePath).

## Parameters

The pipeline requires the following parameters to be defined:

| Name  | About | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | :-------------: | :-------------: | ------------- | :-------------: | ------------- |
| secureFile | Name of Secure File | string |  | | Required |Specifies the name or unique identifier (GUID) of the secure file that is downloaded to the agent machine. The file is deleted when the pipeline job completes.|
| retryCount | Count Retrial of dowload | string |'8' | | Optional | Specifies the number of times to retry downloading a secure file if the download fails. |
| socketTimeout  | Timeout for request sent | string | |  | Optional | downloading a secure file request in Microsoft, this input specifies the timeout for a socket. |

--------------------------------------------------------------------------------------------------------------------------------------------------

These parameters provide multiple use case options for the template, enable/disable flags for the utilization of different templates as per the requirements.

## Use Cases

You can directly call a particular template as per the requirement. for example:

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/Ado_Download_Securefile.ado
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: Ado_Download_Securefile.yml@Template
    parameters:
    secureFile: 'ssh_key.pem'
```

* Note: Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.
