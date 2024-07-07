
# Description
Performs RSA encryption on the contents of file data using the indicated padding scheme according to IETF RFC 3447 (PKCS#1).  

The key referenced by key-context is required to be:

1. An RSA key
2. Have the attribute encrypt SET in it’s attributes.

# Usage

`tpm2_rsaencrypt [OPTIONS] [ARGUMENT]`

`tpm2_rsadecrypt [OPTIONS] [ARGUMENT]`

# Example 1 - Performs an RSA encryption/Decryption operation using the TPM
`tpm2_createprimary -c primary.ctx`

`tpm2_create -C primary.ctx -Grsa2048 -u key.pub -r key.priv`

`tpm2_load -C primary.ctx -u key.pub -r key.priv -c key.ctx`

###### Create an RSA key and load it

`echo "my message" > msg.dat`

`tpm2_rsaencrypt -c key.ctx -s rsaes -o msg.enc msg.dat`

###### Encrypt using RSA

`tpm2_rsadecrypt -c key.ctx -s rsaes -o msg.ptext msg.enc`

`cat msg.ptext`

###### Decrypt using RSA
