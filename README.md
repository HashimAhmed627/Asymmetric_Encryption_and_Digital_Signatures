# Asymmetric Encryption 🔑
## Overview
-
## Tasks Covered
-
#
### Generating a Pivate Key 
![Generating a Private Key File](https://github.com/user-attachments/assets/b061e2f9-9145-410b-b764-2c083c496589)

`openssl genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:2048`: This command generates an RSA private key and saves it to a file named `private_key.pem`
- `openssl genpkey`: A utility in OpenSSL used to generate private keys
- `-algorithm RSA`: Specifies the type of key to generate, in this case, a RSA (Rivest-Shamir-Adleman) key
- `-out private_key.pem`: Specifies the name of the file where the private key will be stored
- `-pkeyopt`: Option in OpenSSL is used to specify key-generation or key-parameter options when generating asymmetric key pairs
- `rsa_keygen_bits:2048`: This sets the size of the RSA key to 2048 bits

Displaying the contents of `private_key.pem` confirms the successful generation of the private key
__________________________________________________________________________________________________________________
### Adding a Passphrase to the Private Key File
![Adding Passphrase to Private Key](https://github.com/user-attachments/assets/84ad7a2f-c6d3-4fc0-8335-15d691128ea7)

__________________________________________________________________________________________________________________
### Removing Passphrase from the Private Key File
![Removing Passphrase from Private Key](https://github.com/user-attachments/assets/00b566be-e158-47f7-949a-6a2aa4d89606)

__________________________________________________________________________________________________________________
### Extracting the Public Key From the Private Key
![Extracting Public Key From Private Key](https://github.com/user-attachments/assets/f87a7f52-c58e-4764-9908-cef2b7f1d3c2)

__________________________________________________________________________________________________________________
### Encrypting a File Using the Public Key
![Encrypting a File Using Public Key](https://github.com/user-attachments/assets/1c888e4a-383a-45f3-9566-d9dea1d53916)

__________________________________________________________________________________________________________________
### Decrypting a File Using the Private Key
![Decrypting a File Using Private Key](https://github.com/user-attachments/assets/ccb1b5a8-5626-4ad5-aa3f-a53c6a1e7e13)

__________________________________________________________________________________________________________________
### Creating and Verifying a Digital Signature For a File
![Creating and Verifying a Digital Signature For a File](https://github.com/user-attachments/assets/a54d5aa3-ebdc-41b6-964d-452e8be9d87d)

__________________________________________________________________________________________________________________
## Lessons Learned
