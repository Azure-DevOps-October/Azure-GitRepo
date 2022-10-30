USER MANAGEMENT:
3 types of users in linux
1.Root user:Root user has all the privilages to execute all the cmds(Administrator) will be only one per machine. Ex.: /root is home directory to rootuser
2.sudo user:user who is having temporary root access is called sudo user
3.Normal user: normal user which we can create.This user will have limited privilages (Only user specific operations)

System users:Every application will have its own user.those users will are created in the OS at time of installation of applications.which are called as system users.
these users are not created by us , created by as part of application deloyment.
These s/m users cannot login to the system.they don't have any username and password.they cann't login to the shell.
the process will be running with that user but it is not allow us login to the s/m.

By default Root User ID will be 0 in any Linux OS
	Linux OS and IDs 1 to 999 are assigned to the s/m users.
	Rest of the users will be assigned from 1000 onwards.

To see s/m users cmd is   getent passwd {1..999}

To user accounts          getent passwd {1000..60000} 

To create users:
sudo adduser username  (it prompts details,by default it creats directory)
sudo useradd username  (It doesn't prompts for any details, it just creates the user,manually we shuold create dir)
sudo useradd -d /home/dir username (create a user and attach a dir)
cat /etc/passwd (stores the user info. w.r.to username:Encrypted password:userid:group id:homedir:loginshell/nologin (no need of login just collects the info from inside of s/m ) )

sudo deluser --remove-home username (delete user)

To change password 
syntax:  passwd username

switch users   : sudo su
su -username
to comeout of user  :exit
switch to root user : sudo su -

creating a group
groupadd groupname

adding users to group
sudo usermod -a -G existinggroup existinguser

Adding normal user to sudo group
sudo usermod -aG sudo existinguser
          or
vi /etc/sudoers.d/username
username ALL=(ALL) ALL 			                         : asks passwd for every cmd
username ALL=(ALL) NOPASSWD:ALL                      : setting no passwd for all the cmds
username ALL=(ALL) NOPASSWD:/bin/mkdir,/bin/rmdir    : to set nopasswd and allowing sudo permissions for limited cmds , what are cmds we want to allow those we should mension here.

ALL=(ALL:ALL)
any host=(any user : any group)

File Permissions:
there are 2 ways to manage permissions, one is by text the other is by an octal value

change Mode

  Options  : (U)ser (g)roup (O)thers

-(file/dir/shortcut(link))---(user)---(group)---(Others)
read -4, write-2 , execute -1

change file permissions
chmod u+x file/scriptname/dir
chmod g+rw filename
chmod og+re filename

chmod 000 filename
chmod 764 filename



