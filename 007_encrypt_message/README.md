




# Example 1 - Performs an RSA encryption/Decryption operation using the TPM
`tpm2_createprimary -c primary.ctx`
`tpm2_create -C primary.ctx -Grsa2048 -u key.pub -r key.priv`
`tpm2_load -C primary.ctx -u key.pub -r key.priv -c key.ctx`
###### Create an RSA key and load it

`echo "my message" > msg.dat`
`tpm2_rsaencrypt -c key.ctx -o msg.enc msg.dat`
###### Encrypt using RSA

`tpm2_rsadecrypt -c key.ctx -o msg.ptext msg.enc`
`cat msg.ptext`
###### Decrypt using RSA
