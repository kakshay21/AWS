# Tutorial for setting development Pipelines
## Step I: Configure AWS EC2 and install AWS codeDeploy Agent
#### Follow [this link](http://docs.aws.amazon.com/codepipeline/latest/userguide/tutorials-simple-codecommit.html)
Step 3 in that link has the information, that we are doing first. So follow it upto step 11 under the step 3.

Now that our EC2 is configured. Use your .pem file to SSH into the AWS instance. And use this command to test whether CodeDeploy Agent is installed or not.

```
sudo service codedeploy-agent status
```
If it shows any error then we need to install it. Follow [this link](http://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent-operations-install.html)

## Step II: Create IAM user
Now we need to create IAM role and a User

For this task follow [this link](http://docs.aws.amazon.com/codedeploy/latest/userguide/getting-started-create-iam-instance-profile.html)
. It's always better to concider console method rather than trying it through console.
And one more advice it's better to let that user have full control over EC2, S3, CodeCommit, CodeDeploy and CodePipiLines. Once
Everthing is setup we can experiment and let it work in more restrictive way as per your requirements.

## Step III: Create CodeCommit 
Follow [this link](http://docs.aws.amazon.com/codecommit/latest/userguide/getting-started.html)

Only step 1 in the above link is required but you can reffer to it for git usage.

Create SSH and git crediential in the [IAM](https://console.aws.amazon.com/iam). It will be present in the security crediential of User section

Now You can proceed in two ways either use SSH for using git which i reccomend the most or just by installing [aws CLI](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)

The above link shows how to install aws CLI. Once it is installed 

run this command to configure aws cli

```
$ aws configure
```

please enter the appropriate values as per you credentials from the IAM use you've created in the step II. That includes Access Key Id and Secret Access Key

```
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: ap-southeast-1
Default output format [None]: json
```
Once it's done, upload a sample file to codeCommit. you can follow [this link](https://github.com/kakshay21/AWS/blob/master/awsCodeCommit.md) that I've created.

What I mean by the sample file is [this setup](https://github.com/kakshay21/AWS/blob/master/SampleApp_Linux.zip)

Now push it to the master of CodeCommit

## Step IV: Configure CodeDeploy
Follow [this guide](http://docs.aws.amazon.com/codedeploy/latest/userguide/getting-started-wizard-in-place.html) to create a sample CodeDeploy.

## Step V: Configure CodePipeline
if you've followed the guide correctly, this will be the last step. 
codePipeLine is available [here](http://console.aws.amazon.com/codepipeline)

1. Click on "Get started" or if you have already created any pipelines before create a new pipeline.

2. Enter a pipeline name

3. Set service provider to "AWS Code Commit" int the source tab

4. Enter the repo name and the branch you choose for the deployment. Remember you've configure it in step III.

5. We don't want to build anything we just skip it to Deploy. Under this set the provider to "AWS Code Deploy"

6. Now enter the name of the Code Deploy you've configure in the step IV.

7. Create a Service Role for this case you need to create a new just walk through it. It will setup all the policy and permission 
 that it need. You don't need to alter anything unless you know what you're doing.
 
 You've followed correctly this will create a pipeline with one CodeCommit and one CodeDeploy. But that's not why you came here
 we want to build a pipeline with as many CodeCommit and as many CodeDeploy.
 
 So one way of doing it add seperate CodeDeploy and seperate CodeCommit to this existing pipeline but that's not efficient either.
 
 So we will create different branch for different user and deploy it on same server but different CodeDeploy unit which is configured
 to take different branch as a source instead of different repository and deplot it on the same EC2 instance.
 
 Sounds difficult? It's fairly easy!
 
 ## Actual tutorial starts from here
 Go to [CodePipeLine](http://console.aws.amazon.com/codepipeline) console.
 
 
