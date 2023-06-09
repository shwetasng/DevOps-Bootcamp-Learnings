# LEARNINGS FROM 6th JUNE 2023 (Networking Security)
## Questions:-
- What are compliance regulations?
- What is symmetric and asymmetric encryption? What are different symmetric and asymmetric encryption algorithms?
- What happens if EVE changes the message in symmetric encrption? Would receiver be able to decrypt the original message?

## Learnings :-
- Consider 'BOB' and 'ALICE' as two person who communicates with each each other using an insecure channel that can be manipulated and tracked by 'EVE'.
- 'EVE' can see & change the message sent over the channel.
- CRYPTOGRAPHY :- Mathematics fiels to encrypt & decrypt the data.
- CIPHER :- short-name for encryption algorithm.
- "CEASER CIPHER" -- very basic encryption algorithm, easy to decrypt. Follows "shift by 3" rule.

- ### Symmetric Key Encryption:-
- Encrypting and decrypting the message the message using the same key.
- Encrypted message between the sender and receiver is the randomly arranged bits having no meaning in particular.

- TO ENCRYPT:-
- "echo 'vv7:kOr|E\[PC!JM' > .secretKey" is the command to write the key (that sender uses to encrypt the data & receiver uses to decrypt the data) into the hidden file(represented using .) called secretKey. This file has restricted permissions as it contains sensitive data.
- "cat .secretKey" command used to display the key. Key should be only known to sender and receiver only.
- "echo "My_message_here" > .message.txt" command is used to write the message that needs to be sent to the receiver in encrypted format. Message is written inside the hidden file message.txt
- "openssl enc -e -aes--cbc -salt -in message.txt -out encrypted_message.txt -pass file:.secretKey" command is executed.
   - Here :- 
     - "-e" -> encrypt
     - "aes- -cbc" = encrption algorithm (This is the standard algorithm).
     - "-salt" = Another protection layer that encrypts the message further sent over the channel. We can encrypt the same message again-and-again with same key          and can get different encrypted results every time when same message is floated over the channel.
     - "-in" = input to message.txt
     - "-out" = output (written to encrypted_message.txt file"
     - "-pass file:.secretKey" = providing password(key) as a file (.secretKey file contains the key)
- "cat encrypted_message.txt" command is executed to display the encrypted message.
- "EVE" can get inside that when the same message is floated(though in encrypted form) across the channel, some event is going to take place. Thus, we use -salt which is an added protection protection layer to the message floating through the channel.

- TO DECRYPT:- 
- "openssl enc -d -aes-
  -cbc -salt -in encrypte_message.txt -out original_message.txt -pass file:.secretKey" command
- In above example we have same key to encrypt and decrypt the meassage, thus illustrated symmetric encryption.

- PROBLEM WITH SYMMETRIC KEY ENCRYPTION :- 
  - Sender and receiver have to meet physically to exchange the key in order to maintain the security. It's not feasible to get symmetric key encryption and it's not enough to meet just once because the key should be rotated, hence need to meet whenever the key is rotated. Other ways than meeting physically to transfer the key are insecure. 
