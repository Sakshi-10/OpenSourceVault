# Performing Basic CRUD operations in HashiCorp Vault

1. CREATE
2. READ
3. UPDATE
4. DELETE

<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/096c6674-fb01-4a27-be4c-e235245a5b80">

We would use the kv type to perform basic CRUD operations

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## CREATE

vault kv put -mount=secret myAwesomeApp/creds dbid=admin dbpid=Password@123

Use the kv secret engine with mount point as secret , put my creds into kv secret 
myAwesomeApp/creds is the path where my creds will be stored 
Dbid and dbpid are my key value pairs representing the secrets I wish to store 
We have 2 key value pairs above

<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/fd38a821-7014-4152-8588-d0807da0f275">

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## READ

vault kv get -mount=secret myAwesomeApp/creds

<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/1de07dc3-56b2-4e9e-96ca-6332d76a19ac">

NOTE: you can see the dbpid because you have login using Root Token  so we could see the secrets in plain text and not encrypted format 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## UPDATE

<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/4e22088b-add1-42cb-8690-84c3e4e4465c">

<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/f0910490-5842-44cf-bb56-5d4d4ed4841e">

Notice : version says 2 :Passing optional parameter -version 

<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/123e5082-8837-4525-be82-d48e0b24ddd1">

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## DELETE

<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/f01a0f46-3374-4d63-9873-7d341fef2236">
<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/ec4abfb5-c397-4dcc-b5ac-0c61892c26e0">

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
TIP : You could see that when I created the dbid and dbpwd I was manually typing -> this can have some security breach as the history may reveal the password 
You want to avoid exposing the password

Use : vault kv put -mount=secret MyNewApp token=- 

This would allow you to type the pwd without displaying it and once you are done type ^Z to exit
<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/b29c6daf-b2bc-4cca-b0a6-ef41ee0948f7">

<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/3c6075d0-9689-466e-8be8-c1b45be96b55">

For more to explore : https://developer.hashicorp.com/vault/tutorials/get-started-hcp-vault-dedicated/vault-first-secrets

Happy Learning !!
