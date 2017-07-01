# AWS-CODECOMMIT TUTORIAL

## STEP 1
###  Requirements
1. Python 2 version 2.6.5+ or Python 3 version 3.3+
2. Windows, Linux, macOS, or Unix

If you already have pip and a supported version of Python, you can install the AWS CLI with the following command:

```
pip install --upgrade --user awscli
```
then run command to verify installation

``` 
aws --version
```

In case you have any trouble, then follow [this instruction](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)

## STEP 2
### Configure aws

run this command

```
$ aws configure
```

please enter the appropriate values as per you credentials from the email. That includes Access Key Id and Secret Access Key

```
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: ap-southeast-1
Default output format [None]: json
```

# STEP 3
## Cloning the repository

```
git clone https://git-codecommit.ap-southeast-1.amazonaws.com/v1/repos/ZOOD-PWA
cd ZOOD-PWA
```

# STEP 4
## Work on your branch

Do work on your own branch and your branch id is listed in your email

``` 
git pull origin master 
```

The above command is required to update your local repo from aws repo. So do it every time before starting any new feature of your own.

Then to switch to your own branch

```
git checkout origin akshay_1234
```

in this case my branch id is akshay_1234

### One important thing to note
Here we have created two directories PLAY and PWA

Concider PWA as your master (just consider it!). You're not allowed to do anything with master unless explicitly told.

So update PLAY folder only when you're sure that this new feature it good and ready for production. We will monitor your progress based on what is present in this directory.

And now concider PLAY as your playground. You can experiment any new things, any random stuff without any issue. You can send the link of this folder for verifying without integrating it to PWA folder. 

You can start your work by creating as many branch as you want "locally" by

```
git checkout -b akshay_1234-my-new-feature
```

and when you're done with the change
```
git add *
git commit -a
```


And then add commit message to keep a track of your changes just by looking at your message

and when you're done with that push it to your aws CodeCommit branch by 
```
git push origin akshay_1234
```
### remember not to push anything in the master until you're explicitly told.

Do update your local repo with your own branch before adding any new features

```
git pull origin akshay_1234
```

### To see the changes live
For PLAY

Go to http://ec2-13-228-78-10.ap-southeast-1.compute.amazonaws.com/ANIKET/PLAY

For WPA

Go to http://ec2-13-228-78-10.ap-southeast-1.compute.amazonaws.com/ANIKET/PWA

### Changes will take 2-5 min to deploy on this server.

## Now Suppose you want to share yout code with other member
Just tell them your branch name and then can pull it on another locally temporary branch.

Just make sure you're done with your work and checkout to master by typing
```
git checkout master
```
Now create a branch so that you don't disturb the master
``` 
git checkout -b myTempBranch
```
now pull your teammate code here. Let's suppose your teammate branch is "USER1-branch"
```
git pull origin USER1-branch
```
Now if you see the code locally you'll actually see the codes of your teammate.
## This guide is only for Admin who is given a task to merge to master

Now suppose you need to merge the changes to a production ready branch i.e master. For this scenario let's say you've a team leader who is given rights to merge. Now USER1 has made a feature and you want to merge it or test it whether he is right or not. Now USER1 branch name is "USER1-branch".
So you're first step is without disturbing your current work switch to master by typing
```
git checkout master
```
and then create a temporary branch by typing
```
git checkout -b myTempLocalBranch
```
that command will make a temporary branch and switch to that branch. Keep in mind that we don't need to make any edits in the production directly because that leads to several problems. Just concider not doing that.

Now when you're in myTempLocalBranch pull the USER1 branch
```
git pull origin USER1-branch
```
This command will make the code of that user on you local machine.

Now your task is to see the changes and verify it. You can see the difference that USER1 has made from master by typing
```
git diff origin/master origin/USER1-branch
 ```
When you're satisfy with the feature merge it to master branch by typing
```
git merge --no-ff USER1-branch
```
