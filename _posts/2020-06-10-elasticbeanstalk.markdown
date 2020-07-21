---
layout: blog
title:  "Launching a Drupal Build on AWS Elastic Beanstalk"
date:   2020-06-10 00:00:18 -0500
categories: posts
excerpt_separator: <!-- more -->
published: true
---
<div>Setup and Launch a Drupal Build on Elastic Beanstalk. </div>
<p>***** Elastic Beanstalk is difficult to provision servers. I attempted to add PHP Modules to the Ubuntu instance with no success. *****</p>

Install CLI
IAM User
Git
<!-- more -->




<h3>Regions, Availability Zones, and Local Zones
</h3><a href="https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html
">https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html</a>
Amazon AWS DEVOPS<br/>
Elastic Beanstalk<br/>
PHP 7.3running on 64bit Amazon Linux 2<br/>
<br/>
<h3>Add Amazon IAM Identity and Access Management Console
</h3>Add a user for your new instance.<br/>
Generate an access key limited to the AwsCli tool.<br/>
Dashboard | User | Security Credentials | Create Access Key<br/>
Be sure to download the csv file. You will have to regenerate keys if you lose them.<br/>

<h3>Install Amazon CLI on OSX
</h3>The Amazon CLI allows you to run commands including setting up SSH access to your instance.<br/>
<a href="https://www.youtube.com/watch?v=fzqRGWQX2LM">https://www.youtube.com/watch?v=fzqRGWQX2LM</a><br/>
: brew install awscli<br/>

<pre>
The "examples" directory has been installed to:
 /usr/local/share/awscli/examples

Bash completion has been installed to:
 /usr/local/etc/bash_completion.d

zsh completions and functions have been installed to:
 /usr/local/share/zsh/site-functions
==> Summary
🍺  /usr/local/Cellar/awscli/2.0.19: 11,101 files, 79.9MB
</pre>

<h3>Once installed the aws command line command can be used.
</h3>
aws<br/>
aws ls<br/>
aws configure<br/>
aws s3 ls<br/>
This shows you a list of the available S3 buckets<br/>


************************************************************************************

<h3>Install the EB CLI with homebrew On OSX
</h3>The Amazon Elastic Beanstalk CLI allows you to run commands including setting up SSH access to your instance.<br/>
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-osx.html<br/>
Use Homebrew to install Amazon CLI.<br/>
: brew install awsebcli<br/>
: eb init<br/>
: eb<br/>

Do you want to set up SSH for your instances?<br/>
eb ssh<br/>
<a href="https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb3-ssh.html">https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb3-ssh.html</a><br/>




*****************************************************************************


Deploying a high-availability Drupal website with an external Amazon RDS database to Elastic Beanstalk
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/php-hadrupal-tutorial.html

Launch a DB instance in Amazon RDS

Step 10: For Source, type sg- to view a list of available security groups. Choose the current security group to allow resources in the security group to receive traffic on the database port from other resources in the same group.

Step5: Missing the Database name config value RDS_DB_NAME


Deploying drupal on Elastic Beanstalk
https://github.com/aws-samples/eb-php-drupal

Drupal climbs the AWS Elastic Beanstalk
https://peterjlord.co.uk/article/drupal-climbs-aws-elastic-beanstalk

Using Elastic Beanstalk with Amazon Elastic File System
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/services-efs.html

Using the EB CLI with Git
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb3-cli-git.html

2. awseb-drup-1

Deploying applications to Elastic Beanstalk environments
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.deploy-existing-version.html

Using the EB CLI with Git

1. Launch an instance of Elastic Beanstalk.

1. Install Amazon CLI on your local environment.

3. Create a Mysql database.

3. Upload files to EB

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/services-efs.html

"Elastic Beanstalk also provides sample applications that use Amazon EFS for shared storage. The two projects are configuration files that you can use with a standard WordPress or Drupal installer to run a blog or other content management system in a load balanced environment. When a user uploads a photo or other media, it is stored on an Amazon EFS file system, avoiding the need to use a plugin to store uploaded files in Amazon S3."
https://github.com/aws-samples/eb-php-drupal

http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/customize-containers-ec2.html


mod_rewrite beanstalk ?????

Customizing software on Linux servers
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/customize-containers-ec2.html#customize-containers-format-commands


$ cat /etc/*-release
NAME="Amazon Linux"
VERSION="2"
ID="amzn"
ID_LIKE="centos rhel fedora"
VERSION_ID="2"
PRETTY_NAME="Amazon Linux 2"
ANSI_COLOR="0;33"
CPE_NAME="cpe:2.3:o:amazon:amazon_linux:2"
HOME_URL="https://amazonlinux.com/"
Amazon Linux release 2 (Karoo)


Environment properties and other software settings
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-softwaresettings.html?icmpid=docs_elasticbeanstalk_console


Customizing software on Linux servers *****
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/customize-containers-ec2.html

Creating and deploying PHP applications on Elastic Beanstalk
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_PHP_eb.html

mod_rewrite - HTTP to HTTPS redirection rule only works after accessing it through HTTP first
https://serverfault.com/questions/896449/mod-rewrite-http-to-https-redirection-rule-only-works-after-accessing-it-throu


Advanced environment customization with configuration files (.ebextensions)
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions.html

UGH!
No good info on provisioning the OS instance.


Deploying a Docker Container to AWS with Elastic Beanstalk
https://medium.com/@sommershurbaji/deploying-a-docker-container-to-aws-with-elastic-beanstalk-28adfd6e7e95
Create an environment with
eb create


Stack deletion failed: The following resource(s) failed to delete: [AWSEBSecurityGroup, AWSEBLoadBalancerSecurityGroup].


Drupal Docker on Amazon
Deploying Drupal with MySQL database on Amazon EKS cluster using Amazon EFS
https://medium.com/@srank2000/deploying-drupal-with-mysql-database-on-amazon-eks-cluster-using-amazon-efs-150b6c36e183
UGH Dev ops


