---
title: "Create a Node.js aws-lambda using Serverless framework"
tags: [aws, aws lambda, nodejs, serverless]
description: "Boring Description: As you might already know AWS lambda is about deploying a payload/function/unit to Amazon Infrastructure. Pros: Once deployed you…"
original_date: 2016-11-26T16:13:09-08:00
---

**Boring Description:** As you might already know AWS lambda is about deploying a payload/function/unit to Amazon Infrastructure.

> Pros: Once deployed you don’t have to worry about scaling, load balancing and all the ops.

**Why** [**Serverless**](https://github.com/serverless/serverless) **Framework?:** Well it is just a way to automate/script your payload deployment to AWS instead of manually uploading your artifacts.

---

**Step 1 :**

AWS setup.

Give the IAM user admin privileges in your AWS account. (Not necessary but it is good for bootstrapping)

**Step 2:**

Install serverless globally through npm

- `npm install -g serverless`

**Step 3:**

Create a template (not necessary as long as you the 3 files it generates)

- `sls create -t aws-nodejs --path hello-node-lambda`

```
Note: You can serverless or sls as the command and
 -t for  --template
```

You must see a message like this.

![](/assets/img/posts/create-a-node-js-aws-lambda-using-serverless-framework/1-DhFB-9j9Ou5BtawgAhlWzA.png)

The folder structure of the template will be like this:

![](/assets/img/posts/create-a-node-js-aws-lambda-using-serverless-framework/1-5bd3Nn4lpAd1m1Va3vyhEA.png)

Modify handler.js to this:

```
'use strict';
module.exports.firstHello = (event, context, callback) => {
 const response = {
 statusCode: 200,
 body: JSON.stringify({
 message: 'First Hello from the other side ….',
 input: event,
 }),
 };
callback(null, response);
// Use this code if you don't use the http event with the LAMBDA-PROXY integration
 // callback(null, { message: 'Go Serverless v1.0! Your function executed successfully!', event });
};
module.exports.secondHello = (event, context, callback) => {
 const response = {
 statusCode: 200,
 body: JSON.stringify({
 message: 'Second Hello from the other side ….',
 input: event,
 }),
 };
callback(null, response);
// Use this code if you don't use the http event with the LAMBDA-PROXY integration
 // callback(null, { message: 'Go Serverless v1.0! Your function executed successfully!', event });
};
```

First Hello & Second Hello are our 2 hello lambda functions.

Now in serverless.yml

```
service: hello-node-lambda
provider:
 name: aws
 runtime: nodejs4.3
functions:
 firstHello:
 handler: handler.firstHello
 secondHello:
 handler: handler.secondHello
```

Be cautious about the indentation. It is very touchy about that!

Once we have this ready.

---

**Step 4:** Deploy

```
sls deploy -v
```
![](/assets/img/posts/create-a-node-js-aws-lambda-using-serverless-framework/1-6lM0QSgAIaX_aIxm0xy7UA.png)

Once you see this your deploy is done. You might have some issues here if you don’t give admin access to your IAM role/user.

---

**Step 5:** Testing!

```
sls invoke -f firstHello -l
```

This will invoke your lambda on aws

![](/assets/img/posts/create-a-node-js-aws-lambda-using-serverless-framework/1-8EKGWxXuT2493aW44lnuAA.png)

You can always login to AWS web portal to visualize your lambda.

![](/assets/img/posts/create-a-node-js-aws-lambda-using-serverless-framework/1--AXkq-lMGirdUOOaNEXdtw.png)

AWS Web Portal

You can invoke/test the lambda online too.

**Last thought**

You can change the code on the fly if you like to go the cowboy style! (If you can maintain it that is)

![](/assets/img/posts/create-a-node-js-aws-lambda-using-serverless-framework/1-PgidtcTRmRJUnr-r80Y6FA.png)
