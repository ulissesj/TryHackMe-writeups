# Capture Flag3 at /etc/flag3

Firstly, I did the usual payload ("/etc/flag3") to view the file, and I got this.

![alt text](https://github.com/ulissesj/TryHackMe-writeups/blob/main/FileInclusion/flag3/1_flag3.PNG "Challenge 3 - Page warning")

We can see that it displays the current path but our payload got filfered. It filters "/" and numbers and even the NULL byte "%00".

Reading the hint from TryHackMe and the PHP manual, I switched the request from GET to POST.

**Note:
The variables in $_REQUEST are provided to the script via the GET, POST, and COOKIE input mechanisms and therefore could be modified by the remote user and cannot be trusted. The presence and order of variables listed in this array is defined according to the PHP request_order, and variables_order configuration directives.**

Trying to request POST the page I noticed that it returned "File Content Preview of /etc/flag3", so it turns out that it bypassed the filters leading to the final payload.
![alt text](https://github.com/ulissesj/TryHackMe-writeups/blob/main/FileInclusion/flag3/2_flag3.PNG "Challenge 3 - Bypass filters")
```
$ curl -X POST -d 'file=/etc/flag3%00' http://MACHINE_IP/challenges///////chall3.php --output -
```

It so returned the flag.

![alt text](https://github.com/ulissesj/TryHackMe-writeups/blob/main/FileInclusion/flag3/3_flag3.PNG "Challenge 3 - Flag 3")

