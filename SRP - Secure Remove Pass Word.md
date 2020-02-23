# SRP - Protocol 
SRP is a handshake protocol that makes multiple requests and responses between the client and the server. 

Main utility: To perform password-based authentications

## What can be done with SRP
* authenticate without ever sending a password over the network.
* authenticate without the risk of anyone learning any of your secrets – even if they intercept your communication.
* authenticate both the identity of the client and the server to guarantee that a client isn’t communicating with an impostor server.
* authenticate with more than just a binary “yes” or “no”. You actually end up with an encryption key.

## Concepts 
### Salt
[Salt (cryptography)](https://en.wikipedia.org/wiki/Salt_(cryptography)
A salt is random data that is used as an additional input to a one-way function that hashes data, a password or passphrase.

### Zero-knowledge proof
[Zero-knowledge proof](https://en.wikipedia.org/wiki/Zero-knowledge_proof)

### Password Authenticated Key Agreement
[Password Authenticated Key Agreement](https://en.wikipedia.org/wiki/Password-authenticated_key_agreement)

### Key Derivation Function (KDF)
[KDF - Key Derivation Functiond](https://en.wikipedia.org/wiki/Key_derivation_function)
A Key derivation function (KDF) is a cryptographic hash function that derives one or more secret keys from a secret value such as a master key, a password, or a passphrase using a pseudorandom function.
ddd
## How does SRP work?
SRP consists of three steps {**registration**, authentication and verification}

## References
[What-is-secure-remote-password-srp-protocol-and-how-to-use it](https://medium.com/swlh/what-is-secure-remote-password-srp-protocol-and-how-to-use-it-70e415b94a76)

[developers-how-we-use-srp-and-you-can-too](https://blog.1password.com/developers-how-we-use-srp-and-you-can-too/)

[crypto algorithms - SRP]([https://clipperz.is/security_privacy/crypto_algorithms/#srp](https://clipperz.is/security_privacy/crypto_algorithms/#srp))

