# Operations by using Generated AWS Dynamic Secrets

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## READING AND GENERATING DYNAMIC CREDENTIALS 
Now the AWS secret engine is enabled and configured with a Role. Now we can ask Vault to generate an access key pair for that role by reading the aws/creds/roleName
<img width="1684" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/f6b59c0b-a554-4ad6-b847-5c00693682b0">

<img width="1088" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/ebba8151-31ab-4ab7-a8b6-be43e393b81d">

The accesskey and secret key can be used to perform any s3 operation(specified within the role permissions)
--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Putting Object in the bucket and Listing Contents using DYNAMIC SECRETS

Further in the discussion I would use below bucket 
<img width="1684" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/5b39a6ae-794a-484b-9e3e-7cf4487ae2f2">
The credentials in the above picture are static secrets and you can see the arn from the get caller identity -> I have also listed the bucket contents 


Now I would use the above generated dynamic Credentials and list bucket contents
I am using git bash for the aws cli commands 
Set the parameters

![image](https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/063844e3-3b64-4d22-a163-186754903ed5)

Check ARN from the get caller identity
![image](https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/1112f5d2-d2b2-4143-86e0-f92facbd6459)

This is a prove that I am not using permanent static creds

<img width="1684" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/612b8263-70d6-4e26-bbea-508cc29c055a">

The above operations are based on the permissions you mentioned in the policy.json 
To recollect Look at the policy_document:
![image](https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/0575a8c1-55fe-4227-ad0b-3b4297d2d4f6)

To list all of your buckets, you must have the s3:ListAllMyBuckets permission. Doc : https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-bucket-intro.html#access-bucket-console-ex![image](https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/03c33b38-973c-4446-a291-ca1063fa1198)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

You can tweak with the permission body in policy.json and use the dynamic credentials in your application
