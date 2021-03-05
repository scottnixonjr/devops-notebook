# AWS CLI

This guide favors v2 of the cli.

`aws ecr get-login` is more secure and should replace all uses of `$(aws ecr get-login -no-include-email)`

Example of how to pass it to docker.
`aws ecr get-login-password | docker login --username AWS --password-stdin MY-REGISTRY-URL`

## Assume Role:

`aws sts assume-role --role-arn "arn:aws:iam::${AWS::Account}:role/${ROLE_NAME}" --role-session-name AWSCLI-Session`

{
    "Credentials": {
        "AccessKeyId": "XXXXXXXXXXXXX",
        "SecretAccessKey": "XXXXXXXXXXXXX",
        "SessionToken": "XXXXXXXXXXXXXH+/j8lm5YkyjjCKyAUnoyt0FXl6CN3L6uERiRHElx07ToKA7Us7LIM2c036h2XXXXXXXXXXXXXXbb+XQM6tRwYg4FRgntDXXXXXXXXXXXXXDpvA0/90npc8OYN4TGiTfWHPnQpsCm6VOHvVTuMLdruR9A8Gl5+p63C9PiXQu48DMinKahRFXEutFF0VAu5rSa4lMigSNH1FbGsotcrxgAYyLcN8z0VvDhlcTsNqzZN2zTRHN/Uu313rU8JK/XXXXXXXXXXXXXfg==",
        "Expiration": "2021-02-04T22:20:53Z"
    },
    "AssumedRoleUser": {
        "AssumedRoleId": "XXXXXXXXXXXXX:AWSCLI-Session",
        "Arn": "arn:aws:sts::XXXXXXXXXXXXX:assumed-role/example-role-name/AWSCLI-Session"
    }
}

```
export AWS_ACCESS_KEY_ID=XXXXXXX
export AWS_SECRET_ACCESS_KEY=XXXXXXX
export AWS_SESSION_TOKEN=XXXXXXX
export AWS_DEFAULT_REGION=us-east-1
```

Get Session 

`aws sts get-caller-identity`

>{
>    "UserId": "XXXXXXXXXXXXX:AWSCLI-Session",
>    "Account": "XXXXXXXXXXXXX",
>    "Arn": "arn:aws:sts::XXXXXXXXXXXXX:assumed-role/example-role-name/AWSCLI-Session"
>}