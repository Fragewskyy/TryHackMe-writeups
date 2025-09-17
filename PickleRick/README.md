# Pickle Rick
## IP
- 10.10.172.228
## Task

This Rick and Morty-themed challenge requires you to exploit a web server and find three ingredients to help Rick make his potion and transform himself back into a human from a pickle.

Deploy the virtual machine on this task and explore the web application

## Steps

Ok so first hint on site were weird BURRRRRP words so let's use Burp Suite and check.

![alt text](image.png)

It seems that our first hint is in html as on photo, so let's save that username:

![alt text](image-1.png)

Let's do nmap scan!

![alt text](image-2.png)

SSH opened maybe we will try dict attack, but let's use GoBuster before.

`gobuster dir -w /usr/share/wordlists/dirb/big.txt -k -u http://10.10.172.228 -x html,php`

Gobuster found a login page, we will try to login using saved username and weird word from robots.txt

![alt text](image-3.png)

BINGO! Now we have access to command panel

![alt text](image-4.png)

After ls there was Sup3rS3cretPickl3Ingred.txt file in directory, cat command was blocked so after using less, first flag is ours.

![alt text](image-5.png)

After short path traversal we found second flag using following command `less "/home/rick/second ingredients"`

![alt text](image-6.png)

Interesting that after sudo -l we have access to all commands without password so we can easily access root folder
Inside root folder there was our third and last flag we did it !

`sudo less /root/3rd.txt`

![alt text](image-7.png)

## Flag

Our first flag is: **mr. meeseek hair**
Our second flag is: **1 jerry tear**
Our second flag is: **fleeb juice**