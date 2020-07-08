# aws-gitlab
CFT for Gitlab on AWS

This CFT deploys:
    - S3 bucket
    - IAM Role with embedded policy
    - VPC (2 public and 2 private subnets)
    - Network
    - RDS PostgreSQL database
    - Redis for ElastiCache
    - GitLab Server 
    - Gitaly Server 
    - Elastic Load Balancer 
    - Auto Scaling Group 

**REQUIRED MANUAL ACTIONS**
    Before deploying this cft, you will need to set up AMI parameters in the AWS System Manager Parameter Store. This way, the CFT will be able to pull the ImageId when deploying. Follow these steps:  

    1. From the AWS Systems Manager, select *Parameter Store* on the left-hand menu.

    2. Click *Create Parameter* and enter */gitlab/gitlab/ami/gitlab-ce-12.2.5* as the name. If you choose to assign a different name, be sure to change the default when specifying parameters at CFT deployment.    

    3. Select *Standard* Tier and *String* for the Type.

    4. Set the Data Type to *aws:ec2:image*, paste the *GitLab AMI* under Value, and click *Create Parameter*. 

    Follow steps 1-4 again to create a parameter for Gitaly using the name */gitlab/gitaly/ami/ubuntu-server-18.04-lts-hvm*. Again, if you choose to assign a different name, adjust the default at CFT deployment. 

    Below are the most recent AMIs as of July 8th, 2020:
        GitLab: ami-00006f6838542d59c
        Gitaly: ami-0ac80df6eff0e70b5 

