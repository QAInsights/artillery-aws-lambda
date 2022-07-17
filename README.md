# Artillery AWS Lambda

## AWS Credentials

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "CreateOrGetLambdaRole",
            "Effect": "Allow",
            "Action": [
                "iam:CreateRole",
                "iam:GetRole"
            ],
            "Resource": "arn:aws:iam::<REPLACE_ACCOUNT_NUMBER>:role/artilleryio-default-lambda-role"
        },
        {
            "Sid": "CreateLambdaPolicy",
            "Effect": "Allow",
            "Action": [
                "iam:CreatePolicy",
                "iam:AttachRolePolicy"
            ],
            "Resource": "arn:aws:iam::<REPLACE_ACCOUNT_NUMBER>:policy/artilleryio-lambda-policy"
        },
        {
            "Sid": "SQSPermissions",
            "Effect": "Allow",
            "Action": [
                "sqs:*"
            ],
            "Resource": "arn:aws:sqs:*:<REPLACE_ACCOUNT_NUMBER>:artilleryio_test_metrics*"
        },
        {
            "Sid": "LambdaPermissions",
            "Effect": "Allow",
            "Action": [
                "lambda:InvokeAsync",
                "lambda:CreateFunction",
                "lambda:DeleteFunction"
            ],
            "Resource": "arn:aws:lambda:*:<REPLACE_ACCOUNT_NUMBER>:function:artilleryio-*"
        },
        {
            "Sid": "S3Permissions",
            "Effect": "Allow",
            "Action": [
                "s3:DeleteObject",
                "s3:GetObject",
                "s3:PutObject",
                "s3:ListBucket",
                "s3:GetLifecycleConfiguration",
                "s3:PutLifecycleConfiguration"
            ],
            "Resource": [
                "arn:aws:s3:::artilleryio-test-data-*",
                "arn:aws:s3:::artilleryio-test-data-*/*"
            ]
        }
    ]
}
```

## Install Node JS and Artillery

```
sudo dnf module install nodejs:16 -y

npm version

sudo npm install -g artillery
```
