# Schneier 2015: Applied Cryptography: Chapter 1: Foundations

## Sender, Reciever, Messages and Encryption

Sender-Receiver Dynamics

Sender aims to securely transmit a message to a receiver, ensuring confidentiality from potential eavesdroppers.

Messages and Encryption

Message starts as plaintext, the original, readable form. Encryption disguises the message to create ciphertext, concealing its content. Decryption reverses this process, turning ciphertext back into plaintext.

Cryptography and Cryptanalysis

Cryptography is the practice of safeguarding messages, performed by cryptographers. Cryptanalysts specialize in breaking encrypted messages through cryptanalysis. Cryptology encompasses both cryptography and cryptanalysis, rooted in mathematics. Modern cryptologists typically possess expertise in theoretical mathematics.

## Authentication, Integrity, and Nonrepudiation on top of confidentiality

Authentication: The receiver should be able to confirm where a message came from. Nobody should be able to pretend to be someone else.

Integrity: The receiver should be able to check if a message was changed while it was being sent. Nobody should be able to swap a real message for a fake one.

Nonrepudiation: The sender shouldn't be able to lie later and say they didn't send a message. They can't deny sending it.

### Security of algorithms 

Different algorithms offer varying levels of security based on factors like cost, time, and data volume required to break them.
Lars Knudsen classified levels of breaking an algorithm:
1.Total break. A cryptanalyst finds the key, K, such that DK(C) = P.
2.Global deduction. A cryptanalyst finds an alternate algorithm, A, equivalent to DK(C), without knowing K.
3.Instance (or local) deduction. A cryptanalyst finds the plaintext of an intercepted ciphertext.
4. Information deduction. A cryptanalyst gains some information about the key or plaintext. This information could be a few bits of the key, some information about the form of the plaintext, and so forth.

Unconditionally secure algorithms provide no way to recover plaintext, regardless of available ciphertext.
Only a one-time pad is considered unbreakable with infinite resources; all other systems are susceptible to brute-force attacks.
Cryptography primarily focuses on computationally secure systems, which resist attacks given available resources.
Attack complexity is evaluated in terms of data, processing, and storage requirements.
Declaring an algorithm secure based solely on current technology is risky; robust systems are designed to withstand future advances in computing power.

### Steganography
Steganography is a technique to hide secret messages within other messages so that no one even knows there's a secret message present. In the past, people used tricks like invisible inks or tiny marks on paper. Nowadays, people hide messages in pictures by making tiny changes that our eyes can't detect. For example, they might change the tiniest parts of a picture to hide a secret message.

### Substitution ciphers and transposition ciphers

In the past, cryptography used methods that dealt with individual characters. These methods either swapped characters or rearranged them. The more effective ones did both, often multiple times.

Today, things are more advanced, but the basic idea is the same. Now, instead of characters, modern algorithms work with the tiniest units of information called bits (which are like the building blocks of data). Although the "alphabet" has shrunk from 26 letters to just 2 (0 and 1), solid cryptographic methods still mix up and swap elements to keep information secure.

A transposition cipher is a way of hiding a message by rearranging the order of its letters. For example, instead of writing the message in a straight line, you write it in rows. When you read the letters from top to bottom, you get the secret message. However, transposition ciphers can be figured out if you analyze the frequency of the letters. So, sometimes, people use more complicated methods to make it harder to crack.

One famous historical example is the German ADFGVX cipher from World War I, which combined both rearranging and replacing letters. It was a complex code but was eventually solved by a French cryptanalyst. While transposition ciphers are still used today, they have some limitations and are not as common as other methods like substitution ciphers.

### Find out frequency distribution of letters for a language that you know
1.  a  457 350  11,62%
2.  i  421 366  10,71% 
3.  t  388 711   9,88% 
4.  n  341 181   8,67% 
5.  e  323 087   8,21% 
6.  s  309 350   7,86%

Source: [Matti Pääkkönen, ”A: sta ö:hön Suomen yleiskielen kirjaintilastoja](https://jkorpela.fi/kielikello/kirjtil.html)


### Passbolt - Open source password manager.

A password manager protects against several significant threats, but the top three it guards against are:


1. Password Reuse:

Threat: Using the same password across multiple accounts is a common and dangerous practice. If one account is compromised, all others with the same password are vulnerable.

Protection: A password manager generates and stores unique, complex passwords for each account, preventing the risk associated with password reuse.

2. Weak Passwords:

Threat: Many individuals use simple and easily guessable passwords. These are vulnerable to brute-force attacks.

Protection: Password managers encourage the use of strong, complex passwords that are much harder to guess or crack.

3. Phishing Attacks:

Threat: Phishing scams trick users into revealing their login credentials by leading them to fake websites that mimic legitimate ones.

Protection: Password managers include features like auto-fill that only work on legitimate sites, helping users recognize and avoid phishing attempts. They ensure that login information is only entered on trusted, verified websites.

What is encrypted?

Passwords are always encrypted on server side and they never leave device. Passwords are also encrypted on the client side using a browser extension. The browser extension uses OpenPGP, a standard which provides a combination of strong public-key and symmetric cryptography. The private secret key used to decrypt your password is itself encrypted using a passphrase.

The metadata such as the name, the url, the comments, the folder it is in, the list of people who have access to the password are not encrypted, and are stored in plaintext both on the client and server side.

Passbolt is distributed under Free Software Foundation’s GNU AGPL v3.0 licence. AGPL licence works like any other open source license, but with AGPL license ensures all subsequent changes become available to the community. This is why some companies avoid using this license, as it forces all other code to become GPLed software.

If data is truly yours, you can control where your server is located. Either you can run it from your rasperry pi inside your home, or you can host it at cloud. Passbolt doesnt need an internet and it doesnt use any trackers.

For the data in use, only passwords are encrypted. 
For the data in motion, all communication is encrypted using SSL.
For the data at rest, it is possible to encrypt the database at a file system level. This will add a new encryption level that can be useful, if the server is seized or stolen. I.e NTFS for Windows and F2FS for Linux 4.2+.

# How to self-host passbolt password manager using docker on your own computer.

Pre-Installed:
Docker hub (Windows)
Linux on windows (WSL)

1. Installing passbolt to docker

On CLI:
`` docker login ``

To download the passbolt image for docker:
`` curl https://download.passbolt.com/ce/docker/docker-compose-ce.yaml --output docker-compose-ce.yaml ``

To run the docker container:
`` docker-compose -f docker-compose-ce.yaml up -d ``

Lets check if the container is running on docker:
`` docker ps ``
![image](https://github.com/WindoCode/Infosec/assets/110290723/978f018a-b59b-423c-85a2-7f52b07a0d2c)

With this command line we gave ourselves admin rights. Create an admin account, change EMAIL, FIRSTNAME, LASTNAME variables::

`` docker-compose -f docker-compose-ce.yaml exec passbolt su -m -c "/usr/share/php/passbolt/bin/cake passbolt register_user -u EMAIL -f FIRSTNAME -l LASTNAME -r admin" -s /bin/sh www-data``
![image](https://github.com/WindoCode/Infosec/assets/110290723/a4ccd407-728c-431e-8647-f6a2510a5118)


We want to add few enviromental variables on docker-compose-ce file. 

``notepad docker-compose-ce.yaml``

We want to add following variables to enviroment tab. Save afer edited. :

``
 APP_FULL_BASE_URL: https://localhost
      PASSBOLT_SSL_FORCE: "false"
      EMAIL_DEFAULT_FROM_NAME: 'NAME'
      EMAIL_DEFAULT_FROM: 'your@mail.com'
      EMAIL_TRANSPORT_DEFAULT_HOST: 'localhost'
      EMAIL_TRANSPORT_DEFAULT_PORT: 25
      EMAIL_TRANSPORT_DEFAULT_USERNAME:
      EMAIL_TRANSPORT_DEFAULT_PASSWORD:
      EMAIL_TRANSPORT_DEFAULT_TLS: ``

Follow the link we got after adding ourselves as admin. Ignore the certificate warning.
![image](https://github.com/WindoCode/Infosec/assets/110290723/b8388bff-d30c-4e7c-9deb-00c11d58d3cf)

Passbolt uses browser extensions with passwords. Install the extesion from your browser.

Add your master password and select your own security token. After this part you are given recovery kit. You should keep this ideally somewhere offline.

Now you are greeted with main page of your passbolt server! Lets add your account of choice to passbolt!

1. Go to login page of your choice!
2. Click passbolt icon, next to login input
3. Click create new identity
4. You are greeted with a popup that you add your login details in, you may change the name to what ever you like as long as you regonize it on passbolt page.
   ![image](https://github.com/WindoCode/Infosec/assets/110290723/4e2b2d4d-5718-4d40-be01-3e5dfb15d6b8)
6. Your password is stored now on passbolt website. I recommend generating new password on passbolt page and changing it at service to the one generated. Passbolt passwords have great entropy, which make your PW highly secured.
![image](https://github.com/WindoCode/Infosec/assets/110290723/5f0a4872-6b4d-424a-9cb3-859356cf2521)


## Encrypt and decrypt a message

### Encrypting a Message:

Step 1: Install PGP Software
You'll need to have PGP software installed on your computer. Popular options include GnuPG (an open-source implementation of PGP) or commercial options like Symantec's PGP.

Step 2: Generate a PGP Key Pair
Open your PGP software and create a new key pair. This will generate a public key (which you can share with others) and a private key (which you must keep secret).

Step 3: Obtain Recipient's Public Key
If you're sending a message to someone, you need their public key. They can send it to you directly, or you can find it on a public key server.

Step 4: Encrypt the Message
Open your PGP software and select the option to encrypt a message.
You'll be prompted to select the recipient's public key. Choose the appropriate key.

Step 5: Compose and Encrypt Your Message

Write your message in the provided text area.
When you're ready to encrypt, use the recipient's public key to do so.
Step 6: Send the Encrypted Message

You can now send the encrypted message through your preferred communication channel (email, messaging apps, etc.).

### Decrypting a Message:
Step 1: Receive the Encrypted Message
The recipient receives the encrypted message.

Step 2: Import Your Private Key
Open your PGP software and import your private key.

Step 3: Decrypt the Message
Open the encrypted message using your PGP software.
The software will prompt you for your private key passphrase (this is the password you set when you generated your keys).
Once you enter the passphrase, the message will be decrypted and displayed.

Step 4: Read the Decrypted Message
You can now read the decrypted message.

# a) ETAOIN

First I saw patterns ”DHHP//”, which showed like a link. ”OWG” in this case would standout as COM, as common domain. I saw KWU standout a lot. I would assume this is some common word, like you! As E is the most common letter in english, I gave E = I.

On second part I counted the top 5 most frequent numbers. I 12 times, B 12 times, M 10 times, T 10 times, AKOWY 8 times. I added above letters to my decypher alpabet, and started cracking the riddle. As I was solving the riddle, some words missed a letter or two, which were guessable by solving the previous words. Filled up the decypher alphabet and got the answer.

THATS’IT YOU’RE NOW OFFICIALLY A CODEBREAKER. AS YOU MAY SEE SIMPLE SUBSTITUTION CIPHERS CAN BE BROKEN WITH FREQUENCY ANALYSIS SE YOU AR http://TEROKARVINEN.COM.

![image](https://github.com/WindoCode/Infosec/assets/110290723/1718cc69-530a-4d09-8960-d888bdac3e8d)

