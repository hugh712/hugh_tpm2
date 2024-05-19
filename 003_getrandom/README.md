# Description
Returns the next SIZE octets from the random number generator.  The SIZE parameter is expected as the only argument to the tool.
Note that the TPM specification recommends that TPM’s fix the number of available entry to the maximum size of a hash algorithm output in bytes.
Most TPMs do this, and thus the tool verifies that input size is bounded by property TPM2_PT_MAX_DIGEST and issues an error if it is too large.
Output defaults to stdout and binary format unless otherwise specified with -o and –hex options respectively.

# Usage
`tpm2_getrandom [OPTIONS] [ARGUMENT]`

# Example 1 - Clear the authorization values on the platform hierarchy
`tpm2_getrandom -o random.out 20`
###### Generate a random 20 bytes and output the binary data to a file

# Example 2 - Generate a random 8 bytes and output the hex formatted data to stdout
`tpm2_getrandom 8`
