I had trouble finding all the places to change max files that can be opened on Ubuntu and Debian in one spot.

So here we go:

### Step 1
First modify /etc/sysctl.conf add the following line: need I say check that it isn’t there already?

    fs.file-max = 131072
To avoid a reboot type in the following to reread the configuration and apply it to the system.

    sysctl -p
### Step 2
Now include the pam limits shared library to:

    /etc/pam.d/common-session
    /etc/pam.d/common-session-interactive
The syntax follows:

    session required pam_limits.so
### Step 3
You are ready to modify the limits config file (/etc/security/limits.conf):

    elasticsearch  -  nofile   131072
    elasticsearch  -  memlock  unlimited