

## Example 1 - Create an RSA Endorsement Key and make it persistent
`sudo tpm2_createek -P abc123 -w abc123 -c 0x81010001 -G rsa -u ek.pub`

## Example 2 -Create an ECC NIST_P384 Endorsement Key and make it persistent
`sudo tpm2_createek -G ecc384 -c 0x81010002`

## Example 3 - Create a transient Endorsement Key, flush it, and reload it.
`sudo tpm2_createek -c ek.ctx -G rsa -u ek.pub`

###### Check that it is loaded in transient memory
`sudo tpm2_getcap handles-transient`
`- 0x80000000`

###### Flush the handle
`sudo tpm2_flushcontext 0x80000000`

###### Note that it is flushed
`sudo tpm2_getcap handles-transient`
`<null output>`

###### Reload it via loadexternal
`sudo tpm2_loadexternal -C o -u ek.pub -c ek.ctx`

###### Check that it is re-loaded in transient memory
`sudo tpm2_getcap handles-transient`
`- 0x80000000`


## Example 4 - Create an Attestation Key and make it persistent
`sudo tpm2_createek -c ek.handle -G rsa -u ek.pub`

`sudo tpm2_createak -C ek.handle -c ak.ctx -u ak.pub -n ak.name`

`sudo tpm2_evictcontrol -C o -c ak.ctx 0x81010002`
