# aws-cv-connector-cf
THIS SCRIPT IS PROVIDED TO YOU "AS IS."  TO THE EXTENT PERMITTED BY LAW, QUALYS HEREBY DISCLAIMS ALL WARRANTIES AND LIABILITY FOR THE PROVISION OR USE OF THIS SCRIPT.  IN NO EVENT SHALL THESE SCRIPTS BE DEEMED TO BE CLOUD SERVICES AS PROVIDED BY QUALYS

CloudFormation Template to create a Qualys AWS Connector and associated cross-account trust role using the Security Audit managed policy.
To run the script you will need to supply credentials from AWS Secrets Manager for
Qualys user name and password for API access to Qualys Cloud View.
In AWS Secrets Manager create a new secret for the Qualys API username and password formatted like this:

Secret key/value

Secret key::Secret value

username your_username

password some_password

Plain text should look like:

{
  "username": "your_username",
  "password": "some_password"
}

Set BaseUrl in CloudFormation variable:
    Default: Qualys API URL for Cloud View API endpoint. See https://www.qualys.com/docs/qualys-cloud-view-user-guide.pdf page 27

SecretQAPI:
      Default: <ENTER SECRET NAME>
      Description: Secrets Manager - Secret Name
      Type: String

SecretRegion:
      Default: <ENTER REGION FOR SECRET>
      Description: Secrets Manager - Region where secret is stored
      Type: String


# External ID
You can specify a unique External ID consisting of 9-90 numeric characters in place of Empty on line 23 or if one is not supplied, the Lambda function will generate one and use that for the unique External ID.

Parameters:

...

  ExternalId:
    Default: Empty

    Description: Specify a unique number from 9-90 digits, or one will be generated for you

    Type: String

# Role Name
If you want to change the Role name you can edit these settings in line number 27

Parameters:

...

  RoleName:
    Default: CF-QualysAWSConnectorRole
