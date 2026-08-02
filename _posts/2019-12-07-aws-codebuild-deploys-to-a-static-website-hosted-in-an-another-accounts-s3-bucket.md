---
title: "AWS Codebuild deploys to a static website hosted in an another account’s s3 bucket"
tags: [aws, continuous delivery, devops, s3]
description: "So you have a codebuild project running in Account A & you want to deploy some artifacts(static files) into an s3 bucket in Account B! Cross Account…"
original_date: 2019-12-07T15:17:46-08:00
---

So you have a codebuild project running in **Account A** & you want to deploy some artifacts(static files) into an s3 bucket in **Account B**!

![](/assets/img/posts/aws-codebuild-deploys-to-a-static-website-hosted-in-an-another-accounts-s3-bucket/1-iPCFTcIkjYh_salmg0zW3w.png)

Cross Account s3 Access

After you are done fiddling with injecting AWS keys it’s time to try out using IAM roles.

### In Account A

1. Create an IAM role for your codebuild
2. Create a policy for this role

```
{
 "Version": "2012-10-17",
 "Statement": [
 {
 "Sid": "VisualEditor0",
 "Effect": "Allow",
 "Action": [
 "s3:PutObject",
 "s3:GetObject",
 "s3:PutObjectAcl"
 ],
 "Resource": [
 "arn:aws:s3:::my-bucket-dev/*",
 "arn:aws:s3:::my-bucket-stage/*",
 "arn:aws:s3:::my-bucket-prod/*"
 ]}]
}
```

3. Attach this policy to the role. Ensure you have given PutObject to write to s3. PutObjectAcl see Gotcha below

### In Account B

1. Update the public policy of the s3 bucket

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::my-bucket-dev/*"
        },
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::AccountA_Number:role/CodebuildIAMRole"
            },
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": "arn:aws:s3:::my-bucket-dev/*"
        }
    ]
}
```

It’s a handshake policy where you update the same permissions in the two accounts that are going to talk.

### Gotchas

AWS s3 has a behavior where the owner of the s3 bucket (here Account B) might not have access to it’s objects if the object is created by a different account (Account A). So you might have to update the acl permissions while you write the s3 file. In my case I am doing a simple copy of index.html file. So my codebuild project actually calls this line

```
aws cp index.html s3://my-bucket-dev/index.html --acl public-read
```

### References

1. <https://aws.amazon.com/premiumsupport/knowledge-center/cross-account-access-s3/>
2. <https://aws.amazon.com/premiumsupport/knowledge-center/s3-bucket-owner-access/>
