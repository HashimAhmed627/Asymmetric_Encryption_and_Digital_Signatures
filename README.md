# Asymmetric Encryption 🔑
## Overview
This project demonstrates the process of asymmetric encryption using RSA keys to securely encrypt and decrypt files, as well as generate and verify digital signatures. It covers the generation of private and public keys, encrypting and decrypting data, and applying digital signatures for file integrity verification.

## Tasks Covered
- Generate a private RSA key and save it with AES-256 encryption
- Remove the passphrase from the private key
- Extract the public key from the private key
- Encrypt a file using the public key
- Decrypt the file using the private key
- Create and verify a digital signature for a file
#
### Generating a Pivate Key 
![Generating a Private Key File](https://github.com/user-attachments/assets/ee92c4eb-3f65-47a4-884f-8328f273a3f2)

`openssl genpkey -algorithm RSA -aes256 -out private_key.pem -pkeyopt rsa_keygen_bits:2048`: This command generates an RSA private key and saves it to a file named `private_key.pem`
- `openssl genpkey`: A utility in OpenSSL used to generate private keys
- `-algorithm RSA`: Specifies the type of key to generate, in this case, a RSA (Rivest-Shamir-Adleman) key
- `-aes256`: This option tells OpenSSL to encrypt the private key using AES-256 encryption 
- `-out private_key.pem`: Specifies the name of the file where the private key will be stored
  - The `.pem` file format is used to store cryptographic data, such as private keys, public keys, or certificates, in a base64-encoded text format with specific header and footer lines
- `-pkeyopt`: Option in OpenSSL is used to specify key-generation or key-parameter options when generating asymmetric key pairs
- `rsa_keygen_bits:2048`: This sets the size of the RSA key to 2048 bits

When the command is executed, OpenSSL prompts you to enter a passphrase (at least 4 characters long) twice to encrypt the private key with AES-256 encryption and verify accuracy

Displaying the contents of `private_key.pem` confirms the successful generation of the private key.

__________________________________________________________________________________________________________________
### Removing Passphrase from the Private Key File
![Removing Passphrase from Private Key](https://github.com/user-attachments/assets/00b566be-e158-47f7-949a-6a2aa4d89606)

This command removes the passphrase from the private key stored in `private_key.pem` and saves the unencrypted version to `private_nopass.pem`, allowing the private key to be used without requiring a passphrase for access.
__________________________________________________________________________________________________________________
### Extracting the Public Key From the Private Key
![Extracting Public Key From Private Key](https://github.com/user-attachments/assets/f87a7f52-c58e-4764-9908-cef2b7f1d3c2)

`openssl rsa -pubout -in private_key.pem -out public_key.pem`: This command extracts the public key from the private key in `private_key.pem` and saves it to `public_key.pem`
- `rsa`: Command is used to process RSA private keys and derive public keys
- `-pubout`: This option tells OpenSSL to output the corresponding public key derived from the provided private key. It generates the public key that pairs with the given private key
- `in private_key.pem`: Specifies the input file that contains the RSA private key (*`private_key.pem`*)
- `-out public_key.pem`: Specifies the output file where the generated public key will be saved (*`public_key.pem`*)

Displaying the contents of the `public_key.pem` file verifies the successful creation of the public key 
__________________________________________________________________________________________________________________
### Encrypting a File Using the Public Key
![Encrypting a File Using Public Key](https://github.com/user-attachments/assets/1c888e4a-383a-45f3-9566-d9dea1d53916)

`openssl pkeyutl -encrypt -inkey public_key.pem -pubin -in sample.txt -out cipher_sample.txt`: This command encrypts the file `sample.txt` using the public RSA key in `public_key.pem` and saves the encrypted output to `cipher_sample.txt`
- `pkeyutl`: Used to perform utility operations on keys, such as encryption or decryption
- `-encrypt`: This option tells OpenSSL to perform encryption using the provided public key
- `-inkey public_key.pem`: Specifies the input key, which in this case is the public key (`public_key.pem`)
- `-pubin`: This option tells OpenSSL that the provided key is a public key. It's important to specify so that OpenSSL knows that the key being used is meant for encryption
- `-in sample.txt`: Specifies input file to be encrypted (`sample.txt`)
- `-out cipher_sample.txt`: Specifies output file where the encrypted result will be saved

Upon displaying the contents of the newly encrypted file, we can confirm that the data is unreadable and secure.
__________________________________________________________________________________________________________________
### Decrypting a File Using the Private Key
![Decrypting a File Using Private Key](https://github.com/user-attachments/assets/ccb1b5a8-5626-4ad5-aa3f-a53c6a1e7e13)

`openssl pkeyutl -decrypt -inkey private_key.pem -in cipher_sample.txt -out plain_sample.txt`: This command decrypts the file `cipher_sample.txt` using the private key in `private_key.pem` and saves the decrypted output to `plain_sample.txt`

- `decrypt`: This option tells OpenSSL to perform decryption using the provided private key
- `-inkey private_key.pem`: Specifies the input key for the decryption operation
- `-in cipher_sample.txt`: Specifies the input file to be decrypted
- `-out plain_sample.txtx`: Specifies the output file where the decrypted result will be saved

Displaying the contents of the decrypted file shows that it is now in plaintext and readable.
__________________________________________________________________________________________________________________
### Creating and Verifying a Digital Signature For a File
![Creating and Verifying a Digital Signature For a File](https://github.com/user-attachments/assets/a54d5aa3-ebdc-41b6-964d-452e8be9d87d)

`openssl dgst -sha256 -sign private_key.pem -out signature.bin sample.txt`: This command generates a SHA-256 hash of `sample.txt`, signs it with the private key from `private_key.pem`, and stores the digital signature in `signature.bin`

- `dgst`: This command is used to generate a message digest (hash) of a file or input
- `sha256`: Specifies the hashing algorithm to be used which in this case is SHA-256
- `-sign private_key.pem`: This option tells OpenSSL to sign the hash of the file using the private key stored in `private_key.pem`
- `-out signature.bin`: Specifies the output file where the resulting digital signature will be saved. In this case, the signature is written to `signature.bin`
- `sample.txt`: This is the input file whose hash will be generated and then signed

After running the command, a digital signature for the `sample.txt` file has been successfully created

`openssl dgst -sha256 -verify public_key.pem -signature signature.bin sample.txt`: This command verifies the digital signature of `sample.txt` using the public key from `public_key.pem` and ensures that the file has not been altered and that the signature is authentic

- `-verify public_key.pem`: This option tells OpenSSL to verify the signature using the public key stored in `public_key.pem`
- `-signature signature.bin`: Specifies the input signature file that will be verified
- `sample.txt`: This is the input file whos hash will be recalculated and compared against the signature

After verifying the signature of the `sample.txt` file, we receive a 'Verified OK' message, indicating that the file has not been tampered with
__________________________________________________________________________________________________________________
## Lessons Learned
- **Understanding Key Management:** It’s important to grasp how private and public keys interact in encryption and decryption processes.
- **Security of Passphrases:** Encrypting private keys with strong passphrases adds an extra layer of security, but key management needs careful attention.
- **Public Key Encryption:** Encrypting data with the public key ensures that only the holder of the corresponding private key can decrypt it.
- **Digital Signatures:** Using private keys to sign files helps ensure data integrity and authenticity, with the public key used to verify signatures.
