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




