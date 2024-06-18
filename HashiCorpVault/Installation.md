# Installing Vault on windows :

1. Install the binaries from : https://developer.hashicorp.com/vault/downloads Or use chocolately to choco install vault 
    to know more on what is chocolately ? : https://chocolatey.org/
2. Extract the downloaded zip into your respective folder (ex: C:\Users\snasha\Desktop\projects)
3. Open command prompt go to C:\Users\snasha\Desktop\projects\vault_1.16.3_windows_amd64 
    dir -> you can see vault.exe
4. Check the version -> C:\Users\snasha\Desktop\projects\vault_1.16.3_windows_amd64>vault.exe version
    Vault v1.16.3 (e92d9a57018f43360e2e3717b3b6a7f650c88f4c), built 2024-05-29T14:28:42Z
5. To see various help options : vault server -help
6. for our use we will start vault in development mode : 

When you run `vault server -dev` in HashiCorp Vault, you are starting a development mode server. Here’s what this command does and what it means:

1. **Development Mode Server**: The `-dev` flag starts Vault in a development mode. This mode is intended for testing and development purposes rather than production use. It provides a simplified setup that is easy to get started with and doesn't require as much configuration as a production deployment.

2. **Local Backend**: When started in development mode, Vault runs with an in-memory storage backend by default. This means that all data (secrets, policies, etc.) stored in this mode will be lost when the server is restarted.

3. **Unsealed and Unauthenticated**: In development mode, Vault is automatically unsealed and unauthenticated. This makes it easier to experiment with Vault’s features without having to deal with authentication mechanisms or sealing/unsealing processes that are crucial in a production setup.

4. **HTTP and HTTPS Listeners**: By default, the development server listens on both HTTP (http://localhost:8200) and HTTPS (https://localhost:8200) endpoints. This allows clients to interact with Vault without needing to set up TLS certificates for HTTPS communication.

5. **Example Token**: When you start Vault in development mode, it prints an example root token to the console. This token grants full administrative access to Vault, allowing you to perform any operation. In a real production environment, managing tokens and access policies would be much more controlled and secure.

6. **Usage**: Developers use `vault server -dev` primarily to quickly spin up a local instance of Vault for testing, experimenting with APIs, learning Vault’s features, or developing integrations without the need for a full-fledged, secured setup.

It’s important to note that data stored in the development mode server is not persistent across server restarts. For production deployments, you should configure Vault with appropriate backends (like Consul, AWS S3, etc.) for storage and follow best practices for authentication, encryption, and high availability.

![image](https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/a2f45cae-cce2-46c8-a2f5-7687fa1ea0c6)

In the above picture as we can see 
*  Vault is unsealed : means vault server is initialized and unsealed -> allowing access to its secrets 
When in sealed state -> access to secrets is restricted 

*  Successful mount means Vault secrets engine is configured and enabled for use
Vault address value : URL of the vault server 

*  Root token is a highly privileged token that servers as a initial master token created during vault initialization
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
Now keep this cmd open this would act as your Vault Server operating in Dev Mode
Open new CMD window 
*  set VAULT_ADDR=http://127.0.0.1:8200
*  set VAULT_TOKEN= returned value when you started the vault in dev mode

Now you are all set to use this command window to talk to the other vault server engine 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Testing with basic commands 

Secrets list : shows all the enabled secrets within vault server and their  mount paths 
<img width="1710" alt="image" src="https://github.com/Sakshi-10/OpenSourceVault/assets/64091618/7b806dbb-31b1-4aa2-8222-87113d050a32">

Focus on kv type -> key vault : allows us to store key value pairs in the vault 
Notice the mount point for this is a secret

C:\Users\snasha\Desktop\projects\vault_1.16.3_windows_amd64>vault kv
Usage: vault kv <subcommand> [options] [args]

  This command has subcommands for interacting with Vault's key-value
  store. Here are some simple examples, and more detailed examples are
  available in the subcommands or the documentation.

https://developer.hashicorp.com/vault/docs/commands/kv
