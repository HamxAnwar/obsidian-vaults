- How can the data over internet or the messages we sent are unreadable by anyone else but the receiver?
	- This is done with cryptography.
	- Networking protocols : Communicate between devices.
	- Cryptography : Trusting the communication.
#### Cryptography
- Enables secure communication in case f adversary existance.
	- Secure = Confidentiality + Integrity.
- In todays age, we generally use cryptography everyday.
	- When you log in to TryHackMe, your credentials are encrypted and sent to the server so that no one can retrieve them by snooping on your connection.
	- When you connect over SSH, your SSH client and the server establish an encrypted tunnel so no one can eavesdrop on your session.
	- When you conduct online banking, your browser checks the remote server’s certificate to confirm that you are communicating with your bank’s server and not an attacker’s.
	- When you download a file, how do you check if it was downloaded correctly? Cryptography provides a solution through hash functions to confirm that your file is identical to the original one.
- PCI DSS (Payment Card Industry Data Security Standards) specifies that for large companies, the payment card data must be encrypted both while being stored and while being trusted.
- Terms for cryptography:
	- **Plaintext** is the original, readable message or data before it’s encrypted. It can be a document, an image, a multimedia file, or any other binary data.
	- **Ciphertext** is the scrambled, unreadable version of the message after encryption. Ideally, we cannot get any information about the original plaintext except its approximate size.
	- **Cipher** is an algorithm or method to convert plaintext into ciphertext and back again. A cipher is usually developed by a mathematician.
	- **Key** is a string of bits the cipher uses to encrypt or decrypt data. In general, the used cipher is public knowledge; however, the key must remain secret unless it is the public key in asymmetric encryption. We will visit asymmetric encryption in a later task.
	- **Encryption** is the process of converting plaintext into ciphertext using a cipher and a key. Unlike the key, the choice of the cipher is disclosed.
	- **Decryption** is the reverse process of encryption, converting ciphertext back into plaintext using a cipher and a key. Although the cipher would be public knowledge, recovering the plaintext without knowledge of the key should be impossible.

#### Historical Ciphers
- Stated from Egypt in 1900 BCE.
- More smaller spaces:
	- **Ceaser Cipher** shift each letter by a certain number to encrypt the message.
	- 