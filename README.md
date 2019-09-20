[![Build Status](https://travis-ci.org/cfn-modules/secret.svg?branch=master)](https://travis-ci.org/cfn-modules/secret)
[![NPM version](https://img.shields.io/npm/v/@cfn-modules/secret.svg)](https://www.npmjs.com/package/@cfn-modules/secret)

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
        ExcludeLowercase: 'false' # optional
        ExcludeNumbers: 'false' # optional
        ExcludePunctuation: 'false' # optional
        ExcludeUppercase: 'false' # optional
        IncludeSpace: 'false' # optional
        RequireEachIncludedType: 'true' # optional
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
    <tr>
      <td>ExcludeLowercase</td>
      <td>Specifies that the generated password should not include lowercase letters. The default if you don't include this switch parameter is False, and the generated password can include lowercase letters.</a></td>
      <td>false</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>ExcludeNumbers</td>
      <td>Specifies that the generated password should not include digits. The default if you don't include this switch parameter is False, and the generated password can include digits.</a></td>
      <td>false</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>ExcludePunctuation</td>
      <td>Specifies that the generated password should not include punctuation characters. The default if you do not include this switch parameter is that punctuation characters can be included.</a></td>
      <td>false</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>ExcludeUppercase</td>
      <td>Specifies that the generated password should not include uppercase letters. The default if you do not include this switch parameter is False, and the generated password can include uppercase letters.</a></td>
      <td>false</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>IncludeSpace</td>
      <td>Specifies that the generated password can include the space character. The default if you do not include this switch parameter is False, and the generated password doesn't include space characters.</a></td>
      <td>false</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>RequireEachIncludedType</td>
      <td>Specifies whether the generated password must include at least one of every allowed character type. If you don't include this switch, the default value is True, and the generated password includes at least one of every character type.</a></td>
      <td>true</td>
      <td>no</td>
      <td></td>
    </tr>
  </tbody>
</table>
