# EC2 Metadata Services

By default, both v1 and v2 are available to use.

## Service Version 2

IMDSv2 users session requests which requires creating a session token configured between 1 second to a max of 6 hours. 


```
TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` \
&& curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/
```

Enable v2
`aws ec2 modify-instance-metadata-options --instance-id $INSTANCE_ID --http-tokens required --http-endpoint enabled --region $REGION`

One liner if you are running it on an instance. 
```
INSTANCE_ID=$(curl -X GET "http://169.254.169.254/latest/meta-data/instance-id/") REGION=$(curl -X GET "http://169.254.169.254/latest/meta-data/placement/region/") aws ec2 modify-instance-metadata-options --instance-id $INSTANCE_ID --http-tokens required --http-endpoint enabled --region $REGION
```

Starting new instances with v2.
```
aws ec2 run-instances 
    --image-id ami-0abcdef1234567890 
    --instance-type c3.large 
	...
    --metadata-options "HttpEndpoint=enabled,HttpTokens=required"
```

