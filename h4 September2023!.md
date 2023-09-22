# h4 September2023!

# Schneier 2015: Applied Cryptography: One-way functions and One-way hash functions

## One way functions are:

- Fundamental for various cryptographic protocols.
- Are easy to compute in one direction but extremely hard to reverse.
- Impractical to reverse compute, even with the combined computing power of all the world's computers.

- One way functions a secret "trapdoor" element, making them easy in one direction and hard in the reverse, but with knowledge of the secret, the reverse computation is feasible.


## One-way hash functions:
- Are also known as compression function, message digest, cryptographic checksum, etc.
- Are central to modern cryptography and a fundamental building block for various protocols.
- Are functions that converts a variable-length input strings (pre-images) into a fixed-length output strings (hash values).

- A one-way hash function is easy to compute in one direction (from pre-image to hash value), but hard to generate a pre-image from a given hash value. Also hash functions are collision-free: its hard to create two diffrent pre-images that produce same hash value.
- The security of a one-way hash function lies in its one-wayness; the output is not discernibly dependent on the input.

File fingerprinting:

- Is used to verify the integrity of files without transferring the entire file. Instead, parties share and verify hash values.
- Message Authentication Codes (MAC): Are an extension of one-way hash functions, incorporating a secret key along with the pre-image.

# Install Hashcat. Test it with a sample hash.

## Installing hashcat and making preparations for cracking the password
```
$ sudo apt-get update
$ sudo apt-get -y install hashid hashcat wget

```

Updating system and installing hashcat.

```
$ mkdir hashed
$ cd hashed

```
![image](https://github.com/WindoCode/Infosec/assets/110290723/748e361f-68b4-41fd-9bb6-c979d844b70b)

Making new folder for cracking password!

```
$ wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
$ tar xf rockyou.txt.tar.gz
$ rm rockyou.txt.tar.gz

```

Downloading rockyou.txt which contains over 14 million words. Unzipping the tar file to retrieve txt file and removing the tar file afterwards.

![image](https://github.com/WindoCode/Infosec/assets/110290723/0e6a7f7b-f564-4ce5-b13e-5e4c13473119)


## Cracking password

Lets analyze what encryption this hash could use.

```
$ hashid -m 8eb8e307a6d649bc7fb51443a06a216f

```

![image](https://github.com/WindoCode/Infosec/assets/110290723/773bf689-81dc-475b-9590-77c62dd69baf)

As we see from top answers, password is likely hashed with MD hash function. MD5 is cracked hash function, and we try that to crack the password.

To crack the password using MD5, we need next commands:

```
$ hashcat -m 0 '8eb8e307a6d649bc7fb51443a06a216f' rockyou.txt -o solved

```

-m 0 = m means mode, 0 states that we want to try cracking md5 hashed password.
Next we give the password we want to crack and the dictionary we want to use for cracking.
-o = output, we want the result to file called "solved".

![image](https://github.com/WindoCode/Infosec/assets/110290723/c08875b2-7856-4657-9704-eb90dad78713)

As we see, the password is cracked after using the command and the result is found from "solved" - file. I used ls command to see that the output file has been generated. Lets open the file to see our result:

```
$ cat solved

```

Result: february

![image](https://github.com/WindoCode/Infosec/assets/110290723/a2118366-2381-4c58-82a4-e28dac7cedf4)



## Gone phising 

### Target:

- Organization: For this exersise I would target small to medium sized company that handles sensitive customer information.
- Person: Working in marketing,accounting or sales. Somebody who probably has higher access to company data than normal employee.

### Goals for this email: 
- Create a sense of urgency to prompt quick action.
- Convey that the recipient's account is at risk, and action is necessary.
- Harvest passwords from not tech-savvy personnel to access company's systems. Using same password for multiple platforms.


### What tactics are you using?

Psychological:
- Authority (Cialdini): Positioning as a LinkedIn security officer to establish trust and credibility.
- Urgency: Implying that immediate action is crucial to prevent malicious account usage.

Technical Tactics:

- Phishing Link: A disguised URL leading to a page designed to look like a login portal. This is where the attack would take place, capturing login credential.

- For this exercise I would use [Blackeye](https://github.com/An0nUD4Y/blackeye). Very easy to use tool that can run fake login page easily. Would paste the login page to button in the email-link. This way we harvest the login.



Brackets would be replaced with real information. This email is created for educational purposes only.
![image](https://github.com/WindoCode/Infosec/assets/110290723/5647cda4-cc6d-4a4c-a6f9-4fa99e0cf45a)




