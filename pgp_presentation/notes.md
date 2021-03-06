# PGP Notes

## Definitions and historical notes
For the sake of this presentation understand when I am talking about PGP I am actually talking about OpenPGP. So this is about the open standard rather than a particular piece of software.

PGP: A _standard_ used for signing, enc[dec]crypting communications (files/dirs and email) originally developed by Symantec employees then there was a buncha drama that I dont care about in this presentation.

GPG: Gnu Privacy Guard. A free implementation leveraging the PGP standard.

This presentation focuses primarily on the uses of PGP and therefore for all examples referred to herein I will breferencing GPG for reference.

## Design

You generate 2 keys: a **Public Key** and a **Private Key** using one of several supported algorithm (typically people use RSA cuz most people have heard of it).

Example Key Generation:
```
 ❯ gpg --full-gen-key                                                                                     [19:20:55]
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
```

When you generate a key you bind it to an email address and get a fingerprint.

That generates one encryption key. Which is good, but if you are using PGP for anything other than encryption you should be using multiple Keys.

* _"Master Key"_
* _"Encryption"_
* _"Signing Key"_
* _"Authentication"_

## Some things to know about
### Sharing Keys
From the GPG Privacy Handbook
The point of gpg is so either yourself or others can send you encrypted files/messages. You'll want to share your keys with someone via email, just giving them the key on a drive, or upload the key to a keyserver.

![keyserver](keyserver.png)

You send your key to the server:
```
alice% gpg --keyserver certserver.pgp.com --send-key blake@cyb.org
gpg: success sending to 'certserver.pgp.com' (status=200)
```
This allows anyone to query the keyserver for the key.
```
alice% gpg --keyserver certserver.pgp.com --recv-key 0xBB7576AC
gpg: requesting key BB7576AC from certserver.pgp.com ...
gpg: key BB7576AC: 1 new signature

gpg: Total number processed: 1
gpg:         new signatures: 1
```

### Keyserver security


### Web of trust
If someone creates an email named `JoeBiden@sketchymail.hax` how can you know whether its Captain Biden or not?

Basically a decentralized trust model.
Other users will sign keys at these ridiculous things called key signing parties. There are obviously issues with having individual users be in charge of it. Like if you have indirect trust to a bad actor thats bad. This is partially resolved by full trust and partial trust, but still relies on individual users.

Single certificate authorities don't have the same problem, because everyone trusts the cert provider.

![web of trust](https://upload.wikimedia.org/wikipedia/commons/4/4e/Web_of_Trust-en.svg)

## Create a backup!
Export a copy of your key to put on a flash drive, encrypt that drive with LUKS, and lock that mug away!

## What to do when you lose your key
Key is lost or compromised? What do?



### General encryption using gpg:
example
```
% cat file.txt

hmm

% gpg --encrypt file.txt
You did not specify a user ID. (you may use "-r")

Current recipients:

Enter the user ID.  End with an empty line: ragnyll@protonmail.com

Current recipients:
rsa4096/967586DEEE6E26A6 2019-12-15 "ragnyll <ragnyll@protonmail.com>"

file.txt.gpg

uÞîn&¦ Îñûïo'¦ÅÎV¹aEd_aÓèÈË£mß>òSñúÒÜòp¥jfq
Ê¶
^Ä¼®4óL¢µC)\Oçw3ÇÈz/@eëpKÇ5â`Ï¤/#H7¹BÃhp0ÑÌ"û1ósÂßrN7xvÍ@æW+È"]<A®cÞJ²w§ÑYð!àl·EÀøUæÚZð`½nôÚA]0¾{põ¶ñ¿8®d¢ÚKR-	9ïJÒæºuæT*Þpnð7×£ykr±dÙ½B$}ï>	KK#°Nólµäè>?Ö¢f;³´Yxòç&kØ2R@åÂe0åÕ(êç?q&·4üû ø£òÛwÄ(ºJ@¦Rþô\Hkxº¦×Ë0@JRFPèë	£Äa3íÆëiêm¯iõ«i±ãÍO)ÜZê0iÒ®=ù®vÈC>!íFK*qÊFÖC8³ÇáÓ¶¿£;1ü©rmÍ.¦¿ÊÑéwÿK÷ A{x¤RyÐ%¼ÇUYØiB¾E¸VaÛ« 0K!àÏhéç5%¶a(DbßYýKfTèí8?tjþ.jÀIÛú0Á8ÑÃÐWûSój^ÒGmù2b2+ íÞðU}ñí¨2©§S!¤£P!ñ¦MÓ»pèFÎ¦Y2F9Úþ+h¦)¾4<JK¼*

% gpg --decrypt file.txt.gpg
gpg: encrypted with 4096-bit RSA key, ID 967586DEEE6E26A6, created 2019-12-15
      "ragnyll <ragnyll@protonmail.com>"
hmm
```

The standard unix password manager [`pass`](https://www.passwordstore.org/). Its a password manager where you own everything.
It's literally just a bunch of files containing your passwords encrypted with gpg.
```
 ❯ pass
Password Store
├── FinancialPlace
│   └── email@email.com
```
Because it's just a bunch of files you can store it however you want. It comes with a wrapper that can add git commits every time you add a password.

You can add more data to it. Here is an unencrypted example
```
Yw|ZSNH!}z"6{ym9pI
URL: *.amazon.com/*
Username: AmazonianChicken@example.com
Secret Question 1: What is your childhood best friend's most bizarre superhero fantasy? Oh god, Amazon, it's too awful to say...
Phone Support PIN #: 84719
```

You might ask but what if I wanna use it on my phone?
Show app:

It also makes this
### Email
The original use case
https://protonmail.com/blog/what-is-pgp-encryption/

Literally Protonmails entire business model.
NSA cant crack it, Edward Snowden used it when he leaked documents to Greenwald.

Gmail does not use PGP, they use `S/Mime`. They used a centralized certificate authority

### Code Signing
git commit signing

### Package Managers

## Use with a security key
* https://github.com/drduh/YubiKey-Guide

## Sources
* https://protonmail.com/blog/what-is-pgp-encryption/
* https://www.gnupg.org/gph/en/manual/x457.html
* https://en.wikipedia.org/wiki/Pretty_Good_Privacy#OpenPGP
* https://en.wikipedia.org/wiki/GNU_Privacy_Guard
* https://en.wikipedia.org/wiki/Web_of_trust
* https://protonmail.com/blog/pgp-efail-statement/
* https://youtu.be/Lq-yKJFHJpk
* https://www.pandasecurity.com/en/mediacenter/panda-security/how-to-encrypt-email/
* https://wiki.archlinux.org/index.php/Pacman/Package_signing
* https://www.geeksforgeeks.org/pgp-authentication-and-confidentiality/
* https://github.com/drduh/YubiKey-Guide
