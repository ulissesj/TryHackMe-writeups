## Capture Flag1 at /etc/flag1
The first image shows a web page that has a form and a warn to change to POST request.
![alt text](https://github.com/ulissesj/TryHackMe-writeups/blob/main/FileInclusion/flag1/1_flag1.PNG "Challenge 1 - Web page")

To perform a local file inclusion we need to change to a POST request, since the page is configured to GET request. In this case, I used "curl" to get the flag

```
$ curl -X POST -d 'file=/etc/flag1' http://MACHINE_IP/challenges/chall1.php  
```
The payload is getting argument '-d' to be content-type application/x-www-form-urlencoded.
After that, the page is displayed at the terminal and we get the flag

![alt text]( "Challenge 1 - Flag1")
