# Description
Startup the TPM

Typically a Resource Manager (like tpm2‐abrmd (https://github.com/tpm2‐software/tpm2‐abrmd)) or low‐level/boot software will have already sent this command.

# Usage
`tpm2_startup`

# Example 1 - Start the TPM
`sudo tpm2_startup`
###### Send a TPM Startup Command with flags TPM2_SU_STATE

`sudo tpm2_startup -c`
###### Send a TPM Startup Command with flags TPM2_SU_CLEAR

# Example 2 - Shutdown the TPM

`tpm2_shutdown`
###### Send a TPM Shutdown Command with flags TPM2_SU_STATE

`tpm2_shutdown ‐c`
###### Send a TPM Shutdown Command with flags TPM2_SU_CLEAR

# Example 3 - Clean the TPM

`tpm2_clear lockoutpasswd`
###### Set owner, endorsement and lockout authorizations to an empty value

`tpm2_clear -c p`
######  Clear the authorization values on the platform hierarchy
