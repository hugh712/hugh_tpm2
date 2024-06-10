# Description
Generates signature of specified message or message-digest using the specified symmetric or asymmetric signing key. 


# Usage
`tpm2_sign [OPTIONS] [ARGUMENT]`

# Example 1 - Sign and verify with the TPM using the endorsement hierarchy
`tpm2_createprimary -C e -c primary.ctx`
###### create a primary object 

`tpm2_create -G rsa -u rsa.pub -r rsa.priv -C primary.ctx`
###### Use the primary object to create the rsa public and private key

`tpm2_load -C primary.ctx -u rsa.pub -r rsa.priv -c rsa.ctx`
###### Generta a chile rsa key context
####### Parent key is primary.ctx
####### Load the public and private portions of the object into the TPM.

`echo "my message" > message.dat`
###### Generate the message

`tpm2_sign -c rsa.ctx -g sha256 -o sig.rssa message.dat`
###### Sign the message and create the signature
####### Hash algorithm is sha256

`tpm2_verifysignature -c rsa.ctx -g sha256 -s sig.rssa -m message.dat`
###### Verify the message and the signature with the rsa private key

