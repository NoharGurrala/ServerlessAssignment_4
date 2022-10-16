# Serverless Development Workshop

In this workshop, we'll deploy a simple serverless application which shows the message on the html request.

This will create an API that can be used by web services.


# Preparation:

1. Access to a MacOS or Linux machine. These instructions are not tested on Windows; users may need to make small adaptations or run these commands inside of a Docker container or Linux VM. ([Install Docker for Windows](https://docs.docker.com/docker-for-windows/))
2. Amazon Web Services account. Creation of an account is free and various services are provided under a free-tier, although a credit card is required at the time of account creation. AWS Lambda is free for up to 1 million invocations per month, for all users, which is more than sufficient for this course. Storage of functions may incur small fees (normally pennies / month).  Students are solely responsible for their AWS bill and all charges incurred as a result of this course.
3. Install NodeJS 4.4.3 or higher: [NodeJS downloads](https://nodejs.org/en/)
4. Curl (you probably have this already! Curl ships with MacOS and is easily installed via Linux package managers.

# System configuration

* Create ~/.aws/credentials (manually or via `aws-cli configure`), or set environment variables:

Run the following in the Terminal

```

serverless config credentials --provider aws --key <access_key_id> --secret <secret_access_key>

```

# Serverless Framework

There are several frameworks for building so-called "serverless" applications. The most
popular one is called, aptly, [The Serverless Framework](http://www.serverless.com). Other
frameworks can be found on this [fairly exhaustive list](https://github.com/anaibol/awesome-serverless).

For the sake of convenience, we'll settle using TheServerlessFramework with a NodeJS application for this workshop.


* Install module
```
 sudo npm install -g serverless
```
* Create directory for Project
```
mkdir iopipe-workshop
cd iopipe-workshop
```
* Create 
```serverless create --template aws-nodejs``` 
also see [alternatives to nodejs](https://github.com/serverless/serverless/tree/master/lib/plugins/create/templates)



# Deploy a real app!

We've prepared an example project for you to test!

Checkout this repo:

```
$ git clone https://github.com/iopipe/lambda-workshop
```

## Install npm modules

```
$ npm install
```

## Re-name the project!

Edit `serverless.yml` and `doge.js` to change `iopipe-workshop-doge-1` to a unique name.

```
$ sed -i "s/iopipe-workshop-doge-1/iopipe-workshop-doge-$(($RANDOM*$RANDOM))/g" doge.js serverless.yml
# On OS X: sed -i "" -e "s/iopipe-workshop-doge-1/iopipe-workshop-doge-$(($RANDOM*$RANDOM))/g" doge.js serverless.yml
```

## Deploy the app:

```
$ serverless deploy
```



# Delete resources

We have created various resources during this course. You may, of course, keep these applications and resources deployed, but you may incur small fees from Amazon in doing so. Make sure to delete all AWS Lambda functions, S3 objects, S3 buckets, and other resources created during this course using your AWS console. If in doubt, check the Billing "Service" in your AWS Console.

Resources will have been created under IAM roles, Lambda functions, S3 buckets, API Gateway, and Cloudformation. Simply deleting the cloud formation resources is usually enough, but again, double-check!

The following command *should* remove all resources:

```
$ serverless remove
```
