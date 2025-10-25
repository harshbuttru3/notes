## Security Attacks : 
Any actions that compromises the security of information. 
- Four Types of Attacks : 
	- **Interruption** : Attack on availability.
	- **Interception** : Attack on confidentiality. 
	- **Modification** : Attack on integrity.
	- **Fabrication** : Attack on authenticity. 
- **Passive Attacks** : Obtain information that is being transmitted (eavesdropping).
	- Two types : 
		- Release of message contents. 
		- Traffic analysis.
	- Very difficult to detect.
- **Active Attacks** : Involve some modification of the data stream or the creation of a false stream.
	- Four categories : 
		- **Masquerade** : One entity pretends to be a different entity. 
		- **Replay** : Passive capture of a transaction and subsequent replay. 
		- **Modification** : Some portion of a message is altered on its way. 
		- **Denial** **of** **service** : Prevents access to resources. 
## Security Services : 
- Confidentiality (privacy) 
- Authentication (who created or sent the data )
- Integrity (Has not been altered ) 
- Non-repudiation (parties cannot later deny) 
- Access control (prevent misuse of resources ) 
- Availability (permanence, non-erasure)
	- Denial of Service Attacks
	- Virus that deletes files.
![[Pasted image 20251020120537.png]]
## Cryptography Primitives : 
### Encryption : 
- Most important concept behind network security is ***encryption***. 
- Two forms of encryption : 
	- 1. Private (or symmetric) : single key shared by sender and receiver.
	- 2. Public-key (or Asymmetric) : Separate keys for sender and receiver.
![[Pasted image 20251020120826.png]]
### Authentication : 
- Techniques to uniquely identify the sender of a message. 
- Various approaches : 
	- Encryption techniques
	- Cryptographic hash functions
	- Digital signature -> a combination of various cryptographic primitives.

### Private or Symmetric key cryptography
- A common secret value **k** (called key) is shared b/w sender and receiver.
- Sender encrypts a message **P** (called plaintext) using **K** to generate a ciphertext C.
	- C = EA(P,K)
- Receiver decrypts the ciphertext C using K to get back the palintext P.
	- P = DA(C,K)
![[Pasted image 20251022114833.png]]
- Security to the scheme 
	- Should depend only on the secrecy of the key.
	- Should not depend on the secrecy of the algorithm.
- Assumptions that we make: 
	- Algorithms for encryption/decryption are known to the public.
	- Keys used for encryption/decryption are kept secret.
- Key distribution problem of secret key systems: 
	- Establish key before communication.
	- Need **n(n-1)/2** keys with **n** different parties.
- Overall, very large number of keys are required.
	- Difficult to maintain secrecy

## Classical Private-Key Encryption Techniques
Broadly falls under two categories : 
## 1. **Substitution ciphers**
Each letter or group of letters of the plaintext are replaced by some other letter or group of letters, to obtain the ciphertext.

**Caesar Cipher :** (a substitution cipher) 
- Earliest known substitution cipher.
- Replace each letter of the alphabet with the letter ***three places after*** that alphabet. 
- Alphabets are assumed to be wrapped around (Z is followed by A, etc.).

P : HAPPY NEW YEAR
C : KDSSB QHZ BHDU

- We can generalize the idea by replacing each letter by the k$^{th}$ following letter. 
	- "k" becomes the secret key.
- If we assign a number to each letter (A=1, B=2, etc), then
	- C = E(P) = (P+K-1) % 26 +1
	- P = D(c) = (C-K +25) % 26 +1
- Drawback : 
	- Brute force attack is easy 
	- Number of possibilities are rather small (i.e. 25)'
**Mono-alphabetic Cipher :** 
- Allow any arbitrary substitution. 
- There can be 26! or 4 x 10$^{26}$  possible keys.
- A typical key may be : (Z A Q W S X C D E R F V B G T Y H N M J U I K L O P)
	- "A" replaced by "Z", "B" replaced by "A", "C" replaced by "Q", and so on.
- **Drawbacks :**
	- We can make guesses by observing the relative frequency of letters, digrams, and trigrams in the text.
	- Easy to break in general. 
## 2. **Transposition ciphers**
Letters of the plaintext are permuted in some form. 
- Many techniques have been proposed under this category.
- A simple scheme : 
	- Write out the plaintext in a rectangle, row by row, and read the message column by column, by permuting the order of the columns.
	- Order of the column becomes the key.
- ![[Pasted image 20251022123245.png]]

- **Drawbacks :** 
	- The cipher text has the same letter frequency as the original plaintext
	- Guessing the number of columns and some probable words in the plaintext holds the key.
## Practical Ciphers : 
- They are much more complicated. 
	- Require computers to perform encryption and decryption.
	- Almost impossible to carry out by hand. 
	- Can encrypt any kind of data, not necessarily only text. 
## Stream Ciphers vs. Block Ciphers 
- A stream cipher encrypts the plaintext bit by bit (in streams).
- A block cipher encrypts n-bit blocks at a time.
	- For example, A 256-bit cipher encrypts 256-bit blocks at a time.
	- Shorter blocks have to be suitably padded. 

## Practical Private-Key Algorithms : 
- Data Encryption Standard (DES)
	- Block size is 64 bits.
	- Key is 56 bits. 
- IDEA 
	- Block size is 64 bits. 
	- Key size is 128 bits. 
- Advanced Encryption Standard (AES)
	- Also known as Rijndael cryptosystem. 
	- Block size is 128 bits.
	- Key size can be 128,192, or 256 bits. 
### Data Encryption Standard(DES). 
- Most widely used encryption scheme at one time.
	- Also known as the Data Encryption Algorithm (DEA). 
	- It is a block cipher. 
- Some of the features : 
	- The palintext is 64-bits in length.
	- The key is 56-bits in length. 
	- Longer plaintext are processed in 64-bits blocks. 
	![[Pasted image 20251026023754.png]]

- The overall Processing at each iteration : 
![[Pasted image 20251026023914.png]]

- Concerns about : 
	- The algorithm and the key length (56-bits). 
	- Longer key lengths are essential for critical applications. 
### Triple DES 
- Use three keys and three executions of the DES algorithm (encrypt-decrypt-encrypt ). 
	![[Pasted image 20251026024142.png]]
- Effective key length is 168 bits. 
![[Pasted image 20251026024220.png]]
### Need for a new standard
- DES had been in use for a long time. 
	- A replacement for DES was needed. 
	- Theoretical attacks can break it. 
- Can use Triple-DES- but slow with small blocks. 
- US NIST issued call for ciphers in 1997. 
	- 15 candidates accepted in june 1998.
	- 5 were short-listed in August 1999. 
- Rijndael was selected as the ***Advanced Encryption Standard*** in october 2000. 
## The AES cryptosystem : 
- In the Rijndael proposal, the block length and the key length can be independently specified to be 128, 192, or 256 bits. 
- The AES standard limits the block length to 128 bits. 
	- key length can be 128, 192, or 256 bits. 
- Easy to implement, both in hardware and software. 
- Resistant against all known attacks. 
### AES Rounds : 
- AES has 10,12, or 14 rounds. 
	- All rounds are identical, except the first and last one. 
- Various steps in each round : 
	- **SubBytes** : Non-linear substitution. 
	- **ShiftRows** : Transposition. 
	- **MixColumn** : Mixing operations of each column. 
	- **AddRoundKey** : Round key added to state. 
![[Pasted image 20251026025040.png]]
### Details of Each Round : 
![[Pasted image 20251026025110.png]]
### Overall Structure : 
![[Pasted image 20251026025133.png]]
