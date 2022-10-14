# Capture Flag2 at /etc/flag2
There is a warning on the page indicating that only admins can access the page, we need to change the cookies and get admin.
![alt text](https://github.com/ulissesj/TryHackMe-writeups/blob/main/FileInclusion/flag2/1_flag2.PNG "Challenge 2 - Web page")
Opening the devtool of the browser, we can access the cookie and change from guest's cookie it to admin's.
![alt text](https://github.com/ulissesj/TryHackMe-writeups/blob/main/FileInclusion/flag2/2_flag2.PNG "Challenge 2 - Admin Cookie")
Reloading the page we can see that we are admin, the current path and also an include function warning.
![alt text]("https://github.com/ulissesj/TryHackMe-writeups/blob/main/FileInclusion/flag2/3_flag2.PNG Challenge 2 - Include warning")
We have to peform a path traversal to get in the root directory and add a NULL byte '%00' and the of the string to bypass the ".php" extension file.
**NOTE: This is solved since PHP 5.4**
This payload "../../../../etc/flag2%00" is stored at the cookie field edited in the devtool.
![alt text](https://github.com/ulissesj/TryHackMe-writeups/blob/main/FileInclusion/flag2/4_flag2.PNG "Challenge 2 - Payload")
Reload the page again and we have the flag
![alt text](https://github.com/ulissesj/TryHackMe-writeups/blob/main/FileInclusion/flag2/5_flag2.PNG "Challenge 2 - Flag 2")
