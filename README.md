TODO: Build and badges

# cfn-modules: AWS Secret

AWS Secret with optional encryption using defined key.

## Install

TODO: NPM publish

## Usage

> If you pass in a [KMS Module](https://github.com/cfn-modules/kms-key) the key will be used to encrypt the secret.

```
---
AWSTemplateFormatVersion: '2010-09-09'
Description: 'cfn-modules secret example'
Resources:
  Key:
    Type: 'AWS::CloudFormation::Stack'
    Properties:
      Parameters:
        AlertingModule: !GetAtt 'Alerting.Outputs.StackName'
      TemplateURL: './node_modules/@cfn-modules/kms-key/module.yml'
  Secret:
    Type: 'AWS::CloudFormation::Stack'
    Properties:
      Parameters:
        KmsKeyModule: !GetAtt 'Key.Outputs.StackName'
        Name: "Project/Env/Secret"
      TemplateURL: './node_modules/cfn-modules-secret/module.yml'
```

## Parameters

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Default</th>
      <th>Required?</th>
      <th>Allowed values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Name</td>
      <td>The name that identifies the secret</a></td>
      <td></td>
      <td>yes</td>
      <td></td>
    </tr>
    <tr>
      <td>KmsKeyModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/kms-key">kms-key module</a></td>
      <td>The key used to encrypt/decrypt the secret</td>
      <td>no</td>
      <td></td>
    </tr>
  </tbody>
</table>
