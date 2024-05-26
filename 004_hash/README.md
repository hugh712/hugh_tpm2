# Description
Performs a hash operation on file and returns the results.  If argument is not specified, then data is read from stdin.  If the results of the hash will be used in
a signing operation that uses a restricted signing key, then the ticket returned by this command can indicate that the hash is safe to sign.

Output defaults to stdout and binary format unless otherwise specified via -o and –hex options respectively.

# Usage
`tpm2_hash [OPTIONS] [ARGUMENT OR STDIN]`

# Example 1 - Hash a file with sha1 hash algorithm and save the hash and ticket to a file
`tpm2_hash -C e -g sha1 -o hash.bin -t ticket.bin data.txt`
###### Generate a random 20 bytes and output the binary data to a file
