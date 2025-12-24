##### Using the `sendmail` client

`sendEmail -s 192.168.50.121 -t victim@bar.com -f attacker@foo.com -u "test"  -o message-content-type=html -o message-file=./template.html -a iCalendar.ics`

##### Using Telnet

```
telnet <server_address> <port>
EHLO hostname
MAIL FROM: <attacker@foo.com>
RCPT TO: <victim@bar.com> #You can repeat this for multiple recipients
DATA
Subject: Super Legit Email 

Hi, This is the body of an email. #Body, pressing Enter for new lines as needed.

Thanks,
Attacker

.

QUIT
```

