## Get the current time and clock from the TPM in a signed form
`tpm2_gettime`

#### Create a key and get attested TPM time

## Example - Create a rsa key and get attested TPM time
#### (1) Create a primary, and export as primary.ctx
`tpm2_createprimary -C e -c primary.ctx`

#### (2) Create a rsa key
`tpm2_create -G rsa2048:rsaes -u rsa.pub -r rsa.priv -C primary.ctx`
###### -u is the public key export
###### -r is the private key export


#### (3) Load both the private and public portions of an object into the TPM
`tpm2_load -C primary.ctx -u rsa.pub -r rsa.priv -c rsa.ctx`
###### -u is the import public key
###### -r is the import private key
###### -c is the file name of the saved object context, for future interactions with the object
###### The tool outputs the name of the loaded object in a YAML dictionary format with the key name where the value for that key is the name of the object in hex format


#### (4) Use the saved object context to get current time 
`tpm2_gettime -c rsa.ctx -o attest.sig --attestation attest.data`
###### It returns both a signature, and the data in the standard TPM attestation form

###### It outputs to stdout, in YAML format, the TPMS_TIME_INFO structure from the TPM.  The structure contains the current setting of Time, Clock, resetCount,  and  restartCount.

    time: 13673142     # 64 bit value of time since last _TPM_Init or TPM2_Startup
                       # in ms.
    clock_info:
      clock: 13673142  # 64 bit value of time TPM has been powered on in ms.
      reset_count: 0   # 32 bit value of the number of TPM Resets since the last
                       # TPM2_Clear.
      restart_count: 0 # 32 bit value of the number of times that TPM2_Shutdown or
                       # _TPM_Hash_Start have occurred since the last TPM Reset or
                       # TPM2_Clear.
      safe: yes        # boolean yes|no value that no value of Clock greater than
                       # the current value of Clock has been previously reported by
                       # the TPM.

