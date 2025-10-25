- It Uses two Keys of every simplex logical communication link. 
	- Public Key 
	- Private Key
- The use of two keys has profound consequences in the areas of 
	- Confidentiality
	- key distribution
	- Authentication
![[Pasted image 20251026025503.png]]
![[Pasted image 20251026025606.png]]![[Pasted image 20251026025619.png]]![[Pasted image 20251026025630.png]]
## Applications : 
- Encryption / decryption : 
	- The sender encrypts a message with the recipient's public key. 
- Digital signature / authentication : 
	- The sender signs a message with its private key.
- Key exchange : 
	- Two sides cooperate to exchange a session key. 
## Requirements : 
- Computationally easy for a party B to generate a key pair
	- Public key KU$_B$
	- Private key KR$_B$
- Easy for sender to generate ciphertext : 
	- C = E (M, KU$_B$ )
- Easy for the receiver to decrypt ciphertext using private key : 
	- M = D(C, KR$_B$) = D(E (M, KU$_B$), KR$_B$)
- Computationally infeasible to determine  KR$_B$ Knowing  KU$_B$.
- Computationally infeasible to recover message M, knowing  KU$_B$ and ciphertext C. 
- Either of the two keys can be used for encryption, with the other used for decryption : 
		![[Pasted image 20251026030437.png]]

## THE RSA Public key Algorithm 
- Developed by Ron Rivest, Adi Shamir and Len Adleman at MIT, in 1977. 
- A block cipher. 
- The most widely implemented. 
![[Pasted image 20251026030700.png]]
![[Pasted image 20251026030716.png]]