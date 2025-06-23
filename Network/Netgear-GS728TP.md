# Netgear SmartSwitch GS752TP | GS728TP/v2 | GS728TPP/v2 | GS752TPv2 | GS752TPP

This documentation will work for all of the Netgear switches mentioned in the title.

![](https://www.netgear.com/images/support/Switches/SmartManagedSwitches/GS728TP.png)

**GS728TP — 28-Port Gigabit Ethernet Smart Switch with 4 SFP Ports (16 PoE, 8 PoE+) (192W)**

## **Documentation**

[Product Data Sheet](https://www.downloads.netgear.com/files/GDC/datasheet/en/GS516TP-GS728TP-GS728TPP-GS752TP.pdf)

[Hardware Installation Guide](https://www.downloads.netgear.com/files/GDC/GS728TP/GS728TP_TPP_752TP_HIG_18Dec2012.pdf)

[Installation Guide](https://www.downloads.netgear.com/files/GDC/GS728TP/GS728-52TP-TPP_IG_20Dec2012.pdf)

[Software Administration Manual](https://www.downloads.netgear.com/files/GDC/GS728TP/GS752TP_GS728TP_GS728TPP_SWA_3Dec2013.pdf)

## **Firmware and Software Downloads**

**NETGEAR Switch Discovery Tool for Linux Version 1.2.103 -** File size: 69.7 MB [Download](https://www.downloads.netgear.com/files/GDC/NSDT/NETGEAR_Switch_Discovery_Tool_Linux-V1.2.103.zip)

**NETGEAR Switch Discovery Tool for Windows Version 1.2.103 -** File size: 41 MB [Download](https://www.downloads.netgear.com/files/GDC/NSDT/NETGEAR_Switch_Discovery_Tool_Windows-V1.2.103.zip)

**NETGEAR Switch Discovery Tool for Mac Version 1.2.103 -** File size: 65.4 MB [Download](https://www.downloads.netgear.com/files/GDC/NSDT/NETGEAR_Switch_Discovery_Tool_macOS-V1.2.103.zip)

**Smart Control Center v1.1.3.4 -** File size: 19.7 MB [Download](https://www.downloads.netgear.com/files/GDC/S3300/SCC-Release-V1.1.3.4.exe)

## Enable SSH

1.  **Enable Telnet**  
    In the [manual](http://www.downloads.netgear.com/files/GDC/GS728TP/GS752TP_GS728TP_GS728TPP_SWA_3Dec2013.pdf), Netgear mentions that you can enable telnet “for diagnostic purposes.” To do this, go to [Maintenance > Troubleshooting > Remote Diagnostics](http://blog.hansguthrie.com/wp-content/uploads/2016/01/telnet.png).
2.  **Login**  
    Once you have telnet enabled, connect to it using your favorite telnet client. ([Putty](http://www.putty.org/) works great on Windows). The password is whatever you use to login to the web interface.  
    Username: admin  
    Password: <web interface password> (default: password)
3.  **Enter Configuration Mode**  
    Once you are logged in, you will be at a command prompt with the name of your switch followed by `#` symbol.  
    Type `config` to enter configuration mode.
4.  **Enable SSH**  
    Type `ip ssh server` to enable ssh access. When you press enter, it will save the configuration immediately, and you will see something like  
    `27-Jan-2016 16:16:41 %COPY-N-LOGGINGFILECOPYSTOP: stop log messages related to file copy operations`  
    `27-Jan-2016 16:16:43 %COPY-N-LOGGINGFILECOPY: start log messages related to file copy operations`  
    Wait for this to finish before issuing another command.
5.  **Enable Password Auth**  
    Next, enable password authentication by typing `ip ssh password-auth`. Again, you will see messages while it saves the configuration.
6.  **Change SSH Port (optional)**  
    You can optionally change the SSH port by typing `ip ssh port <port number>`.
7.  **Change SSH Timeout**  
    You can view and change the SSH timeout (as well as other options) from the command line. Enter `config `mode and then type `line ssh`. The prompt will now show `(config-line)#`. Type `do show line ssh` to view the current configuration, and you’ll see that by default the SSH timeout is 10 minutes. You can increase it to 60 minutes with `exec-timeout 60`.

## Convert OpenSSH Public Key to SSH2 Format

```plaintext
ssh-keygen -e -f id_rsa.pub > id_rsa_ssh2.pub
```

## Import SSH Public Key of another host

1.  SSH to Netgear Switch
2.  Enter into Config mode `config`
3.  Enter into ***config-pubkey-chain*** mode: `crypto key pubkey-chain ssh`
4.  Configure new ssh client with username on switch side; type of pubkey import (rsa | dsa): `user-key admin rsa`
5.  Now you should be in ***config-pubkey-key*** mode to import your Pub SSH key:  `key-string`
6.  Now your cursor should be in new line to paste in your SSH2 format key, once done then hit ENTER twice to save it in running-config
7.  You'll be presented with `Fingerprint: 23:2b:5d:5a:8e:80:b0:11:dd:92`
8.  Then enter exit out of entire config mode: `end`
9.  To Save the config in startup-config: `w then press Y`