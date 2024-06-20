# Getting started with AWS Secret Engine

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Prerequistics 

1) Have a AWS Account (Free tier account would work) : https://aws.amazon.com/free/?trk=ff721c0f-c85d-4643-817f-04fb0e8a7323&sc_channel=ps&ef_id=:G:s&s_kwcid=AL!4422!10!71674641724836!71675163902616&msclkid=c95551b35e1e168c7df737c0baa15fd7&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all

2) Have a AWS S3 bucket : example in this repo I am using foss0310sakshi S3 bucket 
3) Craete AWS IAM role (foss0310sakshi-user) and IAM policy may or maynot be attached.
4) IAM role associated with AWS s3 bucket -> Get Access credentials 
   example: { "AccessKey": "AK****************C", "SecretKey": "Gx**************************ZYUHDH" }

Create access key :  Go to IAM Users -> Security creds  tab -> scroll down and create access key

Further in the discussion I would use below bucket 
<img width="1684" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/5b39a6ae-794a-484b-9e3e-7cf4487ae2f2">

The credentials in the above picture are static secrets and you can see the arn from the get caller identity -> I have also listed the bucket contents 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## ENABLING AWS SECRET ENGINE

Unlike the kv secret engine (discussed in CRUD Operations) which is enabled by default, AWS secret engine must be enabled before use.
<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/b859ed88-0759-4585-97cd-d2769f356dcd">

Note: Different secrets engine have different behavior
AWS secret engine generates dynamic , on demand AWS access credentials!

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Configure AWS Secrets Engine

Configure to authenticate and communicate with AWS. 
1) You can you Bucket credentials (IAM access key and secret key as mentioned in prerequistics ) 
2) You can also use aws root account credentials (Though this is not recommended)

<img width="1684" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/d89603b7-80db-4ab1-b69c-d3fe6504d115">
Replace AWS_ACCESS_KEY, AWS_SECRET_KEY and AWS_REGION with your AWS IAM user's access key, secret key, and the region where your resources are located.

These credentials are now stored in AWS secret Engine 
The Engine will use these credentials when communicating with AWS in future requests

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Configure Vault Role

A role in Vault is a human friendly identifier to an action.
Vault knows how to create a role but doesn't know what permissions , groups and policies you want to attach to that user

Create a policy :
> vim policy.json
<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/1f4f5fb2-2576-45d7-be49-eafef889aa92">

>>vault write aws/roles/foss-sakshi-role credential_type=iam_user policy_document=@policy.json
foss-sakshi-role is the  unique role name

<img width="1684" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/a99aff0e-e48a-4a62-886b-40bc20aa0647">

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## READING AND GENERATING DYNAMIC CREDENTIALS 

When you hit the read request then the dynamic credentials are created 
To be able to read the credentials the role "foss-sakshi-role" (AWS IAM ROLE mentioned in the prereq) needs permission of "iam:CreateUser","iam:PutUserPolicy","iam:CreateAccessKey"
<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/ce738fa4-0455-4cac-98bc-37eb0e3dc99a">

Now the AWS secret engine is enabled and configured with a Role. Now we can ask Vault to generate an access key pair for that role by reading the aws/creds/roleName
<img width="1684" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/ae60f095-b239-40ba-8cda-d04c98029313">

Dynamic Credential Diagram
<img width="1088" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/ebba8151-31ab-4ab7-a8b6-be43e393b81d">

The accesskey and secret key can be used to perform any s3 operation(specified within the role permissions)
