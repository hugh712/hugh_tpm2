## Get TPM time
`tpm2_startup`

##### Create a key and get attested TPM time

###### Create a primary export as primary.ctx
`tpm2_createprimary -C e -c primary.ctx`

###### Create an rsa2048 key with an rsaes asymmetric encryption scheme
###### -u is the public key export, 
###### -r is the private key export
`tpm2_create -G rsa2048:rsaes -u rsa.pub -r rsa.priv -C primary.ctx`

`tpm2_load -C primary.ctx -u rsa.pub -r rsa.priv -c rsa.ctx`

`tpm2_gettime -c rsa.ctx -o attest.sig --attestation attest.data`
