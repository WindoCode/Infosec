# h4 September2023!

## Install Hashcat. Test it with a sample hash.

### Installing hashcat and making preparations for cracking the password
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


### Cracking password

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

### Trying Hashcat on my host computer






