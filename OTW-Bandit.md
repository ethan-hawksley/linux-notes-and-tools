### Intro
ssh -p 2220 bandit0@bandit.labs.overthewire.org
Password: bandit0

### Level 0
ls
cat readme
Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

### Level 1
ls
cat ./-
Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

### Level 2
ls
cat './--spaces in this filename--'
Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

### Level 3
ls
cd inhere
ls
ls -a
cat ...Hiding-From-You
Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

### Level 4
ls
cd inhere
ls -a
cat ./-file00
cat ./-file01
cat ./-file02
cat ./-file03
cat ./-file04
cat ./-file05
cat ./-file06
cat ./-file07
Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

### Level 5
ls
cd inhere
ls -a
find . -size 1033c
cat ./maybehere07/.file2
Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

### Level 6
find / -size 33c -user bandit7 -group bandit6
cat /var/lib/dpkg/info/bandit7.password
Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

### Level 7
ls
less data.txt
grep millionth data.txt
Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

### Level 8
ls
less data.txt
sort data.txt | uniq -u
Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

### Level 9
ls 
grep '\=\=\=' data.txt -a
Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

### Level 10
ls
less data.txt
base64 -d data.txt
Password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

### Level 11
ls
less data.txt
tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
Password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

### Level 12
mktemp -d
cd /tmp/tmp.zyBMFfHWq8
mv file.zip file.gz
gzip -d file.gz
bzip2 -d file
mv file.out file.gz
gunzip file.gz
mv file file.zip
tar -xf file.zip
tar -xf data5.bin
bzip2 -d data6.bin
tar -xf data6.bin.out
mv data8.bin data8.gz
gunzip data8.gz
cat data8
Password: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

### Level 13
ls
cat sshkey.private
exit
wl-paste > bandit14.private
chmod 600 bandit14.private
ssh -p 2220 bandit14@bandit.labs.overthewire.org -i bandit14.private
Password:
```
-----BEGIN RSA PRIVATE KEY-----  
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+  
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB  
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb  
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV  
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7  
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA  
J3j/RWmap9M5zfJ/wb2bfidNpwbB8rsJ4sZIDZQ7XuIh4LfygoAQSS+bBw3RXvzE  
pvJt3SmU8hIDuLsCjL1VnBY5pY7Bju8g8aR/3FyjyNAqx/TLfzlLYfOu7i9Jet67  
xAh0tONG/u8FB5I3LAI2Vp6OviwvdWeC4nOxCthldpuPKNLA8rmMMVRTKQ+7T2VS  
nXmwYckKUcUgzoVSpiNZaS0zUDypdpy2+tRH3MQa5kqN1YKjvF8RC47woOYCktsD  
o3FFpGNFec9Taa3Msy+DfQQhHKZFKIL3bJDONtmrVvtYK40/yeU4aZ/HA2DQzwhe  
ol1AfiEhAoGBAOnVjosBkm7sblK+n4IEwPxs8sOmhPnTDUy5WGrpSCrXOmsVIBUf  
laL3ZGLx3xCIwtCnEucB9DvN2HZkupc/h6hTKUYLqXuyLD8njTrbRhLgbC9QrKrS  
M1F2fSTxVqPtZDlDMwjNR04xHA/fKh8bXXyTMqOHNJTHHNhbh3McdURjAoGBANkU  
1hqfnw7+aXncJ9bjysr1ZWbqOE5Nd8AFgfwaKuGTTVX2NsUQnCMWdOp+wFak40JH  
PKWkJNdBG+ex0H9JNQsTK3X5PBMAS8AfX0GrKeuwKWA6erytVTqjOfLYcdp5+z9s  
8DtVCxDuVsM+i4X8UqIGOlvGbtKEVokHPFXP1q/dAoGAcHg5YX7WEehCgCYTzpO+  
xysX8ScM2qS6xuZ3MqUWAxUWkh7NGZvhe0sGy9iOdANzwKw7mUUFViaCMR/t54W1  
GC83sOs3D7n5Mj8x3NdO8xFit7dT9a245TvaoYQ7KgmqpSg/ScKCw4c3eiLava+J  
3btnJeSIU+8ZXq9XjPRpKwUCgYA7z6LiOQKxNeXH3qHXcnHok855maUj5fJNpPbY  
iDkyZ8ySF8GlcFsky8Yw6fWCqfG3zDrohJ5l9JmEsBh7SadkwsZhvecQcS9t4vby  
9/8X4jS0P8ibfcKS4nBP+dT81kkkg5Z5MohXBORA7VWx+ACohcDEkprsQ+w32xeD  
qT1EvQKBgQDKm8ws2ByvSUVs9GjTilCajFqLJ0eVYzRPaY6f++Gv/UVfAPV4c+S0  
kAWpXbv5tbkkzbS0eaLPTKgLzavXtQoTtKwrjpolHKIHUz6Wu+n4abfAIRFubOdN  
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==  
-----END RSA PRIVATE KEY-----
```

cat /etc/bandit_pass/bandit14
Password: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

### Level 14
nmap localhost
nc localhost 30000
Password: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

### Level 15
openssl s_client localhost:30001
Password: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

### Level 16
nmap -p 31000-32000 localhost
openssl s_client -connect localhost:31790 -quiet
Password:
```
-----BEGIN RSA PRIVATE KEY-----  
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ  
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ  
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu  
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW  
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX  
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD  
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl  
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd  
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC  
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A  
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama  
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT  
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx  
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd  
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt  
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A  
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi  
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg  
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu  
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni  
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU  
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM  
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b  
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3  
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=  
-----END RSA PRIVATE KEY-----
```

### Level 17
ls
cat passwords.old
cat passwords.new
diff passwords.old passwords.new
Password: x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

### Level 18
ssh -T -p 2220 bandit18@bandit.labs.overthewire.org
ls
cat readme
Password: cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

### Level 19
./bandit20-do
./bandit20-do whoami
./bandit20-do ls /etc/bandit_pass
./bandit20-do cat /etc/bandit_pass/bandit20
Password: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO

### Level 20
nc -l 5000
Ctrl+Z
./suconnect 5000
Ctrl+Z
fg 1
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Ctrl+Z
fg 2
Ctrl+Z
fg 1
Password: EeoULMCra2q0dSkYj561DX7s1CpBuOBt

### Level 21
ls /etc/cron.d
cat /etc/cron.d/*
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Password: tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q

### Level 22
ls /etc/cron.d
cat /etc/cron.d/*
cat /usr/bin/cronjob_bandit22.sh
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
Password: 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga

### Level 23
cat /etc/cron.d/cronjob_bandit24
cat /usr/bin/cronjob_bandit24.sh
vi /var/spool/bandit24/foo/runme.sh
	cat /etc/bandit_pass/bandit24 > /tmp/tempoutputfile
cat /tmp/tempoutputfile
Password: gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8

### Level 24
printf "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 %s\n" {0000..9999}  
| nc localhost 30002
Password: iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

### Level 25
ls
cat bandit26.sshkey
Password:
```
-----BEGIN RSA PRIVATE KEY-----  
MIIEpQIBAAKCAQEApis2AuoooEqeYWamtwX2k5z9uU1Afl2F8VyXQqbv/LTrIwdW  
pTfaeRHXzr0Y0a5Oe3GB/+W2+PReif+bPZlzTY1XFwpk+DiHk1kmL0moEW8HJuT9  
/5XbnpjSzn0eEAfFax2OcopjrzVqdBJQerkj0puv3UXY07AskgkyD5XepwGAlJOG  
xZsMq1oZqQ0W29aBtfykuGie2bxroRjuAPrYM4o3MMmtlNE5fC4G9Ihq0eq73MDi  
1ze6d2jIGce873qxn308BA2qhRPJNEbnPev5gI+5tU+UxebW8KLbk0EhoXB953Ix  
3lgOIrT9Y6skRjsMSFmC6WN/O7ovu8QzGqxdywIDAQABAoIBAAaXoETtVT9GtpHW  
qLaKHgYtLEO1tOFOhInWyolyZgL4inuRRva3CIvVEWK6TcnDyIlNL4MfcerehwGi  
il4fQFvLR7E6UFcopvhJiSJHIcvPQ9FfNFR3dYcNOQ/IFvE73bEqMwSISPwiel6w  
e1DjF3C7jHaS1s9PJfWFN982aublL/yLbJP+ou3ifdljS7QzjWZA8NRiMwmBGPIh  
Yq8weR3jIVQl3ndEYxO7Cr/wXXebZwlP6CPZb67rBy0jg+366mxQbDZIwZYEaUME  
zY5izFclr/kKj4s7NTRkC76Yx+rTNP5+BX+JT+rgz5aoQq8ghMw43NYwxjXym/MX  
c8X8g0ECgYEA1crBUAR1gSkM+5mGjjoFLJKrFP+IhUHFh25qGI4Dcxxh1f3M53le  
wF1rkp5SJnHRFm9IW3gM1JoF0PQxI5aXHRGHphwPeKnsQ/xQBRWCeYpqTme9amJV  
tD3aDHkpIhYxkNxqol5gDCAt6tdFSxqPaNfdfsfaAOXiKGrQESUjIBcCgYEAxvmI  
2ROJsBXaiM4Iyg9hUpjZIn8TW2UlH76pojFG6/KBd1NcnW3fu0ZUU790wAu7QbbU  
i7pieeqCqSYcZsmkhnOvbdx54A6NNCR2btc+si6pDOe1jdsGdXISDRHFb9QxjZCj  
6xzWMNvb5n1yUb9w9nfN1PZzATfUsOV+Fy8CbG0CgYEAifkTLwfhqZyLk2huTSWm  
pzB0ltWfDpj22MNqVzR3h3d+sHLeJVjPzIe9396rF8KGdNsWsGlWpnJMZKDjgZsz  
JQBmMc6UMYRARVP1dIKANN4eY0FSHfEebHcqXLho0mXOUTXe37DWfZza5V9Oify3  
JquBd8uUptW1Ue41H4t/ErsCgYEArc5FYtF1QXIlfcDz3oUGz16itUZpgzlb71nd  
1cbTm8EupCwWR5I1j+IEQU+JTUQyI1nwWcnKwZI+5kBbKNJUu/mLsRyY/UXYxEZh  
ibrNklm94373kV1US/0DlZUDcQba7jz9Yp/C3dT/RlwoIw5mP3UxQCizFspNKOSe  
euPeaxUCgYEAntklXwBbokgdDup/u/3ms5Lb/bm22zDOCg2HrlWQCqKEkWkAO6R5  
/Wwyqhp/wTl8VXjxWo+W+DmewGdPHGQQ5fFdqgpuQpGUq24YZS8m66v5ANBwd76t  
IZdtF5HXs2S5CADTwniUS5mX1HO9l5gUkk+h0cH5JnPtsMCnAUM+BRY=  
-----END RSA PRIVATE KEY-----
```
### Level 26
SSH with small terminal.
v to enter vi.
:shell=/bin/sh
:!sh
bash
ls
./bandit27-do
./bandit27-do cat /etc/bandit_pass/bandit27
Password: upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB

### Level 27
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
cd repo
ls
cat README
Password: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN

### Level 28
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
cd repo
ls
cat README.md
git log
git checkout a1487fd098591dfa210ede70ba60f7093f47d20d
cat README.md
Password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7 

### Level 29
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
cd repo
ls
cat README.md
git log
git branch -a
git switch dev
cat README.md
Password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL

### Level 30
git clone ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo
cd repo
ls
cat README.md
git log
git branch -a
git tag
git checkout secret
git show secret
Password: fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy

### Level 31
git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo
cd repo
ls
cat README.md
echo 'May I come in?' > key.txt
rm .gitignore
git add .
git commit -m "feat: add file"
git push
Password: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K

### Level 32
$0
bash
cat /etc/bandit_pass/bandit33
Password: tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0

### Level 33
ls
cat README.txt
Password: Wargame completed!