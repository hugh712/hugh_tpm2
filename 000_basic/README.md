
## Why TPM

- Generate security key
    - RSA, AES, ECC…
- Store security Key
    - Temporary or Permanent 
- Manage security key
    - Encrypt, import, export, migration 
- protect security key
    - Authorization, protect from attack 
- Use security key


## Hash

#### Hash Extend

## HMAC

## Nonce

## KDF

## Symmetric & Asymmetric Algorithm
Check https://github.com/tpm2-software/tpm2-tools/blob/master/man/common/object-alg.md


## Sign with Symmetric (Use OpenSSL as example)
`openssl enc -aes-256-cbc -in un_encrypted.data -out encrypted.data`

`openssl enc -d -aes-256-cbc -in encrypted.data -out un_encrypted.data`

## Sign with Asymmetric (Use OpenSSL as example)
Ref [x2]


## Primary
To create keys for signing, one needs to first create a primary key under any of the 4 hierarchies. This primary key can now be used to create children keys. The children keys can now be used for signing. It is also possible for each child key of the primary key to become parent keys if it meets certain conditions. Thus one can have a deep hierarchy of keys.

The primary key cannot sign. It can only decrypt the child key for signing. This is specified by what is called key attributes. The key's attributes are set at key creation. These attributes are used to control the behaviour of the keys[0].


## Hierachy
- o for TPM_RH_OWNER
- p for TPM_RH_PLATFORM
- e for TPM_RH_ENDORSEMENT
- n for TPM_RH_NULL

## Authorization
![alt text](../pics/tpm_auth.png "tpm authorization")

## Authorization Formatting
Authorization for use of an object in TPM2.0 can come in 3 different forms: 
1.  Password
2.  HMAC
3.  Sessions

## Keys
- Endorsement Key (EK)
- Attestation key (AK)
- Attestation Identity Key (AIK)


## Bank

## PCR

## Policy

## Session

## TCTI

## Ref

[0] https://dev.to/nandhithakamal/tpm-part-1-4emf

[x1] https://stackoverflow.com/questions/16056135/how-to-use-openssl-to-encrypt-decrypt-files

[x2] https://opensource.com/article/21/4/encryption-decryption-openssl
