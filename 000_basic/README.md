


## Bank

## Primary
To create keys for signing, one needs to first create a primary key under any of the 4 hierarchies. This primary key can now be used to create children keys. The children keys can now be used for signing. It is also possible for each child key of the primary key to become parent keys if it meets certain conditions. Thus one can have a deep hierarchy of keys.

The primary key cannot sign. It can only decrypt the child key for signing. This is specified by what is called key attributes. The key's attributes are set at key creation. These attributes are used to control the behaviour of the keys[0].


## Hierachy
- o for TPM_RH_OWNER
- p for TPM_RH_PLATFORM
- e for TPM_RH_ENDORSEMENT
- n for TPM_RH_NULL

## Authorization Formatting
Authorization for use of an object in TPM2.0 can come in 3 different forms: 
1.  Password
2.  HMAC
3.  Sessions

## Keys
- Attestation key (AK)


## PCR

## Policy

## Session

## TCTI

[0] https://dev.to/nandhithakamal/tpm-part-1-4emf
