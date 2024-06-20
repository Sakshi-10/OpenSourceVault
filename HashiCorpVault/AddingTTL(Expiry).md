# Time To Live TTL (Expiry) Of Token

Want to keep token only for 20 mins ? 

Default is 768hr 
Tokens generated for services or applications usually have a default lease_duration of 768 hours (32 days) if not otherwise specified in Vault's configuration.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
NOTE : **TTL is only available for  assumed_role, federation_token, and session_token credential types**

1) CREATE ASSUMED ROLE
    <img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/6883ae52-9764-4e9f-8d73-cca87de416b3">
--------------------------------------------------------------------------------------------------------------------------------------------------------------------

2) Specify the TTL when you write the role in HashiCorp Vault
  <img width="1684" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/e2f9b91a-d74b-4880-b1fc-2ca99dc46a37">

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

3) Change the Policy associated with the Bucket (foss0310sakshi)
<img width="1684" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/3bf995aa-5112-4b68-902b-a2fa15a53a51">
<img width="974" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/f80b0b48-3cec-4c8d-88cc-b93902bc7a06">

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

4) Read the Dynamic Credentials 
<img width="1693" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/87b40656-cbc2-479d-820b-db25099ac623">

Few moments later: 

<img width="1693" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/c8b55489-19ed-47c4-a2a6-0175bd1b26be">

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

5) In GITBASH -> Export the session token also along with accessKey and secretKey
If you don't export session token then listing the bucket contents won't work 

<img width="1693" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/26ea9f88-1b90-4b87-a5d7-32de817c2e68">

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

6) Few Moment later
<img width="1693" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/17693a09-f9d6-4d7a-a797-1b01532310ef">

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

7) Now the token is expired

<img width="1693" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/c56ac7a3-8030-4489-9420-3a8c83436554">

<img width="1693" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/5c7c91c1-9179-440b-be98-3c28831b9a6b">

--------------------------------------------------------------------------------------------------------------------------------------------------------------------


The same procedure can be done via credential type as session token rather than assumed role
