# Display CentOS 6 Applications Remotely (X11 Forwarding)
Sometimes you need to display an CentOS's application GUI of a remote machine to your local machine.

For example, you login to a CentOS server via SSH and want to launch the server's "gedit" application with GUI displayed on your local machine to edit some file on server.

---

**Prerequisites:**

* Local machine: must running X server

* Remote machine: allow SSH

---

### Config SSH on remote machine to allow X11 Forwarding
Open file */etc/ssh/ssh_config* and make sure that the following directives is set:
```
X11Forwarding yes

X11DisplayOffset 10

X11UseLocalhost yes

ForwardX11Trusted yes
```

Restart SSH: ``service sshd restart``


Install *xorg-x11-auth.x86_64* (if need):
``yum install xorg-x11-xauth.x86_64``

Check file */var/lib/dbus*, if you see that either the file ‘‘machine-id” is empty or missing, fix it by:
``dbus-uuidgen --ensure``

### Connect and run application with X11 forwarding
Login to remte machine by SSH: ``ssh -Y user@hostname``

Run application (eg. "gedit") normally, you will see the application GUI displayed on your local machine.

---

References:
[http://www.techotopia.com/index.php/Displaying_CentOS_6_Applications_Remotely_%28X11_Forwarding%29](http://www.techotopia.com/index.php/Displaying_CentOS_6_Applications_Remotely_%28X11_Forwarding%29)

[http://itvomit.com/2013/09/27/centos6-4-minamla-x11-forwarding-session-using-ssh-fails/](http://itvomit.com/2013/09/27/centos6-4-minamla-x11-forwarding-session-using-ssh-fails/)
