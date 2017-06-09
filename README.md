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
aws -version
```

In case you have any trouble follow [this instruction](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)

## STEP 2
### Configure aws

run this comand

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

The above command is required to update your local repo from aws repo. So do it every time before starting any new feature of your own

Then to switch to your own branch

```
git checkout origin akshay_1234
```

in this case my branch id is akshay_1234

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
