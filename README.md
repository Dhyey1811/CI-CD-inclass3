## Automated Infrastructure Deployment with AWS CloudFormation and CodePipeline
## Objective
To set up an automated CI/CD pipeline using AWS CodePipeline that provisions AWS resources using CloudFormation.
## Lab Requirements
## 1. Create a Simple CloudFormation Template
- Define a CloudFormation YAML or JSON template that creates an S3 bucket.
- Include parameters for bucket name and versioning (Enabled/Suspended).
- Validate the template using AWS CLI:
aws cloudformation validate-template --template-body file://s3-bucket-template.yaml
## 2. Set Up a GitHub Repository
- Create a new GitHub repository.
- Push your CloudFormation template to a specific branch (e.g., main or deploy).
## 3. Configure CodePipeline
Create a new pipeline with the following stages:
- Source: Connect to your GitHub repository and monitor the chosen branch.
- Deploy: Use AWS CloudFormation as the deploy provider.
- Specify stack name and select the template file from source.
- Provide ParameterOverrides like:
{
  "BucketName": "dpatel8965482",
  "VersioningStatus": "Enabled"
}
## 4. Automate Deployment Triggers
- Ensure the pipeline triggers on code changes pushed to the branch.
- Test by editing the template (e.g., adding a new AWS service or modifying existing resource).
## 5. Verify and Clean Up Resources
- Confirm the S3 bucket creation in AWS Console.
- After verification, delete the stack to avoid ongoing charges.
IAM Permissions
Ensure the CodePipeline service role has the necessary CloudFormation permissions:
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "*",
      "Resource": "*"
    }
  ]
}
Troubleshooting
- Ensure all JSON used in ParameterOverrides is valid and clean.
- Confirm that parameter names in override exactly match the template.
- Avoid copying from formatted documents to prevent hidden characters.
