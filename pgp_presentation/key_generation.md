% gpg --full-gen-key
gpg (GnuPG) 2.2.27; Copyright (C) 2021 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
  (14) Existing key from card
Your selection? 1

RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: Jimbo
Email address: jimbo@jimbo.web
Comment:
You selected this USER-ID:
    "Jimbo <jimbo@jimbo.web>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key F72FC9B3CA121151 marked as ultimately trusted

gpg: revocation certificate stored as '/home/ragnyll/.gnupg/openpgp-revocs.d/24F2A1D7BDCC0C7648B69515F72FC9B3CA121151.rev'
public and secret key created and signed.

pub   rsa4096 2021-02-14 [SC]
      24F2A1D7BDCC0C7648B69515F72FC9B3CA121151
uid                      Jimbo <jimbo@jimbo.web>
sub   rsa4096 2021-02-14 [E]
