# UNIX/Linux operating systems (Basic).

Linux system installation and updates. Administration basics.

## Part 1. Installation of the OS

##### Install Ubuntu 20.04 Server LTS.
![InstallOS](misc/images/P1.png)


## Part 2. Creating a user

##### Create a user other than the one created during installation. The user must have permission to read logs from the /var/log folder.
![CreateUser1](misc/images/P2_1.png)
![CreateUser2](misc/images/P2_2.png)
![CreateUser3](misc/images/P2_3.png)
![CreateUser4](misc/images/P2_4.png)
![CreateUser5](misc/images/P2_5.png)


## Part 3. Setting up the OS network

##### Set the machine name as user-1
##### Set the time zone corresponding to your current location.
![OSNet1](misc/images/P3_1.png)

##### Output the names of the network interfaces using a console command.
![OSNet2](misc/images/P3_2.png)

Interface lo can be used by network client software to communicate with a server application located on the same computer. That is, if you specify the URL http://127.0.0.1/ or http://localhost/ in the web browser on the computer where the web server is running, it takes you to that computer's web site. This mechanism works without any active connection, so it is useful for testing services without compromising their security as with remote network access.

##### Define and display the external ip address of the gateway (ip) and the internal IP address of the gateway, aka default ip address (gw).
![OSNet3](misc/images/P3_3.png)

Dynamic Host Configuration Protocol (DHCP).

##### Set static (manually set, not received from DHCP server) ip, gw, dns settings (use public DNS servers, e.g. 1.1.1.1 or 8.8.8.8).
![OSNet4](misc/images/P3_4.png)
![OSNet4.1](misc/images/P3_4.1.png)

##### Reboot the virtual machine. Make sure that the static network settings (ip, gw, dns) correspond to those set in the previous point.
![OSNet5](misc/images/P3_5.png)
![OSNet5.1](misc/images/P3_5.1.png)


## Part 4. OS Update

##### Update the system packages to the latest version
![OSUpdate](misc/images/P4_1.png)


## Part 5. Using the **sudo** command

##### Allow user created in [Part 2](#part-2-creating-a-user) to execute sudo command.

![sudo1](misc/images/P5_1.png)

sudo allows a permitted user to execute a command as the superuser or another user, as specified by the security policy.  The invoking user's real (not effective) user-ID is used to determine the user name with which to query the security policy.

![sudo2](misc/images/P5_2.png)


## Part 6. Installing and configuring the time service

##### Set up the automatic time synchronisation service.

![time](misc/images/P6_1.png)

output of the timedatectl command (to configure the automatic time synchronization service "timedatectl set-ntp on").


## Part 7. Installing and using text editors

##### Install **VIM** text editor (+ any two others if you like **NANO**, **MCEDIT**, **JOE** etc.)

![TextEditor](misc/images/P7_1_0.png)
![TextEditor](misc/images/P7_1_1.png)
![TextEditor](misc/images/P7_1_2.png)

`joe test_joe.txt`

![TextEditor](misc/images/P7_2_1.png)

CTRL + K - X for exit with save

![TextEditor](misc/images/P7_2_5.png)

`joe test_joe.txt`

![TextEditor](misc/images/P7_2_2.png)

CTRL + C for exit without save

![TextEditor](misc/images/P7_2_3.png)

`vim test_vim.txt`

:wq for exit with save

![TextEditor](misc/images/P7_3_1.png)

`vim test_vim.txt`

:q! for exit without save

![TextEditor](misc/images/P7_3_2.png)

`nano test_nano.txt`

Ctrl + S then Ctrl + X for exit with save

![TextEditor](misc/images/P7_4_1.png)

`nano test_nano.txt`

Ctrl + X then 'n' for exit without save

![TextEditor](misc/images/P7_4_2.png)


## Part 8. Installing and basic setup of the **SSHD** service

##### Install the SSHd service.
`sudo apt-get install openssh-server`

`sudo systemctl enable ssh` - to enable ssh on boot

##### Add an auto-start of the service whenever the system boots.
`systemctl list-unit-files --type=service --state=enabled`

![SSHD](misc/images/P8_1.png)

##### Reset the SSHd service to port 2022.
`vim /etc/ssh/sshd_config`

![SSHD](misc/images/P8_2.png)

![SSHD](misc/images/P8_3.png)

`service ssh restart`

`netstat -tan`

netstat: -t (--tcp) tcp protocol output -a (--all) Show both listening and non-listening sockets -n (--numeric) Show numerical addresses instead of trying to determine symbolic host, port or user names Proto - the protocol (tcp, udp, raw) used by the socket.

Recv-Q - the count of bytes not copied by the user program connected to this socket.

Send-Q - the count of bytes not acknowledged by the remote host.

Local Address - Address and port number of the local end of the socket. Unless the --numeric (-n) option is specified, the socket address is resolved to its canonical host name (FQDN), and the port number is translated into the corresponding service name.

Foreign Address (0.0.0.0) - address and port number of the remote end of the socket. Analogous to "Local Address."

State - the state of the socket. Since there are no states in raw mode and usually no states used in UDP, this column may be left blank.

##### Show the presence of the sshd process using the ps command. To do this, you need to match the keys to the command.

![SSHD](misc/images/P8_4.png)

ps -aux | grep sshd output ps: `a` this option causes ps to list all processes with a terminal (tty), or to list all processes when used together with the x option. `u` Display user-oriented format. `x` this option causes ps to list all processes owned by you (same EUID as ps), or to list all processes when used together with the a option.

##### Reboot the system.


## Part 9. Installing and using the **top**, **htop** utilities

##### Install and run the top utility.

The top program provides a dynamic real-time view of a running system.

![Top](misc/images/P9_1.png)

![Top](misc/images/P9_2.png) - uptime

![Top](misc/images/P9_3.png) - number of authorised users

![Top](misc/images/P9_4.png) - total system load

![Top](misc/images/P9_5.png) - total number of processes

![Top](misc/images/P9_6.png) - cpu load

![Top](misc/images/P9_7.png) - memory load

pid of the process with the highest memory usage By selecting the %MEM column by keys `<` `>` and pressing `Shift` we get sorted process.

![Top](misc/images/P9_8.png)

![Top](misc/images/P9_9.png)

##### Install and run the htop utility.

The htop - interactive process viewer.

sorted by PID.

![HTop](misc/images/P9_10.png)

sorted by PERCENT_CPU.

![HTop](misc/images/P9_11.png)

sorted by PERCENT_MEM.

![HTop](misc/images/P9_12.png)

sorted by TIME.

![HTop](misc/images/P9_13.png)

## Part 10. Using the **fdisk** utility

`fdisk -l`

`swapon --show`

![fdisk](misc/images/P10_1.png)

Obtained information about the disk and swap file.


## Part 11. Using the **df** utility

##### Run the df command.

![df](misc/images/P11_1.png)

1-K blocks = 1024 bytes

Size: 31658,25 Мб

Used: 4602,96 Мб

Available: 25728,64 Мб

Use: 16%

##### Run the df -Th command.

![df](misc/images/P11_2.png)

Size: 30Gb

Used: 4.3Gb

Avail: 24Gb

Use%: 16%

Type filisystem: ext4


## Part 12. Using the **du** utility

Run the du command.

`du`

![du](misc/images/P12_1.png)

Output the size of the /home, /var, /var/log folders (in bytes, in human readable format).

`du -shb /home /var/log /var`  - in bytes

`du -sh /home /var/log /var`

![du](misc/images/P12_2.png)

Output the size of all contents in /var/log (not the total, but each nested element using *)

`du -sh /var/log/*`

![du](misc/images/P12_3.png)


## Part 13. Installing and using the **ncdu** utility

Install the ncdu utility.

`sudo apt install ncdu`

`ncdu`

![ncdu](misc/images/P13_1.png)

Output the size of the /home, /var, /var/log folders.

![ncdu](misc/images/P13_2.png)

![ncdu](misc/images/P13_3.png)

## Part 14. Working with system logs

Open for viewing:

`vim /var/log/dmesg`

![Logs](misc/images/P14_1.png)

`vim /var/log/syslog`

![Logs](misc/images/P14_2.png)

`cat /var/log/auth.log | grep systemd-logind` - the last successful login time

![Logs](misc/images/P14_3.png)

`sudo systemctl restart ssh.service`

`vim /var/log/syslog`

![Logs](misc/images/P14_4.png)


## Part 15. Using the **CRON** job scheduler

Using the job scheduler, run the uptime command in every 2 minutes.

`crontab -e` and press `Enter`

![CRON](misc/images/P15_1.png)

`vim /var/log/syslog`

![CRON](misc/images/P15_2.png)
