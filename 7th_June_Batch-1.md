# LEARNINGS FROM 6th JUNE 2023 (Networking Security & Introduction to Cloud Computing)
## Questions:-
- What are compliance regulations?
- What is symmetric and asymmetric encryption? What are different symmetric and asymmetric encryption algorithms?
- What happens if EVE changes the message in symmetric encrption? Would receiver be able to decrypt the original message?
- Is asymmetric key encryption enough to communicate securely over the channel?
- What is TLS Handshake?
-
## Practical:-
- Launch an EC2 instance and connect your instance to your local machine.

## Learnings :-
- Consider 'BOB' and 'ALICE' as two person who communicates with each each other using an insecure channel that can be manipulated and tracked by 'EVE'.
- 'EVE' can see & change the message sent over the channel.
- CRYPTOGRAPHY :- Mathematics fiels to encrypt & decrypt the data.
- CIPHER :- short-name for encryption algorithm.
- "CEASER CIPHER" -- very basic encryption algorithm, easy to decrypt. Follows "shift by 3" rule.

### Symmetric Key Encryption:-
- Encrypting and decrypting the message the message using the same key.
- Encrypted message between the sender and receiver is the randomly arranged bits having no meaning in particular.

TO ENCRYPT:-
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

TO DECRYPT:- 
- "openssl enc -d -aes-
  -cbc -salt -in encrypte_message.txt -out original_message.txt -pass file:.secretKey" command
- In above example we have same key to encrypt and decrypt the meassage, thus illustrated symmetric encryption.

- PROBLEM WITH SYMMETRIC KEY ENCRYPTION :- 
  - Sender and receiver have to meet physically to exchange the key in order to maintain the security. It's not feasible to get symmetric key encryption and it's not enough to meet just once because the key should be rotated, hence need to meet whenever the key is rotated. Other ways than meeting physically to transfer the key are insecure. 
  
 ### Asymmetric Key Encryption
  - rsa asymmetric encryption algorithm
  - EXAMPLE:-
    - Consider "BOB" as sender and "ALICE" as receiver.
      - ALICE generates 2 keys, Public Key and Private Key. He shares his public key with BOB. (Public key be shared to anyone, it's pubicly available).
      - BOB obtains ALICE public key and uses it to encrypt the message to be send over the network.
      - ALICE uses his private key to decrypt the message.
  - In asymmetric key encryption, key used for encrypting & decrypting the message is different.
  - What EVE can do to break the system in this case?
    -  Once ALICE sends his public key to BOB, EVE can see the ALICE's public key. EVE doesn't alows ALICE public key to reach BOB. EVE sends his own public key to BOB. BOB believes that the keyhas been sent by ALICE but don't know the key belongs to EVE. Thus, the reliable and secure communication is lost between the BOB and ALICE. BOB encrypts the message with EVE's public key. EVE can then decrypt the message with his private key. EVE moodifies the encrypted message recived from BOB. Since, EVE possesses the ALICE public key, he encrypts the modified message and sends it to ALICE. ALICE receives the message and assumes the message to be received from BOB.
    -  Thus, EVE successfully modified BOB and ALICE message.
- Thus, certificate authority to which both, BOB nad ALICE trusts provides secure communication between them. 
- If ALICE encrypts the message using his Private key(not available to anyone) and BOB decrypts the message using the public key (anyone can derypt the message using public key), then the communication can be made secure.

### DIGITAL SIGNATURE
- Way to sign the documents digitally (used to prove the authenticity).
- EXAMPLE:-
  - Customer buys a product from Amazon e-commerce platform. Customer visits the tax office to refund the tax. Tax officer asks the customer to prove the authenticity of the receipt that customers carried with him.
  - Customer asks the Amazon to provide a way to prove the authenticity of the receipt. Amazon takes the receipt, digitally signs it and sends the receipt as plain text as well as encrypted to the tax department.
  - Tax officer takes the public key of Amazon and decrypts it and if the decrypted format is same as plain text send by Amazon. the receipt is proved authentative.
 
### DIGITAL CERTIFICATE
- It is a public key signe by someone-else(certificate authority) that both sender and receiver trusts to.
- It's a combination pf digital signature + Asymmetric key encryption + Symmetric key encryption.
- EXAMPLE:- Certificate Authority takes ALICE public key and signs it using their own Private Key.


## CLOUD COMPUTING
- Before the introduction of cloud in the businessses, they used to maintain their own physical server which had the following drawbacks:- 
  - Costly maintanance
  - Physical storage space
  - Hidden costs (like cost to cool down the servers)
  - Physical Security
  - Extra skilled staff to maintain them.
- Public cloud is like electricity service where the consumer don't need to manufacture their own electricity but uses the electricity supllied throgh electric department and pay only for the units of electricity used. Hence, cloud uses Pay-As-You-Go model.
- AWS is the first to launch the public cloud.
- Benefits of using a public cloud:-
 - Easy to go global (easy launching and deployment of applications).
 - Focus on business differentiators (focus only on your business, not on scaling or load balancing(these are taken care of the AWS cloud itself). No need to care about servers).
 - Economies of Scale (easy scaling of the resources required).
- We can implement Monolithic architecture on cloud, but we preferably implements Microservices architecture on cloud.
- AWS has data centres in REGIONS. Each region has a region code. 
- Each region is divided into atleast 3 AVAILABILITY ZONES(AZ). AZ are completely physically seperated. If one of the AZ breaks down,other AZs keeps on functioning well thus ensuring highly available application & ensures fault tolerance (i.e Zero Downtime).
- AZs contains servers.
- We use region code to interact with AWS using bash script.
 
### Security in AWS
- Shared Responsibility Model.
- AWS is responsible for security of the cloud (e.g. AWS promises to provide private network if you need).
- User is responsible for security in the cloud.
 
### Compliance in AWS

