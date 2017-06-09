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

``` aws -version```

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
