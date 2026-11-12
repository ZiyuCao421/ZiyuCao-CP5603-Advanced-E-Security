# CP5603 Practical 5 --- Cryptography in Practice

## 1. Overview

This practical explored how cryptographic tools support data integrity,
confidentiality, and authenticity. The work was completed in a Linux
Mint virtual machine using the terminal and GnuPG (GPG).

### Environment

-   Operating system: Linux Mint in Oracle VirtualBox
-   GPG version observed: 2.4.4
-   Working directory: `~/cryptography-prac5`

``` bash
mkdir -p ~/cryptography-prac5
cd ~/cryptography-prac5
pwd
gpg --version
```

## 2. Part A --- Hashing and Integrity

### Create a sample file and calculate its hash

``` bash
echo "Confidential CP5603 data" > sample.txt
cat sample.txt
sha256sum sample.txt
```

Observed SHA-256 digest before modification:

``` text
0ab4b3bfb713b7ba7e561f2c134f8b691a3ec80aab1f237c923718e7271c49f
```

Add a period to the message and calculate the digest again:

``` bash
echo "Confidential CP5603 data." > sample.txt
sha256sum sample.txt
```

Observed digest after modification:

``` text
66850c70b9096feb0bd47939ef98fc3d66a9ab132b2bdc52eee1634241d6c456
```

### Observation

The input changed only slightly, but the SHA-256 digest changed
significantly. This demonstrates the **avalanche effect**: a small input
change produces a substantially different digest.

A hash can help detect data changes if the expected digest comes from a
trusted source. A matching hash alone does not prove who created a file.
Hash functions also have a theoretical possibility of collisions, where
different inputs produce the same digest.

## 3. Part B --- Public-Key Encryption and Confidentiality

### Create the plaintext file

``` bash
echo "This is a confidential message for CP5603." > secret.txt
cat secret.txt
```

### Generate a GPG key pair

``` bash
gpg --full-generate-key
```

The generated key configuration used ECC-related algorithms:

-   **Ed25519**: used for digital signatures.
-   **Cv25519 (Curve25519-based)**: used for encryption-related
    operations.

The lab identity was `CP5603 lab user` with the example address
`labuseradmin@example.com`. These are lab identifiers, not proof of a
real-world identity.

### Encrypt the file

``` bash
gpg -e -r "CP5603 lab user" secret.txt
ls -l
```

The encrypted output was created as `secret.txt.gpg`.

-   `-e` requests encryption.
-   `-r` specifies the recipient whose public key is used.

### Decrypt the file

``` bash
gpg -d secret.txt.gpg
```

The original plaintext was successfully recovered:

``` text
This is a confidential message for CP5603.
```

### Observation

Public-key encryption supports **confidentiality**: the file is
encrypted for the selected recipient, and the corresponding private key
is needed to decrypt it. In this lab, the same user generated the key
pair, encrypted the file for that key identity, and decrypted it. In a
real exchange, a sender normally encrypts for the recipient's public
key, while the recipient keeps their private key secret.

Private keys and their passphrases must be protected. Anyone who obtains
a usable private key may be able to decrypt data intended for that key.

## 4. Part C --- Digital Signatures

### Create a message and sign it

``` bash
echo "This message is signed for CP5603." > message.txt
cat message.txt
gpg --clearsign message.txt
```

This created `message.txt.asc`, containing readable text and a
signature.

### Verify the signature

``` bash
gpg --verify message.txt.asc
```

GPG reported a **Good signature** for the lab identity. It also
displayed a warning that this was not a detached signature and that
`message.txt` was not verified as a separate file. This warning does not
mean the cleartext signature failed: the signed content inside
`message.txt.asc` was verified.

### Observation

A digital signature helps detect changes to signed content and verifies
that the signature corresponds to the relevant public key. It can
support integrity, authentication, and non-repudiation. However,
`Good signature` does not by itself prove the signer's real-world
identity; the public key must be reliably associated with that person or
organisation.

The signature used EdDSA/Ed25519, while the encryption subkey used
Cv25519. These algorithms serve different purposes.

## 5. Key Concepts

  -----------------------------------------------------------------------
  Concept                 Main purpose            Important limitation
  ----------------------- ----------------------- -----------------------
  Hashing                 Produces a fixed-length Does not encrypt data
                          digest to help check    or prove the sender's
                          data changes            identity

  SHA-256                 Cryptographic hash      A trusted reference
                          function producing a    digest is needed for
                          256-bit digest          meaningful comparison

  Symmetric encryption    Uses a shared secret    The secret key must be
                          key to encrypt and      shared and protected
                          decrypt                 securely

  Public-key encryption   Uses a recipient's      Correct public-key
                          public key for          ownership and
                          encryption and          private-key protection
                          corresponding private   matter
                          key for decryption      

  Digital signature       Verifies that signed    Trust in the
                          content matches a       identity-to-key binding
                          signature made by the   must be established
                          corresponding private   
                          key                     

  Key management          Covers key generation,  Poor key handling can
                          storage, distribution,  undermine otherwise
                          backup, and revocation  strong algorithms

  Hash collision          Two different inputs    Practical collision
                          produce the same digest attacks can undermine
                                                  uses such as signatures
                                                  or integrity checks
  -----------------------------------------------------------------------

## 6. Seminar Discussion Topics

### Blockchain: What is its purpose?

A blockchain maintains a shared, ordered record of transactions across
multiple participants. Cryptographic hashes link blocks, while digital
signatures can authenticate transaction authorisation. Consensus
mechanisms help participants agree on the ledger's state without relying
entirely on one central record keeper.

Blockchain does not automatically guarantee that every recorded
statement is true. It can make later alteration detectable or difficult
under the system's assumptions, but it cannot independently verify the
truth of data entered into the system.

### Comparing cipher tools

When comparing cryptographic tools, consider their purpose, security
assumptions, performance, key size, implementation maturity, and
suitability for the target device or application. A hash function, a
symmetric cipher, a key-agreement protocol, and a digital-signature
algorithm are not interchangeable.

### Lightweight cryptography

Lightweight cryptography aims to provide appropriate security under
constraints such as limited memory, processing power, energy, or
communication bandwidth. It is relevant to small embedded and IoT
devices. Lightweight must not mean using an obsolete or inadequately
reviewed algorithm.

### Twofish and Blowfish

Twofish and Blowfish are symmetric block ciphers. They are distinct
algorithms and should not be confused with hashing or public-key
cryptography. When evaluating a cipher for a new system, consider
current security recommendations, implementation support, key-management
requirements, and the mode of operation rather than relying on the
algorithm name alone.

## 7. Reflection

This practical helped me understand that cryptography is closely
connected to mathematics, rather than being simply a collection of
encryption tools. During the SHA-256 experiment, I changed the original
message by adding only one period, but the resulting hash value changed
significantly. This demonstrated how a small input modification can
produce a completely different output, illustrating the avalanche
effect.

I also became interested in the mathematical structures behind
cryptographic algorithms, particularly linear combinations, linear
transformations, and matrix operations. These concepts provide useful
ways to understand how data can be represented and transformed
systematically. However, secure cryptographic algorithms cannot rely
only on simple linear operations, because predictable mathematical
relationships may create opportunities for attackers. Non-linear
transformations are also important in many modern cipher designs.

Hash collisions present another security challenge because two different
inputs can theoretically produce the same hash value. If attackers can
deliberately exploit such collisions, they may undermine integrity
checks or digital signatures. Therefore, choosing secure algorithms,
such as SHA-256, and verifying the authenticity of the source are both
important. Overall, this practical encouraged me to explore the
mathematical foundations of cybersecurity and to see cryptography as an
application of mathematical reasoning to real-world security problems.

## 8. Commands Used

``` bash
# Create and enter the lab folder
mkdir -p ~/cryptography-prac5
cd ~/cryptography-prac5

# Check GPG
gpg --version

# Hashing
echo "Confidential CP5603 data" > sample.txt
sha256sum sample.txt
echo "Confidential CP5603 data." > sample.txt
sha256sum sample.txt

# Encryption and decryption
echo "This is a confidential message for CP5603." > secret.txt
gpg -e -r "CP5603 lab user" secret.txt
gpg -d secret.txt.gpg

# Digital signature
echo "This message is signed for CP5603." > message.txt
gpg --clearsign message.txt
gpg --verify message.txt.asc

# List lab files
ls -l
```

## 9. Final Takeaways

-   Hashing can help detect content changes but does not provide
    confidentiality.
-   Public-key encryption supports confidentiality when the correct
    recipient public key is used.
-   Digital signatures support integrity and key-based authentication,
    but identity trust must be established separately.
-   Strong algorithms can still be undermined by weak passwords, exposed
    private keys, incorrect implementation, or poor key management.
-   Cryptographic systems combine mathematical constructions with
    operational controls; security depends on the whole system, not just
    one algorithm.
