# Description
Performs an HMAC operation and returns the results. 

Output defaults to stdout and binary format unless otherwise specified via -o and –hex options respectively.

# Usage
`tpm2_hmac [OPTIONS] [ARGUMENT]`

# Example 1 - Perform an HMAC with Default Hash Algorithm
`tpm2_createprimary -c primary.ctx`
###### create a primary object 

`tpm2_create -C primary.ctx -G hmac -c hmac.key`
###### Use the primary object to create the hmac key

`tpm2_hmac -c hmac.key --hex data.in`
###### Perform an hmac using the key’s default scheme (hash algorithm) and output to stdout in hexidecimal format.
