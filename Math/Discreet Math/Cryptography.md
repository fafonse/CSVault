
## History

### Caesar Cypher
The most famous old cypher is the Caesar Cypher, where you just shift all the letters over by three.
`william` $\rightarrow$ `zlooldp`

We iterated with this for a while, usually by adding a formula for the decryption that included more than addition. However, this method is still worse than random assignment, AKA just randomly moving letters. With both methods you want to remove any double letters or spaces too, since those are dead give aways.

Also with encryption you should remove any repeating phrases/guessable phrases. You can ask the Nazi's about that one.

The Caesar Cypher was made obsolete overnight, when some arabic guy just used *frequency checking*. If you know the frequencies of common letters in the alphabet, then you can easily decrypt those letters by comparing the frequencies with those of the encrypted message.

### Block Cypher
Instead of one letter at a time, you combine groups of letters. You can do a lot more scrambling around that way.

## Types of Encryption

There are two main types of encryption:
1.  **Symmetric** 
	- The one method of encryption everyone used for most of history.
	   Both parties need to know the encryption/decryption formulas.
	- You run into issues with the number of keys required for multi-user communication
	- You also need to share a lot of private info (which could be intercepted) for encryption to work.
	- ***FAST***
2. **Asymmetric** 
	- In asymmetric encryption, there are two "keys". There's a encryption key and a decryption key. That way you can share the encryption key around (your *public* key), and whenever someone wants to send you a message you can decrypt it with a secret decryption key (your *private* key).