Understanding HTTPS (HyperText Transfer Protocol Secure) ?

This article was done using my notes from a brilliant speech, recently made by Ross Bagurdes : "Understanding How HTTPS Protects Your Data with Ross Bagurdes" (2018), available on Pluralsight :  Pluralsight LIVE 2018: Get Your Geek On (Security).
url: https://app.pluralsight.com/player?course=ps-live-2018-get-your-geek-on-security&author=pluralsight-live&name=3a422490-c02c-4074-a3fd-a406c28c5063&clip=0&mode=live


HTTPS is commonly misunderstood

HTTPS protects your data over the web. But how does it really work ? HTTPS is widely misunderstood, we often hear that keys are used to encrypt data and keys are part of certificates. There are public and private certificates. We use the public certificate to encrypt data and the server will use the private certicate to decrypt it. Well, it far for what is really going on. Certificates are not used almost at all in HTTPS. It uses a completely different sytle of encryption...

This is what we want to take a look at ! 

Web Browser Encryption

Web browser encryption is usely done through two components : Negotiate Encryption Session and Encryption Algorithms. So, what are those ?  First of all, to transfer data over the web, we need to negotiate an encryption session between the Web client and the Web server using TLS or SSL, which are the same protocol. Second of all, the protocol we use (TLS v1.2 or TLS v1.3) to negotiate our session will then determine the encryption algorithms we use (RSA, Diffie-Hellman, ECDHE, 3DES, AES, ChaCha20).

The problem and the solutions with Encrypting Data

Encrypting Communication relies on the following logic. The web browsers runs the data through an algorithm and a secret to produce a secret message. We send it through the public wire. Then, the server decrypts the message with the same algorithm and key. A problem comes up : we use symetric encryption to realise this task. We need the same key on the server and on the client. But we can't send the key over the public internet. We overcame this problem using HTTPS. As we encrypt data, we need a way to exchange the key between our client and our server. 

There are several ways to exchange the keys :
1. Diffie-Hellman Key Exchange : In 1970's Whit Diffie and Martin Hellman figured out a way to exchange a key without anybody in the middle figuring out what the keys are.
Here is the simplified logic: 

When we set up HTTPS on a server you have to install a certificate. The certificate won't be used for the encryption entirely. At some point in the negotiation between the client and the server, the server will send its certificate to the client. 

In this certifcate two numbers are relevant, p and g. p and g are public keys (available to anyone) and we set  p = 149 and g = 17 for our example. In paralell, the client as the server detain their own private keys.

Key Exchange

On the client side, we run the private key (a = 8) throuh a formula  (g^a MOD p) to calculate an encrypted key, for instance 17^8 MOD 149 = 5. During the handshake process between the server and the client, the client will send its encrypted key to the server. The whole world knows about number 5, 17 and 149.

On the server side, we repeat the same process. We pick a private key (b = 6), run it through our formula (g^b MOD p)  to obtain a second encrypted key, 17^6 MOD 149 = 16. Then , the server will send its encrypted key to the server. 

The client and server have exchanged only 4 numbers. 6 numbers are in total, 4 are known to the world, 2 remain unknown to the world. The client does not know about the private key of the server. The server does not know about the private key of the client. 

What we do then, is that we take these numbers, and we run it throught the formula again. 
On the client, (encrypted key)^a MOD p = key = 16^8 MOD 149 = 129 
On the server,  (encrypted key)^b MOD p = key = 5^6 MOD 149 = 129 
As long that P and G are prime numbers, we will always get the same key on both sides. 

Nodoby can calculate the final keys, unless they have access to the private keys on the client side and the server side. We did not use certificates to encrypt anything, we juste used p and g to produce a common key. A key that both sides can use. 

The way we can exhange the keys, one of them id Diffie-Helman, and it's going to depend upon the version of TLS we use. If we use TLS v1.2 and lower, we can use either RSA (Rivest-Shamir-Adleman, who came up with private-public key encryption in the 1960's. As it is vulnerable, so we don't use it anymore), Diffie Hellman or Elliptical Curve Deffie Hellman. If we use TLS v1.3, we use Elliptical Curve Diffie Hellman. 

Elliptical Curve Diffie-Hellman Ephemeral (ECDHE)

ECDHE is a more modern technic to exchange keys over the internet. It uses two curves (an elliptical curve) to produce a set of 3 points. The second curve and the 3 points produced become public information.

On the client and on the server, we will use a private key, the curve in addition to the 3 data points and run them into a formula to produce a private key. The private key will be exchanged from one side to the other. 
They will use the same formula to decrypt in the same manner as the previous Deffie-Hellman technic. 
This process produces a key that is more computationaly complex with less math involved. 

Data Encryption Protocols

Now that we know how keys are exchanged, let's talk about Data Encryption. 
Here are the major Data Encryption Protocols :
3DES (168 bits, invented in the 1980's). Well, it is vulnerable.
AES (128 or 256 bits, invented int the 1990's) : Advanced Encryption System.
ChaCha20 (much newer)

Theses protocols are used to encrypt data exchanged between the client and the server. On the server, we should not use 3DES as it is vulnerable. 

Handshake Integrity

While we are negotiating our session between our client and our server. We want to make sure that nobody is tempering with it, grab the data in the middle, change data in our headers so that somebody else knows what the keys are. 

We are going to take a little piece of each one of our handshake messages, and we are going to combine it into a long string of values, run it through a hash algorithms. Either SHA, SHA-256, or SHA-384. It is going to produce a hash value that's unique to that handshake. The client and the server are going to exchange it over the wire and then compare these values. 

Conclusion : 
TLS Encryption implies three protocols, which allows for HTTPS transmission : 
1. Key Exchange
2. Data Encryption
3. Handshake Integrity 

So what about the certificates  ? The certificates are primarily used to verify the server. Who it says it is. The server has a certificate given by a certificate authority. Nonetheless, certificates encounter their own problems, which is by itself another topic... 
