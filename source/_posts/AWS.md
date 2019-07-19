---
title: AWS
date: 2019-07-18 21:05:08
tags:
---

## S3
### Disable “delete” option for S3 objects in AWS
1. Attach policy to your IAM user(s) that Deny s3:DeleteObject action


2. Configure bucket policy (Permissions -> Bucket Policy) that will Deny s3:DeleteObject action
For example, bucket policy can look like this:

```
{
    "Version": "2012-10-17",
    "Id": "<...>",
    "Statement": [
        {
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:DeleteObject",
            "Resource": "arn:aws:s3:::<YOUR BUCKET NAME>/*"
        },
        <...>
    ]
}
```