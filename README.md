# cfn-modules: AWS Secrets Manager secret

AWS Secrets Manager secret with encryption.

## Install

> Install [Node.js and npm](https://nodejs.org/) first!

```
npm i @cfn-modules/secret
```

## Usage

> If you pass in a [KMS Module](https://github.com/cfn-modules/kms-key) the key will be used to encrypt the secret.

```
---
AWSTemplateFormatVersion: '2010-09-09'
Description: 'cfn-modules example'
Resources:
  Secret:
    Type: 'AWS::CloudFormation::Stack'
    Properties:
      Parameters:
        KmsKeyModule: !GetAtt 'Key.Outputs.StackName' # optional
        Name: 'my-secret-name' #optional
        Description: 'A secret description' #optional
        CharactersToExclude: '"@/\' # optional
        PasswordLength: 30 # optional
      TemplateURL: './node_modules/@cfn-modules/secret/module.yml'
```

## Examples

none

## Related modules

* [kms-key](https://github.com/cfn-modules/kms-key)

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
      <td>KmsKeyModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/kms-key">kms-key module</a></td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>Name</td>
      <td>The name to give the secret. This is the name shown in the AWS Console</a></td>
      <td>auto generated value</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>Description</td>
      <td>The description to give the secret. This is the description shown in the AWS Console</a></td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>CharactersToExclude</td>
      <td>When generating the initial value these characters will not be used.</a></td>
      <td>'"@/\'</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>PasswordLength</td>
      <td>The length of the generated password.</td>
      <td>30</td>
      <td>no</td>
      <td></td>
    </tr>
  </tbody>
</table>

## Wrapper

If you want to use an existing Secret, use the wrapper with the `Arn` of the existing secret:

```
---
AWSTemplateFormatVersion: '2010-09-09'
Description: 'cfn-modules example'
Resources:
  Secret:
    Type: 'AWS::CloudFormation::Stack'
    Properties:
      Parameters:
        Arn: 'arn:aws:secretsmanager:eu-west-1:111111111111:secret:name/of/secret' # required
      TemplateURL: './node_modules/@cfn-modules/secret/wrapper.yml'
```
