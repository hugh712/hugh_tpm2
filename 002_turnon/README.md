
## Startup the TPM
Typically a Resource Manager (like tpm2‐abrmd (https://github.com/tpm2‐software/tpm2‐abrmd)) or low‐level/boot software will have already sent this command.

`tpm2_startup`

##### Send a TPM Startup Command with flags TPM2_SU_STATE
`sudo tpm2_startup`
##### Send a TPM Startup Command with flags TPM2_SU_CLEAR
`sudo tpm2_startup -c`

## Shutdown the TPM

##### Send a TPM Shutdown Command with flags TPM2_SU_STATE
`tpm2_shutdown`

##### Send a TPM Shutdown Command with flags TPM2_SU_CLEAR
`tpm2_shutdown ‐c`

## Clean the TPM
