# EC2 Image Builder

[AWS Documentation](https://docs.aws.amazon.com/imagebuilder/latest/userguide/image-builder-component-manager-local.html)

AWSTOE is used to validate configuration files.

[Install for linux](https://awstoe-us-east-1.s3.us-east-1.amazonaws.com/latest/linux/amd64/awstoe) 

`awstoe validate --documents myfile.yaml`


Log upload permissions.

```
“Statement”: [
     {
         “Effect”: “Allow”,
         “Action”: [
             “logs:CreateLogStream”,
             “logs:CreateLogGroup”,
             “logs:PutLogEvents”
         ],
         “Resource”: “arn:aws:logs:*:*:log-group:/aws/imagebuilder/*”
     }
]
```