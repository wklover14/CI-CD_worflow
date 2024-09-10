# CI/CD Workflow

This is a simple website used as example for creating a simple CI/CD workflow.

The workflow used github-action and terraform for creating and manging EC-2 instance on AWS. Then appleboy/ssh-action is used to connect to that instance and deploy a docker container containing the application.

## Requirements
To make the project work, you need to provide :
- Github Secrets : AWS_ACCESS_KEY_ID, AWS_BUCKET_NAME, AWS_SECRET_ACCESS_KEY, AWS_SSH_PRIVATE_KEY, AWS_SSH_PUBLIC_KEY
- A S3 bucket
- An ECR-LOGIN-AUTO profile with this policy:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ecr:GetAuthorizationToken",
        "ecr:BatchCheckLayerAvailability",
        "ecr:GetDownloadUrlForLayer",
        "ecr:BatchGetImage"
      ],
      "Resource": "*"
    }
  ]
}
```
