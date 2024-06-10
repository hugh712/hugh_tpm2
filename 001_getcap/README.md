# Check all capability

`sudo tpm2_getcap -l`
- algorithms
  - Get all cap for all algorithms
- commands
- pcrs
- properties-fixed
- properties-variable
- ecc-curves
- handles-transient
- handles-persistent
- handles-permanent
- handles-pcr
- handles-nv-index
- handles-loaded-session
- handles-saved-session


## algorithms

`sudo tpm2_getcap algorithms`
  
    rsa:
      value:      0x1
      asymmetric: 1
      symmetric:  0
      hash:       0
      object:     1
      reserved:   0x0
      signing:    0
      encrypting: 0
      method:     0
    sha1:
      ...
    hmac:
      ...
    aes:
      ...
    mgf1:
      ...
    keyedhash:
      ...
    xor:
      ...
    sha256:
      ...
    sha384:
      ...
    sm3_256:
      ...
    sm4:
      ...
    rsassa:
      ...
    rsaes:
      ...
    rsapss:
      ...
    oaep:
      ...
    ecdsa:
      ...
    ecdh:
      ...
    ecdaa:
      ...
    sm2:
      ...
    ecschnorr:
      ...
    kdf1_sp800_56a:
      ...
    kdf1_sp800_108:
      ...
    ecc:
      ...
    symcipher:
      ...
    cmac:
      ...
    ctr:
      ...
    ofb:
      ...
    cbc:
      ...
    cfb:
      ...
    ecb:
      ...

## Export a public key

`tpm2_createprimary -c primary.ctx`
###### Create a primary object

`tpm2_readpublic -c primary.ctx -o output.dat -f pem`
###### read the public structure in an openssl compliant format

## Serialize an existing persistent object handle to disk for later use

`tpm2_createprimary -c primary.ctx`

`tpm2_evictcontrol -c primary.ctx`
 ###### persistent-handle: 0x81000001
 ###### action: persisted

 `tpm2_readpublic -c 0x81000001 -o output.dat -f pem -t primary.handle`
 ###### use the persistent handle to get a serialized handle

 `tpm2_startauthsession --policy-session -S session.ctx -c primary.handle`
 ###### use this verified handle in an encrypted session with the tpm

 ## About Attributes

 ###### TPMA_OBJECT_RESTRICTED
 ###### TPMA_OBJECT_DECRYPT
 ###### TPMA_OBJECT_FIXEDTPM
 ###### TPMA_OBJECT_FIXEDPARENT
 ###### TPMA_OBJECT_SENSITIVEDATAORIGIN
 ###### TPMA_OBJECT_USERWITHAUTH
 
 
