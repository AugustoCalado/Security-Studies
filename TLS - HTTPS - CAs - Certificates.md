# TLS - HTTPS - CAs - Certificates


## TLS vs SSL
Both TLS (Transport Layer Security) and SSL (Secure Sockets Layer) are cryptographic protocols that provide security over a network. The TLS is the evolution (the most updated version) of SSL which now is deprecated since 2015 by the IETF (Internet Engineering Task Force).

## HTTPS
HTTPS is the HTTP procotol running over TLS, in other words is the secured version of HTTP. By using HTTPS **every packet** transferred between client and server is **encrypted** using public or private key cryptography.

### What does HTTPS ensure?
1. **Privacy** - It means that no one can eavesdrop on your messages
2. **Integrity** - It means that the message is not manipulated on the way to its destination
3. **Identification** - It means that the site that are been visited is indeed the one that should be visited not a fake one.

### Encryptation Algorithms
1. **Symmetric Key Algorithm** 
There is only one key to encrypt and decrypt a message. The Encryption key is mixed in with the message, so even if the encryption algorithm is known, whithout the key, the message is still nonsense. 

The bad point of Symmetric keys is  that they are hard to share.

2. **Asymmetric Keys Algorithms**
In this algorithm there are two keys,  one is public and the other one is private. The public key is used by the sender to encrypt its message and the private key is used by the receiver to decrypt the message.

**public key cryptography**
Any message encrypted with Bob's public key can only be decrypted with Bob's private key.

**signature**
Anyone with access to Alice's public key can verify that a message (signature) could only have been created by someone with access to Alice"s private key

## Digital Certificates

## Digital Signatures


## CA - Certification Authority
How to make sure that the party we are talking to is actually who they claim they are? This is where the certificate authority comes in.

A certificate authority (CA) is a third-party organization with 3 main **objectives**.
1. Issuing Certificates
2. Confirming the identity of the certificate owner
3. Provide proofthat the certificate is valid

**Type of certificates**
1. Domain Validated: This certificate just verifies the domain name, and nothing else.
2. Organization Validated: The certificate requires the validation and manual verification of the organization behind the certificate
3. Extended Validation: The certificate requires an exhaustive verification of the business 

### How Do Certificates Get Validated?  It is done by the "Chain of trust"
When a CA issues a certificate, they sign the certificate with their root certificate pre-installed in the root store (A root store is basically a database of trusted CAs).

**PS:** Most of the time it's an intermediate certificate signed with a root certificate.

* The browser connects to a site via HTTPS and downloads the certificate. 
* The certificate is not a root certificate. 
* The browser downloads the certificate that was used to sign the certificate on the site, but this certificate is still not the root certificate (Mid Certificat). 
* The browser once more looks up the certificate that signed the intermediate certificate. 
* Now it is the **root certificate**. 
* The entire certificate chain is trusted, and thus the site certificate is trusted as well.

### How to get a certificate from a CA?
1. Create a **Certificate Signing Request** with the key pair (public and private key)
2. Ask a CA to sign  the provided certificate from step 1 with its private key (anyone who has the public key of the CA can verify that it was actually signed by the CA)

 Now that the requester has its certificate signed by a CA, everyone who needs to verify its identity checks if the certified provided is signed by a CA by using the CA public key to authenticate. If it was a valid certificate (the one signed by a CA), we can securely use the public key "attached" in the certificate to send our secret key. From now on the communication will be encrypted. 

## The HTTPS Handshake
The process to established a secure connection to transmit messages is called handshake. Here some agreements are made in order to determine how to communicate securely.

1. The client send a list of ssl/tls versions and encryption algorithms (**Cypher Ssuite**) that it can works. 
2. The server choose the best SSL/TLS version and encryption algorithm and reply with its certificate which includes public key, so they can verify the server identity.
3. Client verifies the received certificate against a CA using it's public key. If the validation is consistent, the client generates a "pre master key" that is encrypted by the server public key. In the end the client that a request to the server with the generated content.
4. The server decrypt the "pre master key".
5. Both server and client have generated the same "shared secret" that they are going to use as a symmetric key

## Keystore and Truststore



## References 
[How Http Works]([https://howhttps.works/the-handshake/](https://howhttps.works/the-handshake/))
