# nyu-cloud-computing-spring-22-a3-spamClassifier

A spam classifier using AWS SageMaker, Lambda, S3, CloudFormation.

### Problem Statement
Problem statement is in file _problem_statement.pdf_.

### Code Directory Structure
1. _aws_lambda_: contains zip files for lambda functions and layers used.
2. _aws_cloudformation_: contains the CloudFormation template as _.yaml_ file.

### How to reproduce the project?

#### Pre-requisites
1. Must have AWS account.
2. Must have a hosted Sagemaker model & "Endpoint Name" after already having completed Step 1. and 2. from the
   _problem_statement.pdf_.
3. Must have configured and verified an **email id** in SES for sending and receiving emails on AWS. 

#### Steps
1. Create an S3 bucket and upload all the _.zip_ files from ~/_aws_lambda_ directory. Note the names of
   the **s3 bucket** and **all uploaded files** (along with what resource (function/layer) they
   represent) since we will need those in further steps.
2. Open CloudFormation Console and use _~/aws_cloudformation/spamClassifier.yaml_ as a template and
   continue.
   - Make sure all the parameter values make sense as per your AWS region and current account state
     (refer _Step 1._ results and _Pre-requisites_ to determine what values to change).
   - Change values of any applicable parameters like **LambdaCodeBucket**, **LambdaFunctionName**,
     et cetera.
   - As a safe choice, try to keep **LambdaFunctionName** as random as possible (to avoid CloudFormation
     **getting stuck** issues due to dangling "deleted" bucket names).
3. Click Continue and start creating your stack. If everything goes well, you should have all the
   required resources hosted.
4. Finally, go to SES "Email Receiving" and set the "rule set" which you just created with cloud
   formation as "Active".
5. Try sending an email from your Gmail account (or any other mail server) to _AWS email id_ (the one
   which you configured and verified in **Pre-requisites #3**). You should get back the AWS' Spam
   Classifier results within a few seconds.

