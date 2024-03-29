# Darknet Diaries Podcast: How Jason robbed the wrong bank in Beirut.

In this episode of the Darknet Diaries podcast, Jason E. Street, a security expert, recounts a story about conducting a security awareness engagement for a bank in Beirut. Jason specializes in testing physical security by attempting to breach a company's premises without actually causing harm. In this case, his mission was to access the bank's teller computers without stealing anything.

Jason's approach is to blend in and appear non-threatening. He enters the bank, engages with employees, and tries to gain their trust. During the engagement, he plugs in a USB rubber ducky into various computers, which simulates an attack but doesn't harm the systems. Jason is able to compromise multiple machines and even goes behind the teller line, all while employees assume he's authorized to be there.

In second instance, Jason accidentally enters the wrong bank, believing it's the correct one. Fortunately, his mistake is discovered by his driver before he proceeds with the engagement. After walking into the right bank, he successfully compromises computers at the bank's headquarters by showing them a forged email from a fictitious audit team.

However, things take a turn when an employee at the third bank becomes suspicious. Jason attempts to use his usual tactics but is met with skepticism. When he presents a forged email, the employee asks him to retrieve more documentation from his car, inadvertently allowing Jason to leave.

Jason shares in this episode the importance of being cautious when dealing with strangers in secure areas, verifying their credentials, and not hesitating to report suspicious activity. His engaging storytelling style highlights the significance of physical security awareness in preventing breaches.


## Installing Debian 12.x

For this excersise I installed image **debian-live-12.0-amd64-xfce** as reguested.

On VirtualBox:

Create Virtual Machine", click "Expert Mode"\
Name: DebianTeroKarvinenCom\
Type: Linux\
Version: Debian (64-bit)\
Memory Size: 4000 MB\
Hard disk: Create a virtual hard disk now - yes - 60GB.\

After this I selected the right image from virtual machine storage settings. Booted to desktop and started the installation of Debian.\ 

Language: American English\
Location: Finland\
Default Keyboard Model: Finnish\
Erase disk: yes\
Encrypt: no (Because this is a virtual computer.)\
Boot loader location: Master Boot Record\
User: Valtteri\
Computer name: computer\
Password: xxxxxxxxx\
**Install**

### Updating all programs and security stuff

On desktop, I opened terminal and gave command: 

`$ sudo apt-get update`

This command gives us information what we could update.

![epic](https://i.imgur.com/njfO2Ui.png)


After this we updated every possible program that had and update with command:

`$ sudo apt-get -y dist-upgrade`

![image](https://i.imgur.com/IEvtamo.png)

Rebooted the virtual machine.

#### Installing firewall

Went back to terminal and gave 2 commands to install firewall and enabling the firewall. 

`$ sudo apt-get -y install ufw`
`$ sudo ufw enable`

![image](https://i.imgur.com/7MHgBpo.png)

Rebooted and now I have successfully installed linux. 👍

#Reference

https://terokarvinen.com/2023/information-security-2023-autumn/
