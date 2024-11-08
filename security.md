## Security and Cryptography

### Entropy
Entropy is a measure of randomness. This is useful, for example, when determining the strength of a password.

Entropy is measured in bits, and when selecting uniformly at random from a set of possible outcomes, the entropy is equal to log_2(# of possibilities).

Depending on your threat model, you would need 40 bits of entropy to be pretty good


Hash functions
A cryptographic hash function maps data of arbitrary size to a fixed size, and has some special properties
- An example of a hash function is SHA1, which is used in Git. 

A hash function can be thought of as a hard to invert random looking function
- Non-invertible
- Deterministic 

It can be used as a short summary of the contents of a file
- Software can be downloaded from mirrors, eg. Linux ISOs and it would be nice to not have to trust them



### Key Derivation Functions
They are used for a number of applications


Applications
- Producing keys from passphrase for use in other cryptographic algorithms
- Storing login credentials; generate and store a  random salt for each user, store KDF(password + salt) and verify the login attempts by recomputing the KDF

A **salt** is random unique value tagged along the password which protects in case of a breach to database since hash function is not the hash of password alone


Symmetric Cryptography

```bash
keygen() -> key (this funcion is randomized)

encrypt(plaintext: array<byte, key) -> array<byte> (the cipher text)

decrypt(ciphertext: array<byte>, key) -> array<byte> (the plaintext)
```
- its hard to determine the input (plaintext) without the key

Applications:
- encrypting files for storage in an untrusted cloud service. This can be combined with KDFs, so you can ecnrypt a file with a passphrase. Generate key = KDF (passphrase), and then store encrypt(file, key)


Asymmetric Cryptography

This refers to there being 2 keys, with different roles.
A private key, is meant to be kept private
A public key can publicly shared and it won't affect secuirty 

This refers to there being 2 keys with different roles.
- a private key is meant to be private
- a public key can be publicly shared and it won't affect security

```bash
keygen() -> (public key, private key) (this function is randomized)

encrypt(plaintext: array<byte>, public key) -> 
    array<byte> (the ciphertext)
decrypt(ciphertext: array<byte>, private key) ->
    array<byte> (the plaintext) 


sign(message: array<byte>, private key) -> 
    array<byte> (the signature)
verify(message: array<byte> signature: array<byte>, public key) ->
    bool (whether or not the signature is valid)


```

The encrypt/decrypt functions have properties similar to their analogs from symmetric cryptosystems.

A message can be encrypted using the public key. Given the cipher text, its hard to determine the input without the private key


### What are differences?
Symmetric encryption is a door lock
- anyone with the key can lock and unlock it

Assymmetric encryption is a padlock with a key
- give the unlocked lock to someone (public key)
- put a message in the box and lock on
- only you could open the lock because you kept the key

The sign/verify functions have the same properties that physical signatures have -> hard to forge.

No matter the message, witout the private key, its hard to produce a sginauture such that the verify function returns true

Private messaging, apps like signal and keybase use assymetic keys to establish private communication channels

### Case Studies

Password managers
* Password managers make it convenient to use unique, randomly generated high-entropy passwords for all your logins, and 
* they save all your passwords in one place, encrypted with a symmetric cipher with a key produced from a passphrase using a KDF





