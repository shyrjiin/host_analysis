#!/usr/bin/python
import pxssh 
import pexpect

hostname ="x.x.x.x"
username = "user"
password = "password"

s = pxssh.pxssh()  #s has the pxssh structure to make the magic happen

s.login(hostname,username,password,login_timeout=20)  #login to the system timeout def is 10



print "================================================================================================================="
print "================================================================================================================="
print "======================LINUX HOST SURVEY SCRIPT==================================================================="
print "================================================================================================================="
print "================================================================================================================="


s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)
s.sendline("hostname")
print s.before
s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)
print "================================================================================================================="

s.sendline("date")
print s.before
s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)
print "================================================================================================================="

s.sendline("uname -a")
print s.before
s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)
print "================================================================================================================="

s.sendline("route -n")
print s.before
s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)
print "================================================================================================================="

s.sendline("netstat -pant")
print s.before
s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)
print "================================================================================================================="

s.sendline("iptables -nL")
print s.before
s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)
print "================================================================================================================="

s.sendline("ufw status numbered")
print s.before
s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)
print "================================================================================================================="

s.sendline("dpkg -l")
print s.before
s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)

print "================================================================================================================="
s.sendline("yum list")
print s.before
s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)
print "================================================================================================================="

s.sendline('for user in `cat /etc/passwd | cut -d \: -f1`; do crontab -l -u $user; done')
s.prompt() # waits for the above line to complete.  (waiting for the prompt to return)
print "================================================================================================================="

print s.before
s.sendline("find / -type f -perm /4000 -ls 2>/dev/null")
s.prompt()
print "================================================================================================================="

print s.before # data before the prompt is is s.before
s.sendline('for file in `find -H /etc/ -type f`; do sha1sum $file; done') #run the hash for loop
s.prompt()  #wait for the command to finish
print "================================================================================================================="

finddata = s.before   #save the data to another variable (not required)
for line in finddata.split('\r\n'):   #loop through the output from find 1 line at a time
	if len(line.split()) == 2:  # test for lines with only 2 columns (split by white space)
		print line # print out the lines that match if statement
